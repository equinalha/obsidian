---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:15:00
Owner:
  - Eduardo Quinalha
---
[https://www.youtube.com/watch?v=yuelcT2M9H0&list=PLuHxJ4iJDGDinarjcbKISxlL4pREhl8IR&index=11](https://www.youtube.com/watch?v=yuelcT2M9H0&list=PLuHxJ4iJDGDinarjcbKISxlL4pREhl8IR&index=11)

- Foco na manutenção de código
	- Dificuldade de entendimento do código
	- Relação direta com custo e tempo dentro da empresa
- Código deve agregar valor ao negócio
- Código limpo oferece qualidade e compreensão

# Código Limpo

- Simplicidade e eficiência
- Menor possível
- Conciso
- Nomes significativos
- Poucas dependências, explicitamente declaradas
- Exemplo:
	- Quando é necessário um comentário acima do nome do método, é um mal sinal
	- O nome do método deve ser significativo suficiente para que não seja necessário nenhum comentário

# Nomes Significativos

- Use nomes que revelam seu propósito
	- **Classes **→ substantivo
		- Cliente
		- Página
		- Conta
		- Endereço
	- **Métodos **→ Verbo no infinitivo
		- CriarFuncionario()
		- CadastrarConta()
		- etc.
	- **Variáveis** → Adicione um contexto significativo
- Use nomes pronunciáveis

# Funções

- Escreva funções pequenas
	- Mais de 20 linhas denota falta de otimização
	- Funções grandes são indícios de falta de coesão
- Priorizar funções ternárias
- Cada função deve fazer apenas uma coisa
- Parâmetros
	- O ideal é não ter parâmetros de entrada
	- Se não for possível, no máximo 3 parâmetros de entrada
	- Funções com mais de 3 dificultam os testes e depuração

# Comentários

- Comentários compensam um código ruim
- Comentários bons
	- Direitos autorais
	- Comentários informativos
	- ToDo
- Comentários ruidosos
	- Desnecessários.
	- É possível entender sem a presença dos comentários
- **Não explicar o código nos comentários!**
	- O código deve ser autoexplicativo

# Formatação

- Objetivo
	- Organização
- Declarar variáveis próximo do local do uso
- Ordenação vertical
	- Escrever os métodos na ordem em que são chamados

# Objetos e Estruturas de Dados

- Um método f de uma classe C só deve chamar métodos de:
	- C
	- Um objeto criado por f
	- Um objeto passado por parâmetro para f
	- Um objeto dentro de uma instância de C
- Use polimorfismo, interfaces, classes abstratas

# Tratamento de Erro

- Use exceções ao invés de retornar código
- Usar `try-catch-finally`
- Crie mensagens de erro informativas
- Não retorne null

# Limites

- Moderação no uso de bibliotecas de terceiros

# Teste de Unidade

- TDD
	- Não se deve escrever o código de produção até criar um teste de unidade de falhas
	- Não se deve escrever mais de um teste de unidade do que o necessário para falhar
	- Não se deve escrever mais código de produção do que o necessário para aplicar o teste de falha atual
- Teste Limpo
	- Legibilidade
	- Cada teste para uma coisa só
	- Testes devem ser rápidos
	- Independentes uns dos outros
	- Repetível em qualquer ambiente
	- Testes devem ter uma saída booleana

# Classes

- Pequenas, o menor possível
- Lista de variáveis
	- Primeiro as públicas
	- Em seguida as privadas
- Evitar variáveis públicas

# Sistemas

- Escaláveis
- De fácil manutenção
- Construção do sistema pensando em expansão
- Modularização
- Separação do main()
	- Não usar lógica de negócio na classe que inicia o sistema
- Injeção de dependência
	- Facilita a escalabilidade
	- Testabilidade
	- Manutenção
- Desenvolvimento Gradual
	- Implementar apenas os fatos de hoje
	- Refatorar e expandir implementando novos requerimentos
- Utilizar padrões quando este for adicionar valor ao cliente

# Emergência

- SOLID
- SRP
- DIP
- Princípios
	- Efetuar todos os testes
	- Sem duplicação de código
	- Expressar o propósito do programador
	- Minimizar o número de classes e métodos

# Concorrência

- Uso de threads somente será eficaz em sistemas multinúcleo ou multiprocessado
- Nem sempre o uso de threads irá melhorar o desempenho
	- Somente quando houver tempo de espera muito grande e que possa ser dividido entre múltiplos processadores
- Bloqueios que podem ocorrer pelo uso de threads:
	- Bound Resources → Recursos de tamanho limitados, por exemplo conexões de banco de dados e buffers de tamanho fixo
	- Exclusão Mútua
	- Espera indefinida (Starvation)]
	- Deadlock
	- Livelock → Competição de threads em que uma interfere na outra

# Refinamento Sucessivo

- Uma das melhores maneiras de arruinar um código é fazer modificações sucessivas a fim de melhorá-lo
- Alterar em blocos pequenos
- Sempre executar testes unitários após uma alteração

# JUnit

- Framework para o desenvolvimento de testes unitários
- Facilita automação de testes
