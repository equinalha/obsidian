---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-29T14:41:00
Owner:
  - Eduardo Quinalha
---
# Drivers

- No Windows, o desenvolvimento de drivers segue uma arquitetura rígida e controlada pelas:
	- **Windows Driver Model (WDM)**, 
	- ou pelo mais recente **Windows Driver Frameworks (WDF)**, que inclui:
		- **KMDF** (Kernel-Mode Driver Framework) e 
		- **UMDF** (User-Mode Driver Framework)
- No Windows, os drivers podem operar tanto em `kernel mode` quanto em `user mode`

## Windows Driver Model (WDM)

- Arquitetura antiga de desenvolvimento de drivers
- Introduzida pelo Windows 98 e 2000
- Define um conjunto básico de interfaces e estruturas que os drivers devem implementar para serem compatíveis com o Windows
- **Ainda é suportado**, porém é mais difícil de programar e mais** propenso a erros**
- O desenvolvedor precisa gerenciar manualmente aspectos como sincronização e tratamento de IRP (I/O Request Packets)

## Windows Driver Framework (WDF)

- Abstrai complexidades do WDM
- Oferece API´s mais seguras e de alto nível
- **KMDF (Kernel-Mode Driver Framework): **
	- É utilizado para escrever drivers de modo kernel. 
	- Ele fornece mecanismos como gerenciamento automático de sincronização, suporte a IRPs e filas de I/O, tornando o desenvolvimento mais seguro e menos propenso a falhas críticas.
- **UMDF (User-Mode Driver Framework)**:
	- Projetado para drivers que podem ser executados no modo de usuário, como drivers de impressoras, dispositivos USB ou dispositivos de armazenamento simples. 
	- Ele garante maior segurança, já que as falhas no modo de usuário não afetam a estabilidade do sistema

## Principais Componentes

- **IRP (I/O Request Packet)**
	- Representam solicitações de entrada e saída
	- Enviado pelo subsistema de I/O do windows
- **PIL (Plug and Play, Power Management & Interrupts Layer)**
	- Funcionalidades que precisam ser implementadas nos drivers
- **Filas de I/O**
	- Podem ser definidas nos drivers para gerenciamento das solicitações
- **DDI (Device Driver Interface)**
	- Interfaces usadas pelos drivers para interagir com o kernel e outros subsistemas

## Ferramentas necessárias

- **Visual Studio**
- **Windows Driver Kit (WDK)**
	- Conjunto de bibliotecas e documentação
- **Driver Verifier**
	- Ferramenta integrada ao windows
	- Ajuda a detectar problemas de estabilidade
	- Disponível em: `%WinDir%\system32\Verifier.exe`
- **WinDbg**
	- Depurador de kernel

## Desenvolvimento do Driver

### Funções de Callback

- `EvtDeviceAdd`
- `EvtIoRead`
- `EvtIoWrite`
- `EvtDriverUnload`

### Manuseio de IRPs

- No nível do WDM, o driver deve manipular diretamente os IRPs. 
- No WDF, o framework gerencia os IRPs automaticamente, e o desenvolvedor pode focar nas operações de I/O específicas do dispositivo.

### Gerenciamento de Interrupções

- Drivers de dispositivos de hardware geralmente precisam lidar com interrupções geradas pelo dispositivo, o que requer código específico para gerenciamento de interrupções no kernel.

### **Suporte a PnP e Power Management**

- O driver precisa implementar callbacks para gerenciar eventos como remoção de dispositivos e mudança de estados de energia (suspensão, hibernação).

### Assinatura

- O windows não permite o carregamento de drivers sem assinatura no **modo kernel**
- Exceto se estiver rodando em modo de teste
- O driver precisa ser assinado usando um certificado digital, que pode ser emitido por uma autoridade certificadora (CA), como a Microsoft ou outras CAs confiáveis.

## Tipos de Drivers

- **Device Driver**
- **Filter Driver**
	- Modifica operações de I/O de outros drivers
	- Pode ser utilizado para implementar funções de criptografia, monitoramento ou logs
- **Miniport Driver**
	- Suporte a dispositivos específicos como rede ou adaptadores gráficos

# Serviços

- programas que rodam em segundo plano, sem uma interface gráfica direta com o usuário
- são gerenciados pelo sistema operacional através do **Gerenciador de Controle de Serviços (Service Control Manager - SCM)**

## Desenvolvimento

### C/C++

- Em **C/C++**, o desenvolvimento de um serviço Windows requer o uso de chamadas como `RegisterServiceCtrlHandler` para manipular o ciclo de vida do serviço.

