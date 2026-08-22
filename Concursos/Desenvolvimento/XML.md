---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:19:00
Owner:
  - Eduardo Quinalha
---
# Atributos vs Elementos

- Atributos
	- Não podem ter repetições
	- Chave - Valor
	- Valor sempre entre aspas
	- Não podem ter elementos filhos
- Elementos
	- Pode haver repetições (array)
	- Podem ter elementos filhos

# Namespaces

- Serve para resolver conflitos (elementos com o mesmo nome)
- O namespace é declarado com o atributo **xmlns** na tag de abertura do elemento ou na tag raíz

```xml
// Sintaxe: xmlns:prefix="URI" > Na verdade pode ser outro identificador, não somente uma URI, desde que seja único
// Exemplo:
<raiz>
	<a:flamengo xmlns:a="http://www.flamengo.com.br">
		 <a:esporte>Futebol</a:esporte>
		 <a:mascote>Urubu</a:mascote>
	</a:flamengo>
	<b:flamengo xmlns:b="https://prefeitura.rio">
		 <b:populacao>50.640</b:populacao>
		 <b:distrito>Zona Sul</b:distrito>
	</b:flamengo>
</raiz>

// Outra forma
<raiz xmlns:a="http://www.flamengo.com.br"
		xmlns:b="https://prefeitura.rio">
		<a:flamengo>
			 <a:esporte>Futebol</a:esporte>
			 <a:mascote>Urubu</a:mascote>
		</a:flamengo>
		<b:flamengo>
		 <b:populacao>50.640</b:populacao>
		 <b:distrito>Zona Sul</b:distrito>
		</b:flamengo>
	</raiz>
```

- Quando o namespace é inserido no próprio elemento, não é necessário usar prefixo nos filhos

```xml
<flamengo xmlns:a="http://www.flamengo.com.br">
 <esporte>Futebol</esporte>
 <mascote>Urubu</mascote>
</flamengo>
<flamengo xmlns:b="https://prefeitura.rio">
 <populacao>50.640</populacao>
 <distrito>Zona Sul</distrito>
</flamengo>
```

# Regras de formação

<!-- Column 1 -->
1. Devem possuir um único elemento raíz
2. Todos os elementos devem possuir tag de fechamento
3. Devem estar corretamente aninhados
4. Atributos devem possuir valor entre aspas simples ou duplas
5. Nomes de tags são case-sensitive

## Validação

Existem dois tipos principais de arquivos de validação (esquema):

- DTD
	- Pode estar definido dentro do próprio arquivo XML ou em um arquivo separado com a extensão .dtd
```xml
<!-- Dentro do XML -->
<!DOCTYPE carta
[
<!ELEMENT carta (de,para,assunto,corpo)>
<!ELEMENT de (#PCDATA)>
<!ELEMENT para (#PCDATA)>
<!ELEMENT assunto (#PCDATA)>
<!ELEMENT corpo (#PCDATA)>
]>

<!-- Arquivo externo -->
<!DOCTYPE carta SYSTEM "dados.dtd">
```
	- **Notações:**
		- ==#PCDATA== - Dado a ser verificado pelo validador
		- ==#CDATA== - Dados que não serão validados
		- ==**+**==** **- Elemento obrigatório 1 ou mais ocorrências
		- ==*****==** **- Elemento opcional 0 ou mais ocorrências
		- ==**? **==- Elemento opcional 0 ou 1 vez
		- ==**Sem nenhum símbolo**== - Elemento obrigatório 1 única ocorrência
- XSD
	- Mais recursos que o DTD
	- Escrito em XML
	- Permite a criação de namespaces
	- Exemplos
```xml
<xs:element name="categoria">
	<xs:simpleType>
		<xs:restriction base="xs:string">
			<xs:pattern value="hatch|sedan"/>
		</xs:restriction>
	</xs:simpleType>
</xs:element>
```
```xml
<xs:element name="cidade"  type="xs:string" fixed="Vilhena"/>
```

## XSD vs DTD

| No. | DTD | XSD |
| --- | --- | --- |
| 1) | DTD stands for **Document Type Definition**. | XSD stands for XML Schema Definition. |
| 2) | DTDs are derived from **SGML** syntax. | XSDs are written in XML. |
| 3) | DTD **doesn't support datatypes**. | XSD **supports datatypes** for elements and attributes. |
| 4) | DTD **doesn't support namespace**. | XSD **supports namespace**. |
| 5) | DTD **doesn't define order** for child elements. | XSD **defines order** for child elements. |
| 6) | DTD is **not extensible**. | XSD is **extensible**. |
| 7) | DTD is **not simple to learn**. | XSD is **simple to learn** because you don't need to learn new language. |
| 8) | DTD provides **less control** on XML structure. | XSD provides **more control** on XML structure. |

<!-- Column 2 -->


## XSLT

- Usado para transformar XML em outro documento
- Pode ser outro XML, HTML ou outro formato interpretado por browser
- Usa um XML como template e outro como dados
- Utiliza XPATH para navegar entre os elementos do documento
	- Sintaxe utilizada para definir partes de um documento XML
	- Contém uma biblioteca de funções padrão
	- **XPath é um elemento importante em XSLT e em XQuery**
![[Untitled 747.png]]
	- Exemplos:

| /bookstore/book[1] | Selects the first book element that is the child of the bookstore element |
| --- | --- |
| /bookstore/book[last()] | Selects the last book element that is the child of the bookstore element |
| /bookstore/book[last()-1] | Selects the last but one book element that is the child of the bookstore element |
| /bookstore/book[position()<3] | Selects the first two book elements that are children of the bookstore element |
| //title[@lang] | Selects all the title elements that have an attribute named lang |
| //title[@lang='en'] | Selects all the title elements that have a "lang" attribute with a value of "en" |
| /bookstore/book[price>35.00] | Selects all the book elements of the bookstore element that have a price element with a value greater than 35.00 |
| /bookstore/book[price>35.00]/title | Selects all the title elements of the book elements of the bookstore element that have a price element with a value greater than 35.00 |

```xml
<xsl:template match="/">
  <html>
    <body>
      <table border="1">
        <tr>
          <th>descricao</th>
        </tr>
        <xsl:for-each select="catalogo/item">
          <xsl:sort select="quantidade"/>
          <tr>
            <td>
              <xsl:value-of select="descricao"/>
            </td>
          </tr>
        </xsl:for-each>
      </table>
    </body>
  </html>
</xsl:template>
```

```xml
<?xml-stylesheet type="text/xsl" href="catalogo.xsl"?>
<catalogo>
  <item>
    <descricao>item1</descricao>
    <quantidade>250</quantidade>
  </item>
  <item>
    <descricao>item2</descricao>
    <quantidade>20</quantidade>
  </item>
</catalogo>
```
