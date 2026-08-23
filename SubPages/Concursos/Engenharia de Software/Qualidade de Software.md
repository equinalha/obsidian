---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-14T08:07:00
Owner:
  - Eduardo Quinalha
---
# Definições

> [!warning] ⚠️
> O **controle de qualidade** tem como objetivo **testar** os produtos de software de modo a identificar, relatar e remover os defeitos encontrados, enquanto a **garantia da qualidade **provê a **gerência** sênior da organização com a **visibilidade apropriada sobre o processo de desenvolvimento.**

> [!warning] ⚠️
> Os processos no ciclo de vida de um produto de software podem ser classificados como **fundamentais**, **de apoio** ou **organizacionais**. O processo  de **garantia da qualidade** pode ser considerado um **processo de apoio** que define atividades para garantir a conformidade dos processos e produtos de software com requisitos e planos estabelecidos. Um processo de garantia da qualidade pode abranger a garantia da qualidade do produto, do processo e do sistema de qualidade.

O gerenciamento de qualidade de software pode ser estruturado em três atividades principais: 

- **garantia de qualidade**
	- assegurar que os processos e os produtos de software, no ciclo de vida do projeto, estão em conformidade com os padrões, os procedimentos e as descrições de processos definidos para o projeto submetidos a essa atividade.
	- atividades planejadas e sistemáticas visando garantir que o projeto empregará os processos necessários para atender aos requisitos
- **planejamento de qualidade**
- **controle de qualidade**
	- monitora resultados do projeto a fim de determinar se eles estão de acordo com os padrões relevantes de qualidade e procura identificar meios para eliminar as causas de resultados que sejam insatisfatórios.

# Métricas de Qualidade

- **Correção**
	- Um programa deve operar corretamente ou é de pouco valor para seus usuários.
- **Manutenibilidade**
	- É a facilidade com que um programa pode ser corrigido, se um erro é encontrado, adaptado, se seu ambiente se modifica ou é aperfeiçoado, se o cliente deseja uma alteração nos requisitos.
- **Integridade**
	- Mede a capacidade de um sistema resistir a ataques (tanto acidentais quanto intencionais) à sua segurança.
- **Usabilidade**
	- É a tentativa de quantificar facilidade de uso.

# Atributos de Qualidade de Software

Boehm et al. (1978) sugeriu que havia 15 (quinze) atributos importantes de qualidade de software. Esses atributos estão relacionados com a confiança, a usabilidade, a eficiência e a manutenibilidade de software.

> [!warning] ⚠️
> É **impossível** que algum sistema seja otimizado em todos esses atributos. 
• O plano de qualidade deve **definir os atributos de qualidade mais importantes** para o software que está sendo desenvolvido.

![[Untitled 659.png]]

# Fatores de Qualidade de McCall

- Correção
• O quanto um programa satisfaz a sua especificação e atende aos objetivos da missão do cliente.
- Confiabilidade
• O quanto se pode esperar que um programa realize a função pretendida com a precisão exigida.
- Eficiência
• A quantidade de recursos computacionais e códigos exigidos por um programa para desempenha sua função.
- Integridade
• O quanto o acesso ao software ou dados por pessoas não autorizadas pode ser controlado.
- Usabilidade
• Esforço necessário para aprender, operar, preparar a entrada de dados e interpretar a saída de um programa.
- Facilidade de manutenção
• Esforço necessário para localizar e corrigir um erro em um programa.
- Flexibilidade
• Esforço necessário para modificar um programa em operação.
- Testabilidade
• Esforço necessário para testar um programa de modo a garantir que ele desempenhe a função destinada.
- Portabilidade
• Esforço necessário para transferir o programa de um ambiente de hardware e/ou software para outro.
- Reusabilidade
• O quanto um programa (ou partes) pode ser reutilizado em outras aplicações – relacionado com o empacotamento e o escopo das funções que o programa executa.
- Interoperabilidade
• Esforço necessário para integrar um sistema a outro.

![[Untitled 660.png]]

# 🔥 Verificação e Validação (V&V)

