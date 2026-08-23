---

---
# BOM

- ESP32-C3-WROOM-02
- AMS1117-3.3
- Ferro de solda 40W ponta fina (fenda)
- Fluxo de solda lĩquido
- Pasta para soldar
- Malha (fita) de-soldadora

# Circuito

<!-- Column 1 -->
![[19d2af66-92e9-4fcb-8853-59097513d977.png]]


<!-- Column 2 -->
![[SubPages/Pessoal/images/image 24.png]]


![[SubPages/Pessoal/images/image 25.png]]

[https://www.perplexity.ai/search/desenvolvi-um-dispositivo-iot-bYDY1Pd.RzSLb.zLEbLE0A](https://www.perplexity.ai/search/desenvolvi-um-dispositivo-iot-bYDY1Pd.RzSLb.zLEbLE0A)

# Alimentando com baterias

**Let‘s compare some battery options in more detail:**

| **Battery Option** | **Voltage** | **Capacity Range** | **Pros** | **Cons** |
| --- | --- | --- | --- | --- |
| LiPo Pouch Cell | 3.7V (typ.) | 100 mAh – 5,000 mAh | Lightweight, versatile form factors | Needs protection circuit |
| 18650 Li-ion Cell | 3.7V (typ.) | 1,000 – 3,500 mAh | High capacity, ideal voltage | Can be expensive |
| 2x NiMH AA Batteries | 2.4V | 1,000 – 3,000 mAh | Inexpensive, rechargeable | Voltage drop during discharge |
| 2x Alkaline AA Batteries | 3.0V | 1,500 – 3,000 mAh | Easy to source, long shelf life | Not rechargeable, lower capacity |

1. **Circuito divisor de tensão:**
	- Conecte uma extremidade do NTC 10k aos **3,3 V** do ESP32.
	- Conecte a outra extremidade do NTC ao **pino analógico (exemplo: GPIO 34)**.
	- Conecte um resistor fixo de **10kΩ** entre o pino analógico e o **GND**.
	O pino analógico lerá a tensão da junção entre o NTC e o resistor fixo.
2. **Leitura pelo ADC:**
	- O ESP32 possui ADC de 12 bits, com escala de 0 a 4095.
	- Faça a leitura analógica com `**analogRead(pino);**`
3. **Cálculo da resistência do NTC:**

![[SubPages/Pessoal/images/image 26.png]]

4. **Conversão da resistência para temperatura (em Kelvin):**

Usa-se a equação Beta:

![[SubPages/Pessoal/images/image 27.png]]

onde:

- T0=298.15 K*T*0=298.15*K* (temperatura referência 25 °C)
- β*β* é constante do termistor (geralmente ~3950)
- R0=10000 Ω*R*0=10000Ω (resistência do NTC a 25 °C)

Temperatura em Celsius:

![[SubPages/Pessoal/images/image 28.png]]

---

# Variação térmica

A variação de leitura causada pela temperatura é um **comportamento normal** em células de carga, resultado de efeitos térmicos tanto na ponte de Wheatstone (strain gauges) quanto nos materiais metálicos do sensor. Entretanto, há **formas eficazes de compensar** e reduzir significativamente essa deriva.

---

## Por que ocorre a variação térmica

A célula de carga é composta por extensômetros colados sobre um corpo metálico (geralmente alumínio ou aço inoxidável) que se deforma com o peso aplicado.

Quando a temperatura muda:

- O **módulo de elasticidade** do metal varia, alterando a sensibilidade da medição.
- Os **strain gauges** mudam ligeiramente de resistência com a temperatura.
- O **HX711**, embora estável, também pode apresentar pequeno offset térmico.

Esses fatores juntos causam:

- **desvio do zero** (offset mesmo sem carga);
- **variação de sensibilidade** (mesma carga gera diferentes leituras).

---

## Métodos de compensação térmica

5. **Calibração térmica experimental**
	- Meça o valor fornecido pela célula de carga sob **várias temperaturas** conhecidas **com a mesma carga fixa**.
	- Determine o coeficiente de variação (em g/°C) e corrija o valor medido aplicando uma compensação linear no código:
		`peso_corrigido = peso_lido + coef_temp * (temperatura - temperatura_ref)`
	- O coeficiente pode ser obtido empiricamente, medindo em pelo menos 3 pontos (ex.: 10 °C, 25 °C, 40 °C).
6. **Uso de sensor de temperatura externo**
	- Adicione um **sensor como o DS18B20 ou TMP36** próximo à célula de carga.
	- Monitore a temperatura a cada leitura e aplique correção com base em tabela de calibração.
7. **Compensação via hardware**
	- Algumas células de carga industriais incorporam **termistores NTC** na própria ponte, equilibrando automaticamente a tensão de excitação conforme a temperatura.
	- Essa técnica reduz a variação de zero (~10× menor em sensores compensados).
8. **Recalibração periódica automática**
	- Zeragem automática (tare) em momentos definidos do dia, em condição sem carga, reestabelecendo o offset térmico acumulado.

---

## Boas práticas complementares

- **Evite aquecimento direto** (sol, motores próximos ou dissipadores).
- **Isole termicamente** a célula para reduzir gradientes de temperatura.
- **Promova estabilidade ambiental**: variações bruscas afetam leituras mais do que variações lentas e homogêneas.

---

## Considerações de projeto

- O **intervalo de compensação térmica típico** das células de carga é **10 °C a +40 °C**; fora disso, os erros aumentam significativamente.
- Materiais diferentes influenciam a estabilidade: **aço inoxidável** é o mais estável, **alumínio** é mais sensível.

---

Em resumo, a variação que você observa é esperada, mas pode ser **praticamente eliminada** combinando uma **calibração térmica com sensor de temperatura** e uma **estratégia de compensação via software** — uma solução de baixo custo e ideal para dispositivos IoT com o HX711.

---

# Exemplo simplificado de código Arduino/ESP32:

```c
const int pinoNTC = 34; // pino ADC
const float Vref = 3.3; // tensão de referência do ESP32 ADC
const float Rfixed = 10000.0; // resistor fixo 10k
const float beta = 3950.0; // Beta do NTC
const float T0 = 298.15; // 25 °C em Kelvin
const float R0 = 10000.0; // resistência a 25 °C

void setup() {
  Serial.begin(115200);
}

void loop() {
  int adcValue = analogRead(pinoNTC);
  float Vout = (adcValue * Vref) / 4095.0;
  float Rntc = Rfixed * (Vout / (Vref - Vout));
  float tempK = 1.0 / (1.0 / T0 + (1.0 / beta) * log(Rntc / R0));
  float tempC = tempK - 273.15;

  Serial.print("Temperatura: ");
  Serial.print(tempC);
  Serial.println(" °C");

  delay(2000);
}
```

## Solução de menor custo: compensação via software

9. **Adicione um sensor de temperatura barato (ex.: DS18B20 ou NTC 10 kΩ)**
	- Custo: cerca de R$ 5–10 a unidade.
	- Instale o sensor **próximo à célula de carga** para registrar a temperatura real do sensor metálico, não do ar.
10. **Realize calibrações simples em diferentes temperaturas**
	- Medir o valor lido pelo HX711 para uma **carga fixa** em 2 ou 3 temperaturas (ex.: 15 °C, 25 °C, 35 °C).
	- Calcular um **coeficiente de correção linear**:
		`peso_corrigido = peso_lido + (coef_temp * (temperatura - temp_ref))`
	- Este método reduz significativamente o erro térmico sem precisar de novo hardware ou célula de carga especial.
11. **Implementar correção dinâmica no código**
	- O firmware pode ler a temperatura a cada medição e aplicar automaticamente a compensação.
	- É possível usar uma média móvel para evitar ruído térmico.

---

# Custom PCB

<!-- Column 1 -->
[https://docs-espressif-com.translate.goog/projects/esp-hardware-design-guidelines/en/latest/esp32/pcb-layout-design.html?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc](https://docs-espressif-com.translate.goog/projects/esp-hardware-design-guidelines/en/latest/esp32/pcb-layout-design.html?_x_tr_sl=en&_x_tr_tl=pt&_x_tr_hl=pt&_x_tr_pto=tc)

[https://youtu.be/p3d5Iinbj2Y](https://youtu.be/p3d5Iinbj2Y)

<!-- Column 2 -->
[https://docs.espressif.com/projects/esp-hardware-design-guidelines/en/latest/esp32/esp-hardware-design-guidelines-en-master-esp32.pdf](https://docs.espressif.com/projects/esp-hardware-design-guidelines/en/latest/esp32/esp-hardware-design-guidelines-en-master-esp32.pdf)

[https://forum.arduino.cc/t/minimum-required-for-esp32/1100515/2](https://forum.arduino.cc/t/minimum-required-for-esp32/1100515/2)

Ao utilizar **somente o chip ESP32** (ou o módulo nu, como o ESP32-D0WD ou ESP32-WROOM sem placa de desenvolvimento), sua PCB precisará incluir diversos **componentes essenciais de suporte elétrico e de programação**, que já vêm embutidos nas placas como a **ESP32-C3 Mini** ou **DevKit**.

---

## 1. Alimentação elétrica

O ESP32 opera em **3,3 V**, então é necessário:

- **Regulador de tensão** (como o AMS1117-3.3 ou RT9080) se você usar fontes de 5 V.
- **Capacitores de desacoplamento** próximos aos pinos VCC e GND:
	- 10 µF (cerâmico ou eletrolítico)
	- 0,1 µF (cerâmico)
- **Plano de terra sólido** na PCB, conforme diretrizes da Espressif.

---

## 2. Circuito de boot e reset

Para garantir o modo correto de inicialização e gravação do firmware:

- **Botão de RESET (EN):** ligado ao pino EN (ativa reset ao levar ao GND).
- **Botão de BOOT:** ligado ao pino GPIO0 (mantido em LOW durante bootloader).
- **Resistores pull-up/pull-down:**
	- 10 kΩ entre EN e 3.3 V (pull-up).
	- 10 kΩ entre GPIO0 e 3.3 V (pull-up).
- **Capacitor de auto-reset (100 nF)** entre EN e DTR (facilita autoprogramação via UART).

---

## 3. Interfacing USB e programação

Como o chip não tem USB nativo, será necessário incluir um **conversor USB–UART**, como:

- **CP2102**, **CH340**, ou **FT232R**.
	Conexões típicas:
- RX ↔ TX
- TX ↔ RX
- GPIO0 ↔ GND (modo flash)
- EN ↔ DTR (reset automático)

---

## 4. Antena e RF

- Caso use o **módulo ESP32-WROOM**, a antena já está integrada e calibrada.
- Se usar o **chip nu ESP32-D0WD**, será necessário desenhar ou soldar uma trilha de **antena de 50 Ω** ou conector U.FL, seguindo layout orientado pela Espressif.

---

## 5. Cristal e osciladores

- O chip ESP32 requer um **cristal de 40 MHz** com capacitores de carga (~12 pF).
- Também pode-se adicionar um cristal opcional de 32 kHz para RTC mais preciso.

---

## 6. Outros componentes auxiliares

- LED de status (com resistor de 330 Ω ligado a um GPIO).
- Header de 6 pinos para **UART de programação** (GND, TX, RX, 3V3, EN, GPIO0).
- Filtros EMI opcionais (ferrite bead no VCC principal, 120 Ω @ 100 MHz).

---

## 7. Diretrizes de layout

A documentação oficial da Espressif recomenda:

- Camada de plano GND contínua sob o chip e plano de RF isolado.
- Trilhas curtas no cristal e nos capacitores de desacoplamento.
- Zona livre de cobre sob a antena (mínimo 15 mm de afastamento).

---

## Em resumo

| **Subcircuito** | **Componentes principais** | **Função** |
| --- | --- | --- |
| Alimentação | Regulador 3.3 V, capacitores | Fornece energia estável |
| Boot/reset | 2 botões + resistores | Carregamento e reinício |
| USB–UART | CP2102/CH340 + 2 resistores | Programação e debug |
| Clock | Cristal 40 MHz + 2 capacitores | Oscilador principal |
| RF/Antena | Trilha 50 Ω ou U.FL | Comunicação Wi-Fi |
| GPIO acessórios | LED + resistores | Feedback visual |

---

Em síntese, projetar sua PCB com o **chip ESP32 puro** requer replicar as funções da placa de desenvolvimento: **regulagem de tensão, boot/reset, conversão USB–UART, oscilador e layout RF adequado**.

A Espressif fornece o guia oficial **ESP32 Hardware Design Guidelines**, que detalha todos esses circuitos e layouts de referência.

# PCB para produto final

<!-- Column 1 -->
[https://docs.espressif.com/projects/esp-hardware-design-guidelines/en/latest/esp32/schematic-checklist.html](https://docs.espressif.com/projects/esp-hardware-design-guidelines/en/latest/esp32/schematic-checklist.html)

[https://docs.espressif.com/projects/esp-hardware-design-guidelines/en/latest/esp32/esp-hardware-design-guidelines-en-master-esp32.pdf](https://docs.espressif.com/projects/esp-hardware-design-guidelines/en/latest/esp32/esp-hardware-design-guidelines-en-master-esp32.pdf)

<!-- Column 2 -->
[https://public.robotical.io/Datasheets/ESP32%20Hardware%20Design%20Guidelines.pdf](https://public.robotical.io/Datasheets/ESP32%20Hardware%20Design%20Guidelines.pdf)

Se a placa do produto final não terá interface USB para o usuário, e você pretende programar o ESP32 apenas uma vez antes da venda, a PCB pode ser simplificada nos seguintes aspectos:

---

## O que pode ser removido da PCB

- **Módulo/conversor USB–UART (CP2102, CH340, etc.)** pode ser eliminado.
- **Conector USB** para conexão direta do usuário não será necessário.
- Botões de boot (GPIO0) e reset podem ser mantidos apenas para uso durante a produção, podendo ser omitidos ou ligados a pads para teste/fabricação.

---

## Como programar o ESP32 durante a fabricação

- Insira na PCB um **header de programação UART simples** (ex.: 4 ou 6 pinos) com os sinais necessários:
	- TX do MCU ao RX do programador
	- RX do MCU ao TX do programador
	- GND comum
	- EN e GPIO0 (para colocar ESP32 em modo bootloader) opcionalmente ligados a botões ou pads de teste
- Use um **programador externo USB–UART** (como um módulo USB to Serial) durante a produção para gravar o firmware.
- Depois de programada, a conexão UART pode ser removida, ou deixada como pads test points invisíveis na produção, sem conector para o usuário.

---

## Componentes mínimos em PCB final sem USB

| **Componente** | **Função** | **Observação** |
| --- | --- | --- |
| Regulador 3,3 V + capacitores | Alimentação estável | Essencial para operação |
| Cristal 40 MHz + capacitores | Oscilador principal do chip | Essencial |
| Botão reset (EN) ou pad reset | Permite reinicialização | Pode ser pad para produção |
| Pads UART para programar | Programação durante fabricação | Pode ser série de pontos de teste simples |
| Resistores pull-up/pull-down para boot/reset | Configuração boot correta | Essencial para boot seguro |
| Antena ou circuito RF | Comunicação Wi-Fi | Essencial |
| Condensadores desacoplamento | Estabilidade elétrica | Essencial |

---

## Simplificações possíveis

- Botões físicos podem ser substituídos por **pads para conexão temporária** via clip/teste na produção.
- USB e conectores podem ser omitidos, reduzindo custo, espaço e risco de ações indevidas pelo usuário.
- O circuito fica mais robusto e seguro, pois o firmware não pode ser modificado facilmente pelo usuário final.

---

## Resumo

Você programa o ESP32 via interface UART **externa** durante a montagem/fabricação, usando pads dedicados na PCB que não são acessíveis ao usuário. Não inclui circuito USB nem conectores na placa final. Botões de boot e reset podem ser simplificados para pads de teste.

Isso reduz custo e simplifica o design, mantendo todas as funcionalidades do dispositivo no uso final.

Se desejar, posso ajudar com o esquema básico e layout para essa configuração.

# Projeto do PCB

Para projetar sua PCB com o chip ESP32 sem interface USB para o usuário final, alguns passos e boas práticas são essenciais para garantir funcionalidade, confiabilidade e facilidade na fabricação e programação. Aqui está um guia prático para você começar:

---

## 1. Obtenha documentação oficial

Baixe e estude os documentos da Espressif sobre **hardware design do ESP32**, preferencialmente os guias:

- ESP32 Hardware Design Guidelines
- Datasheet do ESP32 (módulo escolhido ou chip puro)
	Estes mostram esquemas recomendados, restrições de layout e requisitos elétricos.

---

## 2. Software de projeto PCB

Escolha um software de CAD eletrônico, entre os populares e gratuitos estão:

- **KiCad (recomendado e gratuito)**
- Eagle (Autodesk)
- Altium Designer (profissional)
- EasyEDA (online, gratuito)

---

## 3. Elementos essenciais no esquemático

- **Chip ESP32** com os pinos principais conectados (VCC, GND, EN, GPIO0, cristal).
- **Regulador de 3,3 V** e capacitores de desacoplamento próximos ao chip.
- **Cristal de 40 MHz** com capacitores associados.
- Resistores de pull-up em EN (10k) e GPIO0 (10k).
- Circuito de reset: botão ou pad ligado ao EN.
- Pads para programação UART (TX, RX, GND, EN, GPIO0), preferencialmente em header 6 pinos, posicionados em local acessível na placa.
- Saídas e entradas conforme seu circuito (HX711, sensores, etc.).

---

## 4. Layout PCB

- Use uma **camada de plano de terra contínua** para reduzir ruído.
- Mantenha as trilhas dos sinais de clock e RF (antena) o mais curto possível.
- Separe a área de RF (antena) e siga as recomendações para evitar interferências.
- Coloque capacitores de desacoplamento próximos aos pinos de alimentação e terra.
- Deixe espaço para componentes passivos mínimos e busque compactar o design para custo baixo.

---

## 5. Programação e teste após fabricação

- Inclua pads para os sinais UART necessários para flash do firmware.
- Use um clip ou conector temporário para conectar o programador USB-UART durante a manufatura.
- Configure scripts de programação automatizados para facilitar o processo massivo.

---

## 6. Validação

- Faça protótipos da PCB para testes funcionais completos, atenção especial ao circuito de reset, boot e alimentação.
- Teste a estabilidade da comunicação Wi-Fi, consumo energético e integração com o HX711.

---

## 7. Recursos e exemplos

- Pesquise por projetos de referência no GitHub, fóruns e plataformas de maker para PCs similares.
- Espressif mantém exemplos e ferramentas no seu site oficial.

# Projeto de PCB utilizando o KiCad

Para montar o **esquemático inicial da sua PCB com ESP32** no **KiCad**, é recomendável basear-se no circuito mínimo oficial da **Espressif** e nos exemplos abertos disponíveis em projetos públicos. A Espressif publica o **ESP32 Hardware Design Guidelines** que serve como base para isso.

A seguir está um guia passo a passo com estrutura real de projeto.

---

## 1. Configurar o ambiente do KiCad

- Baixe e instale o **KiCad 7 ou 8**.
- Adicione as **bibliotecas oficiais da Espressif** disponíveis no GitHub (símbolos, footprints e 3D models).
- Crie um novo projeto, defina a alimentação em 3,3 V e adicione planos de GND no layout.

---

## 2. Blocos principais do esquemático

12. **ESP32 módulo ou chip**
	- Você pode usar um **módulo ESP32-WROOM-32D** (mais simples) ou o chip nu (ESP32-D0WD).
	- Ligue os pinos de alimentação:
		- VIN (ou VDD3P3) → 3,3 V
		- GND → plano de terra
	- Adicione capacitores de desacoplamento (10 µF e 0,1 µF) próximos ao pino VCC.
13. **Regulador de tensão**
	- Entrada: fonte de 5 V (ou 4,5–6 V de pilhas).
	- Saída: 3,3 V.
	- Exemplo: AMS1117-3.3 com dois capacitores (10 µF entrada e saída).
14. **Circuito de boot e reset**
	- GPIO0: resistor pull-up 10 kΩ.
	- EN: resistor pull-up 10 kΩ + botão momentâneo para GND (reset).
	- GPIO0 conectado a pad de programação (pode ser usado em produção).
15. **Cristal**
	- Cristal de 40 MHz com dois capacitores de 12 pF ligados ao GND.
	- Para uso com RTC opcional, adicione colocação prevista para 32,768 kHz.
16. **Pads de programação UART**
	- Pinos: TX, RX, EN, GPIO0, GND.
	- Organize em uma linha com espaçamento padrão 2,54 mm para conexão temporária durante a fabricação.
17. **Antena**
	- Se usar o módulo com antena integrada, apenas mantenha uma **zona livre de cobre (keepout)** de 15 mm em volta da antena.
	- Se usar chip + antena discreta, siga o layout RF de 50 Ω conforme orientações da Espressif.

---

## 3. Passos para o layout

18. Coloque o ESP32 no centro e o regulador próximo à borda (para dissipar calor).
19. Posicione o cristal e capacitores o mais próximo possível dos pinos correspondentes.
20. Crie planos sólidos de **GND** e **3V3** nas camadas da placa.
21. Adicione **test points** para UART, GND e alimentação.
22. Delimite o perímetro do keepout da antena (zona sem cobre e sem componentes).

---

## 4. Exemplo de estrutura do projeto

| **Bloco** | **Componentes** | **Observações** |
| --- | --- | --- |
| Alimentação | AMS1117-3.3, C1=10µF, C2=0.1µF | Fonte estável 3.3 V |
| Microcontrolador | ESP32-WROOM ou ESP32-D0WD | Núcleo do sistema |
| Boot/reset | R1=10 kΩ, R2=10 kΩ, botão EN | Configuração inicial |
| Clock | Cristal 40 MHz, C3=C4=12 pF | Sinal de clock |
| Programação | Header 5 pinos (TX, RX, EN, GPIO0, GND) | Test pads ou conector |
| RF | Keepout 15 mm | Integridade de sinal |

---

## 5. Recursos complementares

- **Repositórios com projetos abertos**
	- Projeto base com esquemático KiCad:
	- Design completo e tutorial prático do KiCad:.
- **Guia de referência da Espressif** com checklist para esquemático e layout:.

---

Em resumo, no KiCad você vai desenhar um **esquemático modular simples**, usando **regulador, circuitos de boot, pads de programação, antena e desacoplamento**.

Depois disso, basta gerar as footprints e montar o layout conforme o guideline oficial — o que garante compatibilidade elétrica e RF com os módulos comerciais da Espressif.

# PCB Caseiro e testes

É perfeitamente possível criar e testar **um protótipo da sua PCB ESP32 + HX711 em casa** antes de mandar fabricar, usando ferramentas simples e materiais acessíveis. O objetivo é validar o circuito elétrico, medir ruído, verificar consumo e confirmar a integração entre o ESP32 e o HX711.

Aqui está um **passo a passo completo** baseado nas práticas recomendadas e técnicas usadas por desenvolvedores IoT independentes.

---

## 1. Valide o circuito no protoboard

Antes de gerar o layout:

- Monte **o circuito mínimo do ESP32** (alimentação, pull-ups, EN, GPIO0 e interface UART temporária).
- Conecte o módulo **HX711** e a **célula de carga** conforme o esquema previsto no seu design.
- Programe o firmware no ESP32 e teste:
	- comunicação serial,
	- leituras do HX711,
	- estabilidade de tensão e aquecimento.

Essa etapa assegura que a pinagem e alimentação estão corretas.

---

## 2. Crie e imprima o layout para protótipo de circuito impresso

No **KiCad**:

23. Finalize seu esquemático e converta para layout.
24. Execute o DRC (Design Rule Check) para evitar erros.
25. Gere o **arquivo em PDF do cobre** (camada Bottom se for simples face).
26. Use **papel glossy ou fotossensível** e **transferência térmica com ferro ou laminadora** para imprimir o cobre na placa virgem.
27. Revele com percloreto de ferro ou água oxigenada + ácido muriático (use EPI e local ventilado).

Após corroer:

- Limpe a placa, fure os pads e aplique solda estanho nas trilhas.

---

## 3. Soldagem e montagem do protótipo

- Use ferro de solda de ponta fina e fio 0,5 mm.
- Comece pelos componentes menores (resistores, capacitores, ESP32, HX711).
- Se o ESP32 tiver encapsulamento SMD, use **pasta de solda + soprador térmico** ou **chapa quente** para retrabalho.
	(Pode reciclar uma **chapa MHP30** ou sanduicheira comum para reflow artesanal, muito usada por makers.)

---

## 4. Programação e testes

- Use um **conversor USB→UART externo** com jumpers ligados aos pads TX, RX, GND, EN e GPIO0.
- Faça a primeira gravação do firmware, depois valide medições do HX711.

Verifique:

- ruído e precisão na leitura da célula de carga;
- estabilidade térmica e consumo;
- operação do ESP32 em modos sleep se aplicável.

---

## 5. Alternativa moderna: PCB barata de teste

Se preferir não fabricar manualmente:

- Envie os **Gerber Files** exportados do KiCad para uma fábrica de baixo custo (JLCPCB, PCBWay, Elecrow).
- Peça **apenas 5 unidades**, acabamento padrão FR4 1,6 mm e solda HASL (geralmente US$ 2–5 + frete).

Assim você valida o layout real e pode soldar manualmente os componentes.

---

## 6. Dicas extras

- Deixe **vias grandes (≥0,6 mm)** e **pads de fácil soldagem** para protótipos caseiros.
- Posicione o HX711 longe da antena do ESP32 para reduzir interferências.
- Se quiser, use **jumpers ou headers temporários** para testar pinos que futuramente serão fixos.

---

**Conclusão:**

O fluxo completo é: testar no **protoboard → imprimir e corroer PCB artesanal** → validar hardware com **programação via USB-UART** → opcionalmente, pedir PCBs baratas para ajuste fino do layout.

Essa abordagem dá controle total sobre cada fase e reduz desperdício antes da produção comercial.

# Fabricação da PCB Final

[https://pcbbrasil.com.br/quote](https://pcbbrasil.com.br/quote)

# Utilizando do conversor ADC HX711

[https://github.com/bogde/HX711#how-to-calibrate-your-load-cell](https://github.com/bogde/HX711#how-to-calibrate-your-load-cell)

[https://github.com/RobTillaart/HX711/blob/master/examples/HX_kitchen_scale/HX_kitchen_scale.ino](https://github.com/RobTillaart/HX711/blob/master/examples/HX_kitchen_scale/HX_kitchen_scale.ino)

[https://github.com/bogde/HX711/blob/master/src/HX711.h](https://github.com/bogde/HX711/blob/master/src/HX711.h)

# Drifting

Load cells do drift with time. Good ones have specs on that topic.

Your completion resistors may contribute due to changes in resistance from changes in temperature.

If you need to measure at most 50 N, then you're only using 10% of the range of a 50 kg load cell.

Your HX711 may be one of those with floating E-. **Try connecting E- to the Arduino's ground.**

**E- needs to go to both the Arduino's ground and the load cell.**

# Chart no NodeRed

[https://stevesnoderedguide.com/using-the-node-red-chart-node](https://stevesnoderedguide.com/using-the-node-red-chart-node)

# Gerando app Android

```shell
npm install -g eas-cli
eas login
eas build:configure
eas build -p android --profile development    # APK instalável direto
```

# Usando a biblioteca HX711_ADC.h

[https://github.com/olkal/HX711_ADC/blob/master/examples/Calibration/Calibration.ino](https://github.com/olkal/HX711_ADC/blob/master/examples/Calibration/Calibration.ino)

```c
/*   This example file shows how to calibrate the load cell and optionally store the calibration   
value in EEPROM, and also how to change the value manually.   
The result value can then later be included in your project sketch or fetched from EEPROM.
   To implement calibration in your project sketch the simplified procedure is as follow:  */     
   
   LoadCell.tare();       
   //place known mass       
   LoadCell.refreshDataSet();       
   float newCalibrationValue = LoadCell.getNewCalibration(known_mass);
```
