---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-29T14:41:00
Owner:
  - Eduardo Quinalha
---
# O que é?

- framework de desenvolvimento multiplataforma usado principalmente para criar aplicativos com interfaces gráficas (GUI)
- Também pode ser utilizado para outros tipos de software, como ferramentas de linha de comando, servidores e aplicativos móveis
- capaz de compilar para vários sistemas operacionais como **Windows, macOS, Linux, Android e iOS**

> [!note] 🔥
> **A CEBRASPE considera que Qt é Opensource**

# Características

- Um único código-fonte que pode ser compilado e executado em várias plataformas sem (ou com mínimas) alterações no código
- Isso inclui tanto desktops quanto dispositivos móveis
- Ampla biblioteca de interface gráfica
- Suporta componentes de interface modernos e responsivos
- Usando o **Qt Widgets** e o **Qt Quick (QML)**, é possível criar interfaces tanto tradicionais quanto dinâmicas e interativas
- Escrito em C++
- Pode ser usando em QML

### QML

- Linguagem de script para o desenvolvimento de interfaces gráficas usando Qt
- semelhante ao JavaScript
- é usada para descrever a interface do usuário e sua lógica
- frequentemente combinada com **Qt Quick** para criar interfaces gráficas mais modernas, interativas e animadas
- **Qt Quick** é voltado para o desenvolvimento rápido de interfaces gráficas orientadas a gestos e animações, sendo uma escolha comum em aplicativos móveis e **embarcados**

### Frameworks

- Qt Creator
	- oferece ferramentas como depurador, editor de código, designer visual de interfaces e muito mais.
- Qt Designer
	- permite criar interfaces gráficas visualmente, facilitando o design de GUIs
- `qmake`
	- ferramenta de build que facilita o processo de compilação dos aplicativos escritos com Qt

### Build

- Compilar e configurar o Qt para sistemas embarcados pode ser um processo complexo, especialmente se você precisar cross-compilar para uma arquitetura diferente.
- Ferramentas como o **Yocto Project** podem auxiliar na criação de imagens de sistema personalizado com o Qt integrado.

# Estrutura básica

```c++
#include <QApplication>
#include <QPushButton>

int main(int argc, char *argv[]) {
    QApplication app(argc, argv);  // Inicializa o aplicativo Qt

    QPushButton button("Clique aqui");  // Cria um botão com o texto "Clique aqui"
    button.resize(200, 100);  // Define o tamanho do botão
    button.show();  // Exibe o botão

    return app.exec();  // Executa o loop de eventos
}
```

# Componentes

## Qt Widgets

- coleção de classes para criar interfaces gráficas tradicionais, como janelas, menus, caixas de diálogo, botões, etc.
- Esse modelo é muito utilizado em aplicativos desktop.

## Qt Quick e QML

- tecnologia usada para criar interfaces gráficas fluidas e modernas com QML.
- Usada principalmente para desenvolvimento móvel, embarcado e onde interfaces dinâmicas são necessárias.
- Disponibiliza tipos para receber os inputs dos usuários, construir componentes visuais, criar modelos de dados e instanciação atrasada de objetos

## **Qt Network**

- Fornece classes para manipulação de redes, como sockets TCP/UDP, HTTP, FTP e WebSockets. 
- Permite desenvolver aplicativos conectados com funcionalidades de rede robustas.

## **Qt Multimedia**

- Suporte para manipulação de multimídia, incluindo reprodução de áudio e vídeo, captura de câmera e microfone, e gerenciamento de codecs.

## **Qt Charts, Qt 3D, e Qt Data Visualization**

- Bibliotecas adicionais para criação de gráficos, visualizações 3D, e gráficos interativos, usadas principalmente em visualização de dados e aplicativos científicos.

## **Qt SQL**

- Classes para trabalhar com bancos de dados relacionais como SQLite, MySQL, PostgreSQL, entre outros. 
- Permite criar e manipular conexões com banco de dados de maneira simples.

## Qt Core

- fornece as funcionalidades básicas e essenciais necessárias para o desenvolvimento de aplicativos em **C++** com Qt
- contém classes e funções para lidar com tarefas comuns que são** independentes de interfaces gráficas**, como manipulação de arquivos, gerenciamento de threads, temporizadores, data e hora, manipulação de strings, containers, sinais e slots (mecanismo de comunicação entre objetos), entre outros.

### Sistema de Sinais e Slots

- Um dos conceitos mais importantes do Qt é o mecanismo de **sinais e slots**, que permite a comunicação entre objetos. 
- Um "sinal" é emitido por um objeto quando ocorre um evento específico, e um "slot" é uma função que é chamada em resposta ao sinal.
- Isso facilita a programação orientada a eventos e promove o desacoplamento entre os componentes do software.

## Qt D-Bus

- Módulo do **Qt Framework** que fornece suporte à comunicação via **D-Bus**, um sistema de mensagens interprocessuais (IPC - Inter-Process Communication) amplamente utilizado no ambiente **Linux** e em sistemas baseados em **Unix**
- **D-Bus** é um barramento de mensagens projetado para permitir que processos em execução no mesmo sistema se comuniquem entre si
- também é usado para implementar a comunicação entre aplicativos desktop e serviços de sistema.
- Tipos de barramentos
	- **System Bus**: Um barramento global do sistema para comunicação entre serviços de sistema (ex.: gerenciamento de energia, rede, etc.).
	- **Session Bus**: Um barramento por sessão, geralmente utilizado para comunicação entre processos de usuários, como aplicativos gráficos.
- O **Qt D-Bus** abstrai a complexidade de se comunicar com o **D-Bus** e fornece uma interface orientada a objetos para que as aplicações Qt possam interagir facilmente com serviços D-Bus

# Qt em Sistemas Embarcados

- O Qt fornece várias soluções especificamente adaptadas para o desenvolvimento em sistemas embarcados:

## **Qt for Embedded Linux (antigo Qt for Embedded Linux ou Qt/Embedded)**

- Permite que aplicações Qt sejam executadas diretamente no framebuffer do Linux, sem a necessidade de um servidor X11 ou Wayland.
- Ideal para dispositivos com recursos limitados, já que elimina a sobrecarga de um sistema de janelas completo.
- Suporta aceleração de hardware para gráficos, o que é útil em sistemas com GPUs ou processadores gráficos integrados.

## **Qt for MCUs (Qt para Microcontroladores)**

- Uma versão otimizada do Qt projetada para microcontroladores com recursos muito limitados.
- Permite criar interfaces de usuário ricas e fluidas em dispositivos com pouca memória RAM e capacidade de processamento limitada.
- Usa o **Qt Quick Ultralite**, um subconjunto de Qt Quick (QML) otimizado para microcontroladores.
- Indicado para dispositivos com recursos extremamente limitados (por exemplo, menos de 16MB de RAM)

## **Qt Lite**

- Uma iniciativa para modularizar o Qt e permitir que os desenvolvedores selecionem apenas os componentes necessários para suas aplicações, reduzindo assim o tamanho total do binário.
- Muito útil para criar aplicações minimalistas, incluindo apenas o que é essencial.