- Processos de verificação e análise que asseguram que o software cumpra com suas especificações e atenda às necessidades dos clientes que estão pagando por ele.
- Ocorrem durante todo o ciclo de vida do software
	- Revisões dos requisitos
	- Revisões de projeto
	- Inspeções de código
	- Testes de produto
- Objetivos
	- Verificação
		- Descobrimento de defeitos
		- Está de acordo com os requisitos
		- Implementa corretamente as funções especificadas
		- Cumprimento das especificações
		- Atividades:
			- Inspeções e revisões de software
			- Testes de software
	- Validação
		- Avaliação da utilidade e adequação do sistema em uma situação operacional
		- o software está alinhado as reais necessidades do sistema
		- Atende às necessidades do cliente?
		- Implementa o que o cliente realmente desejava?
		- Atividades
			- Homologação
			- Testes de aceitação (beta)
			- Revisões com foco no cliente e usuário

> [!warning] ⚠️
> V&V **não garante que o software está livre de defeitos**, mas apenas garante certo nível de confiabilidade.

> [!note] 🔥
> A **validação** assegura que o produto, como fornecido, irá atender o seu uso pretendido, ou seja, que se está construindo o produto certo. 
E a **verificação** confirma que os produtos de trabalho refletem de forma apropriada os requisitos que foram especificados, ou seja, que
se está construindo o produto corretamente.

> [!note] 🔥
> Entre os principais processos da gestão da qualidade de software, estão a verificação, a validação, a revisão e a auditoria. Os processos de **verificação e validação são processos mais associados ao controle que à garantia da qualidade.**

# Manutenção de software

- Corretiva
▪ Correção de erros encontrados na verificação ou na validação.
- Adaptativa
▪ Adaptação a mudanças externas.
- Melhoria (perfectiva)
▪ Melhorias requeridas pelos usuários.
- Preventiva ou de reengenharia
▪ Abordagem pró-ativa com foco na melhoria da manutibilidade.

# Papéis

- Quality Assurance (QA)
	- responsável por garantir a qualidade do projeto por meio da definição de processos e padrões bem como assegurar que estes sejam seguidos.
	- preparação e execução de planos de testes,
	- SQA é um conjunto de atividades que garantem a qualidade no processo de desenvolvimento de software, focando na prevenção de defeitos e na melhoria do processo, ao invés de apenas na identificação e correção de defeitos no produto final.
	- SQA avalia aspectos como:
		- Adesão a padrões;
		- Revisões e inspeções;
		- Testes de software;
		- Gestão de configuração de software;
		- Planejamento de qualidade;
		- Medição e análise de processos e produtos.
- Desenvolvedores
	- documentação de desvios dos padrões
	- detecção e correção de problemas

# ISO/IEC 9126

## Características da Norma

- **Foco no produto de software**

> [!note] 🔥
> Não leva em consideração o processo

- **Qualidade Interna e Externa**
	- CEF MPU
		- Confiabilidade
		- Eficiência
		- Funcionalidade
		- Manutenibilidade
		- Portabilidade
		- Usabilidade
- **Qualidade em Uso**
	- PESS
		- Produtividade
		- Eficácia
		- Segurança
		- Satisfação

> [!note] 🔥
> Qualidade externa determina qualidade interna

## Conceitos

- **Funcionalidade**
	- Capacidade do produto de software de satisfazer os requisitos funcionais esperados
	- foca em quão bem o software executa as funções para as quais foi projetado e se essas funções atendem às necessidades específicas dos usuários.
	- Critérios (Subatributos):
		- **Adequabilidade:** refere-se à capacidade do software de fornecer um conjunto apropriado de funções para tarefas especificadas.
		- **Exatidão:** diz respeito à capacidade do software de fornecer os resultados corretos ou esperados.
		- **Interoperabilidade:** é a capacidade do software de interagir com um ou mais sistemas especificados.
		- **Conformidade:** trata da adesão do software aos padrões, convenções ou regulamentações em vigor.
		- **Segurança:** avalia a capacidade do software de proteger informações e dados, de modo que pessoas não autorizadas não possam acessá-los ou modificá-los.
		- **Proteção de Dados**: Indica a capacidade do software de proteger os dados contra acesso não autorizado, alteração ou destruição, bem como de garantir a sua confidencialidade, integridade e disponibilidade.
