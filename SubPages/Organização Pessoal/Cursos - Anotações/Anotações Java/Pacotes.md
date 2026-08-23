---

---
Na prática, pacotes são pastas com classes dentro

O caminho completo para a classe é chamado *Full Qualified Name - FQN*

> [!tip] 💡
> Quando métodos e classes não possuem nenhum modificador (public, protected, private) assume-se o modificador padrão <<default>> o qual permite a visibilidade apenas dentro do pacote.

> [!tip] 💡
> a ordem de restrição, do mais restritivo para o menos, é a seguinte:

***private >> default >> protected >> public***

# Trabalhando com Jar

> [!tip] 💡
> Arquivos .jar podem ser utilizados para compartilhar classes entre equipes/projetos.

Para gerar um .jar, basta utilizar a função exportar do eclipse.

Para importar em outro projeto, basta copiá-lo para uma pasta dentro do projeto (geralmente a pasta chama-se *libs*) e depois adicioná-lo ao *build path.*

Pode-se configurar também para gerar um .jar executável. Na prática o que o eclipse faz é colocar uma configuração dentro de um arquivo MANIFEST dentro da pasta META-INF no pacote gerado.