```c++
#include <windows.h>

SERVICE_STATUS        g_ServiceStatus = {0};
SERVICE_STATUS_HANDLE g_StatusHandle = NULL;
HANDLE                g_ServiceStopEvent = INVALID_HANDLE_VALUE;

void WINAPI ServiceMain(DWORD argc, LPTSTR *argv);
void WINAPI ServiceCtrlHandler(DWORD);
DWORD WINAPI ServiceWorkerThread(LPVOID lpParam);

int main(int argc, char *argv[]) {
    SERVICE_TABLE_ENTRY ServiceTable[] = {
        {"MyService", (LPSERVICE_MAIN_FUNCTION)ServiceMain},
        {NULL, NULL}
    };

    StartServiceCtrlDispatcher(ServiceTable);
    return 0;
}

void WINAPI ServiceMain(DWORD argc, LPTSTR *argv[]) {
    g_StatusHandle = RegisterServiceCtrlHandler("MyService", ServiceCtrlHandler);

    g_ServiceStatus.dwServiceType = SERVICE_WIN32_OWN_PROCESS;
    g_ServiceStatus.dwControlsAccepted = 0;
    g_ServiceStatus.dwCurrentState = SERVICE_START_PENDING;
    SetServiceStatus(g_StatusHandle, &g_ServiceStatus);

    g_ServiceStopEvent = CreateEvent(NULL, TRUE, FALSE, NULL);

    g_ServiceStatus.dwControlsAccepted = SERVICE_ACCEPT_STOP;
    g_ServiceStatus.dwCurrentState = SERVICE_RUNNING;
    SetServiceStatus(g_StatusHandle, &g_ServiceStatus);

    WaitForSingleObject(g_ServiceStopEvent, INFINITE);

    g_ServiceStatus.dwCurrentState = SERVICE_STOPPED;
    SetServiceStatus(g_StatusHandle, &g_ServiceStatus);
}

void WINAPI ServiceCtrlHandler(DWORD CtrlCode) {
    switch (CtrlCode) {
        case SERVICE_CONTROL_STOP:
            g_ServiceStatus.dwCurrentState = SERVICE_STOP_PENDING;
            SetServiceStatus(g_StatusHandle, &g_ServiceStatus);

            SetEvent(g_ServiceStopEvent);
            break;
        default:
            break;
    }
}
```

- As principais funções que devem ser implementadas são:
	- `**ServiceMain**`: Função que é chamada quando o serviço inicia.
	- `**ServiceCtrlHandler**`: Manipulador para eventos como start, stop, pause.
	- `**ServiceWorkerThread**`: Representa o processo em execução enquanto o serviço está ativo.
- No C/C++, é necessário criar um instalador ou utilizar o `sc.exe` para instalar o serviço: `sc create MyService binPath= "C:\path\to\service.exe”`

### C# (.NET Framework)

- Desenvolver um serviço em **C#** usando o .NET Framework é bem mais simples, pois ele abstrai grande parte das complexidades. 
- O namespace `System.ServiceProcess` contém as classes necessárias para criar, iniciar e parar serviços.

```c#
using System;
using System.ServiceProcess;

public class MyService : ServiceBase
{
    public MyService()
    {
        this.ServiceName = "MyService";
    }

    protected override void OnStart(string[] args)
    {
        // Código para iniciar o serviço
        System.IO.File.AppendAllText(@"C:\ServiceLog.txt", "Serviço iniciado em: " + DateTime.Now + "\n");
    }

    protected override void OnStop()
    {
        // Código para parar o serviço
        System.IO.File.AppendAllText(@"C:\ServiceLog.txt", "Serviço parado em: " + DateTime.Now + "\n");
    }

    public static void Main()
    {
        ServiceBase.Run(new MyService());
    }
}
```

- Depois de criar o serviço, ele precisa ser registrado no sistema, o que é feito com o `**InstallUtil.exe**`** **ou através de um instalador personalizado:` InstallUtil.exe C:\path\to\MyService.exe`

## Gerenciamento de Serviços

- `services.msc`
	- Interface gráfica do windows

## Ciclo de vida de serviços

- **SERVICE_START_PENDING**: Quando o serviço está em processo de inicialização.
- **SERVICE_RUNNING**: Quando o serviço está em execução e operando normalmente.
- **SERVICE_STOP_PENDING**: Quando o serviço está sendo parado.
- **SERVICE_STOPPED**: Quando o serviço foi finalizado.

# Aplicativos

## UWP

- Universal Windows Platform
- plataforma de desenvolvimento da Microsoft que permite criar aplicativos que podem ser executados em uma ampla variedade de dispositivos que utilizam o sistema operacional Windows, como PCs, tablets, smartphones, consoles Xbox, dispositivos IoT e até o HoloLens (dispositivo de realidade aumentada da Microsoft)
- Permite o desenvolvimento universal
	- O mesmo código executa em dispositivos diversos
- Os aplicativos UWP são executados em um ambiente mais seguro, com sandboxing, o que limita o acesso direto a certos recursos do sistema, aumentando a segurança do aplicativo.

### Estrutura de um Aplicativo UWP

1. **XAML para a Interface de Usuário**:
	- O UWP usa **XAML (Extensible Application Markup Language)** para descrever a interface de usuário. 
	- O XAML permite criar interfaces declarativas e interativas que são fáceis de manter e escalar. 
	- Através de XAML, é possível definir layouts, controles, animações e muito mais.
2. **C# ou C++ para a Lógica de Aplicação**:
	- O **C#** é a linguagem de programação mais usada para a lógica dos aplicativos UWP. 
	- No entanto, também é possível usar **C++** (com ou sem o suporte para DirectX para gráficos de alto desempenho) e **JavaScript** (para aplicativos UWP baseados na web).
3. **Ciclo de Vida do Aplicativo**:
	- A UWP fornece um modelo de ciclo de vida que ajuda a gerenciar o estado do aplicativo em diferentes situações, como quando ele é minimizado, suspenso, ou retomado. 
	- Isso é importante para garantir que o aplicativo seja eficiente em termos de consumo de energia e de recursos.