- **Confiabilidade**
	- Capacidade do produto de software de funcionar sem falhas durante um período especificado sob condições de uso especificadas
	- Subcaracterísticas:
		- **Maturidade:** capacidade do software de evitar falhas quando em uso sob condições normais.
		- **Tolerância a falhas: **Indica a capacidade do software de manter um nível aceitável de desempenho, mesmo diante de falhas ou condições adversas.
		- **Recuperabilidade: **Diz respeito à capacidade do software de recuperar-se de falhas, erros ou interrupções, restaurando o sistema para um estado operacional adequado.
		- **Integridade**: Refere-se à precisão e completude dos dados e do processamento do software, garantindo que o sistema opere de forma confiável e consistente.
		- **Conformidade**: Indica o quão bem o software adere a padrões, convenções e regulamentações pré-definidas. Um software que está em conformidade é mais confiável, pois atende a expectativas específicas de qualidade e segurança.
		- **Segurança**: Embora não seja uma característica diretamente mencionada na ISO/IEC 9126, a segurança é fundamental para a confiabilidade do software. Ela abrange a proteção contra acessos não autorizados, ataques maliciosos e a garantia da privacidade dos dados.
- **Eficiência**
	- Capacidade do produto de software de realizar suas funções com o uso mínimo de recursos
	- Características:
		- **Comportamento em relação ao tempo**: Refere-se ao desempenho do software em relação ao tempo de resposta e processamento. Isso inclui a rapidez com que o software executa suas funções e responde às entradas do usuário, garantindo uma experiência de usuário satisfatória.
		- **Utilização de recursos**: Indica a eficiência no uso de recursos do sistema, como memória, processamento e largura de banda de rede. Um software eficiente deve ser otimizado para consumir recursos de forma econômica, evitando desperdícios e maximizando a utilização dos recursos disponíveis.
		- **Capacidade**: Refere-se à capacidade do software de lidar com uma carga de trabalho específica sem degradação significativa no desempenho. Isso inclui a capacidade de lidar com grandes volumes de dados, processar operações complexas e suportar um número esperado de usuários simultâneos.
		- **Conformidade**: Indica a conformidade do software com padrões e regulamentos relacionados à eficiência, como normas de desempenho e eficiência energética. O software deve atender a esses padrões para garantir um uso eficiente dos recursos e minimizar o impacto ambiental.
		- **Estabilidade**: Refere-se à estabilidade do software durante o uso normal e sob condições adversas. Um software eficiente deve ser robusto o suficiente para lidar com falhas e exceções sem comprometer o desempenho ou a disponibilidade do sistema.
- **Usabilidade**
	- Capacidade do produto de software de ser usado por usuários especificados para alcançar objetivos especificados com eficácia, eficiência e satisfação
	- Características
		- **Compreensibilidade**: Refere-se à facilidade de compreensão do sistema por parte do usuário, incluindo a clareza das informações apresentadas, a organização da interface e a consistência das operações. Um software com alta compreensibilidade permite que os usuários entendam facilmente como usar o sistema e realizar suas tarefas.
		- **Aprendizagem**: Indica a facilidade com que os usuários podem aprender a usar o sistema, seja através de instruções fornecidas, feedbacks claros ou uma interface intuitiva. Um software que facilita a aprendizagem reduz o tempo necessário para os usuários se familiarizarem com o sistema e começarem a usá-lo de forma eficaz.
		- **Operabilidade**: Refere-se à facilidade e eficiência com que os usuários podem operar o sistema, incluindo a facilidade de navegação, a simplicidade das operações e a disponibilidade de recursos de ajuda. Um software operável permite que os usuários realizem suas tarefas de forma rápida e eficiente, sem frustrações ou dificuldades desnecessárias.
		- **Atratividade**: Indica o apelo estético e visual do sistema, incluindo o design da interface, o layout dos elementos e o uso de elementos gráficos. Um software atrativo é mais agradável de usar e pode aumentar a motivação dos usuários para interagir com o sistema.
		- **Satisfação do usuário**: Refere-se à percepção geral dos usuários sobre a experiência de uso do sistema, incluindo a facilidade de uso, a eficácia na realização de tarefas e o grau de satisfação com o sistema. Um software que proporciona uma experiência positiva aos usuários aumenta a sua satisfação e a probabilidade de uso contínuo.
- **Manutenibilidade**
	- Capacidade do produto de software ser modificado para corrigir defeitos, melhorar a performance ou adicionar novas funcionalidades
	- Características
		- **Analisabilidade**: Refere-se à facilidade de entender o código-fonte e a estrutura do software, incluindo a clareza da documentação, a modularidade do código e a identificação de dependências entre os componentes. Um software com alta analisabilidade é mais fácil de entender e diagnosticar em caso de problemas.
		- **Modificabilidade**: Indica a facilidade com que o software pode ser modificado para atender a novos requisitos ou implementar mudanças no sistema. Isso inclui a flexibilidade do design, a separação de preocupações e a facilidade de adicionar, modificar ou remover funcionalidades sem causar impactos indesejados em outras partes do sistema.
		- **Estabilidade**: Refere-se à capacidade do software de resistir a mudanças sem introduzir novos defeitos ou comprometer a integridade do sistema. Um software estável é menos propenso a efeitos colaterais indesejados durante as modificações e atualizações.
		- **Testabilidade**: Indica a facilidade de testar o software para garantir sua qualidade e detectar defeitos. Isso inclui a disponibilidade de ferramentas de teste, a modularidade do código para facilitar a criação de casos de teste e a capacidade de simular diferentes cenários de uso.
		- **Reusabilidade**: Refere-se à capacidade de reutilizar componentes de software em diferentes contextos e projetos, reduzindo assim o esforço de desenvolvimento e aumentando a consistência e confiabilidade do software. Componentes reutilizáveis são mais fáceis de manter e atualizar, pois mudanças feitas em um componente podem beneficiar todos os sistemas que o utilizam.
- **Portabilidade**
	- Capacidade do produto de software de ser transferido de um ambiente de execução para outro
	- Características
		- **Adaptabilidade**: Refere-se à capacidade do software de se adaptar a diferentes ambientes de execução, como diferentes sistemas operacionais, plataformas de hardware ou configurações de rede. Um software adaptável pode ser facilmente configurado e executado em diferentes ambientes sem a necessidade de modificação do código-fonte.
		- **Instalabilidade**: Indica a facilidade de instalar e configurar o software em um novo ambiente. Isso inclui a disponibilidade de instruções claras de instalação, a automação do processo de instalação sempre que possível e a compatibilidade com os procedimentos de instalação padrão do sistema operacional.
		- **Coexistência**: Refere-se à capacidade do software de operar de forma independente de outros softwares instalados no mesmo ambiente. Um software que pode coexistir pacificamente com outros aplicativos minimiza conflitos e problemas de compatibilidade.
		- **Substituibilidade**: Indica a capacidade do software de substituir outro software similar em um ambiente sem causar interrupções significativas ou perda de funcionalidade. Isso envolve garantir que o software seja compatível com os formatos de dados e interfaces utilizados pelo software substituído.
		- **Facilidade de atualização**: Refere-se à facilidade de atualizar o software para uma versão mais recente ou corrigida. Isso inclui a disponibilidade de procedimentos de atualização simples e seguros, a compatibilidade entre diferentes versões do software e a capacidade de migrar dados e configurações entre versões.

# Dimensões de Qualidade de Software

**1 - Qualidade do design**

A qualidade de design do software pode ser medida decompondo o processo em atributos de qualidade como usabilidade, extensibilidade, escalabilidade, capacidade de manutenção e reutilização, testabilidade, confiabilidade, segurança e desempenho, dentre outros.

**2 – Qualidade de conformidade**

Aborda se o software desenvolvido condiz com aquilo que foi determinado pelos requisitos de negócios. O software deve estar em conformidade com o design, aplicar padrões ou convenções apropriados e deve ser entregue no prazo e dentro do orçamento.

**3 – Qualidade de desempenho.**

Lida com a forma como o software é entregue. O software deve estar disponível conforme o necessário para o uso, trabalhar de forma confiável e precisa da maneira pretendida, lidar com a carga de trabalho dos usuários adequadamente e possuir o suporte técnico e manutenção de maneira responsiva.
