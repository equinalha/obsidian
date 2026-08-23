---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-12T07:44:00
Owner:
  - Eduardo Quinalha
---
[https://mange.ifrn.edu.br/shell-script-wikipedia/05-variaveis.html](https://mange.ifrn.edu.br/shell-script-wikipedia/05-variaveis.html)

# Variáveis

- Não é necessário definir tipo
- Atribuição direta

```bash
MENSAGEM_DATA=1979
MENSAGEM_NOME="Bourne Shell"
mensagem_tipo1="Unix Shell"
mensagem_autor="Stephen Bourne"
MENSAGEM=ola
_MENSAGEM2=oi-2.020
```

## Variáveis pré-definidas

- `$?` - Armazena o **status de saída** do último programa executado;
- `$#` - Armazena a **quantidade de parâmetros **de linha de comandos;
- `$$` - Armazena o valor **PID** (Process Identifier) do script em shell que estiver em execução;
- `$@` - Armazena o valor de **todos os parâmetros passados**, similar a variável argv presente nas linguagens de programação C e C++;
- `$!` - Armazena o PID do último processo em segundo plano. Isso é útil para acompanhar o processo à medida que o trabalho é realizado;
- `$0, ..., $9` - Armazena os valores de todos os parâmetros de linha de comando separadamente.

## Variáveis globais

- Definidas com o comando `export`
- Podem ser utilizadas por múltiplos scripts
- Algumas já vem pré-definidas:
	- `PATH`: define diretórios de procura por programas executados no shell;
	- `USER`: informa o nome do usuário do shell;
	- `HOME`: informa o caminho do diretório home do usuário;
	- `LANG`: Idioma/Linguagem, especificada como locale;
	- `PWD`: diretório atual;
	- `TERM`: Tipo de terminal atual em uso.
	- `UID`: UID do usuário atual.
	- `RANDOM`: Gera um número aleatório

## Array

- O Bourne Shell (sh) não é compatível com variáveis do tipo array
- Para usar array, deve-se utilizar o **bash**

```bash
#!/usr/bin/env bash

meu_array=(1 2 3 4 5 6 7 8 9)
meu_Array=("abc" "def" "ghi")
```

## Chamando variáveis

- Para chamar variáveis utiliza-se o sinal de cifrão `$var`
- O cifrão (`$`) também é bastante utilizado em script sh, para executar programas externos 
	- exemplo: `var=$(expr 2 + 2)` irá armazenar a saída do programa `expr`.
- o cifrão mais chave `${var}` é comum ser utilizado das seguintes maneiras:
	- Para acessar posições em um array `${var[1]}`
	- substituir o valor de uma variável se a mesma não possuir um valor: `${var:-nome}`
```bash
read -p "Digite um nome: "myname
echo "${myname:=$(whoami)}"
```
	- No exemplo acima, caso o usuário não digite um nome, será exibido o valor retornado pelo comando `whoami`

## Removendo variáveis

- Basta utilizar o comando `unset` + `nome_da_variável`

# Estruturas condicionais

## If

```bash
# Forma padrão
if [ $1 = $2 ]; then
    echo "Parametro 1=$1 é igual a 2=$2."
fi

# Forma resumida
[ $1 = $2 ] && { echo "Parametro 1 ($1) é igual a 2 ($2)."; exit 0; }
```

## If - else

```bash
# Forma padrão
if [ $1 = $2 ];then echo "Parametro 1 ($1) é igual a 2 ($2)."
else echo "Parametro 1 ($1) não é igual a 2 ($2)."
fi

# Forma resumida
[ $1 = $2 ] && { echo "Parametro 1 ($1) é igual a 2 ($2)."; exit 0; } || { echo "Parametro 1 ($1) é diferente de 2 ($2)."; exit 0; }
```

## Elif

```bash
if [ $3 ]; then
    echo "$3"
elif [ $2 ]; then
    echo "$2"
else
    echo "$1"
fi
```

## Case

```bash
case "$var" in
    valor1)
    ;;

    valor2)
    ;;

    valor3)
    ;;

    valor4|valor5|valor6)
    ;;
    
    *)
    ;;
esac
```

# Operadores

## Booleanos

```bash
# Not
[ ! $x = 22 ]

# Or
[ $x = 22 -o $x = 23 ]

# And
[ $y = 22 -a $x = 22 ]
```

## Teste em arquivos

| **Operadores** | **Descrição** | **Exemplos** |
| --- | --- | --- |
| `-b` | Verifica se o arquivo é um arquivo especial de **bloco**; se sim, então a condição se torna verdadeira. | `[ -b /etc/resolv.conf ]` |
| `-c` | Verifica se o arquivo é um arquivo especial de **caracteres**; se sim, então a condição se torna verdadeira. | `[ -c /etc/resolv.conf ]` |
| `-d` | Verifica se o arquivo é um **diretório**; se sim, então a condição se torna verdadeira | `[ -d /etc/resolv.conf ]` |
| `-f` | Verifica se arquivo é um **arquivo comum** em oposição a um diretório ou arquivo especial; se sim, então a condição se torna verdadeira. | `[ -f /etc/resolv.conf ]` |
| `-g` | Verifica se o arquivo possui o seu conjunto de bits de identificação de **grupo **(SGID); se sim, então a condição se torna verdadeira. | `[ -g /etc/resolv.conf ]` |
| `-k` | Verifica se o arquivo tem seu bit fixo definido; se sim, então a condição se torna verdadeira. | `[ -k /etc/resolv.conf ]` |
| `-p` | Verifica se o arquivo é um pipe nomeado; se sim, então a condição se torna verdadeira. | `[ -p /etc/resolv.conf ]` |
| `-t` | Verifica se o descritor de arquivo está aberto e associado a um terminal; se sim, então a condição se torna verdadeira. | `[ -t /etc/resolv.conf ]` |
| `-u` | Verifica se o arquivo tem seu bit Set ID do usuário (SUID) definido; se sim, então a condição se torna verdadeira. | `[ -u /etc/resolv.conf ]` |
| `-r` | Verifica se o arquivo está legível; se sim, então a condição se torna verdadeira. | `[ -r /etc/resolv.conf ]` |
| `-w` | Verifica se o arquivo é gravável; se sim, então a condição se torna verdadeira. | `[ -w /etc/resolv.conf ]` |
| `-x` | Verifica se o arquivo é executável; se sim, então a condição se torna verdadeira. | `[ -x /etc/resolv.conf ]` |
| `-s` | Verifica se o arquivo tem tamanho maior que 0; se sim, então a condição se torna verdadeira. | `[ -s /etc/resolv.conf ]` |
| `-e` | Verifica se o arquivo existe; é verdadeiro mesmo se o arquivo for um diretório, mas existe. | `[ -e /etc/resolv.conf ]` |

## Relacionais

| **Operadores** | **Descrição** | **Exemplos** |
| --- | --- | --- |
| `-eq` | Verifica se o valor de dois operandos é igual ou não; se sim, então a condição se torna verdadeira. | `[ $x -eq 2 ]` |
| `-ne` | Verifica se o valor de dois operandos é igual ou não; se os valores não forem iguais, a condição se tornará verdadeira. | `[ $x -ne 2 ]` |
| `-gt` | Verifica se o valor do operando esquerdo é maior que o valor do operando direito; se sim, então a condição se torna verdadeira. | `[ $x -gt 2 ]` |
| `-lt` | Verifica se o valor do operando esquerdo é menor que o valor do operando direito; se sim, então a condição se torna verdadeira. | `[ $x -lt 2 ]` |
| `-ge` | Verifica se o valor do operando esquerdo é maior ou igual ao valor do operando direito; se sim, então a condição se torna verdadeira. | `[ $x -ge 2 ]` |
| `-le` | Verifica se o valor do operando esquerdo é menor ou igual ao valor do operando direito; se sim, então a condição se torna verdadeira. | `[ $x -le 2 ]` |

## String

| **Operadores** | **Descrição** | **Exemplos** |
| --- | --- | --- |
| `-z` | Verifica se o tamanho do operando da string fornecido é zero; se tiver comprimento zero, retornará verdadeiro. | `[ -z $str ]` |
| `-n` | Verifica se o tamanho do operando da string especificado é diferente de zero; se tiver um comprimento diferente de zero, retornará true. | `[-n $str ]` |
| `[ $uma_var ]` | Verifica se `uma_var` não é a string vazia; se estiver vazio, ele retornará false. | `[ $str ]` |

# Estruturas de repetição

## For

```bash
# Irá executar echo "Test" 3 vezes
for i in 1 2 3
do
    echo "Test"
done

# Em apenas uma linha
for i in 1 2 3; do echo "Test"; done

# Números ímpares de 1 a 20
for j in $(seq 1 2 20)
do
    echo $j
done

# Números ímpares de 1 a 20
for j in {1..20..2}
do
    echo $j
done

for ((j=1; j<20; j+=2))
do
    echo $j
done
```

## While

```bash
while [ -z $a_input ]; do
    read -p "Enter para continuar ou digite qualquer coisa para sair: " a_input
done

while [ -z $b_input ]; do 
    read -p "Enter para continuar ou digite qualquer coisa para sair: " b_input 
done

while read -p "Digite um numero: " c_input
do
    if [ $c_input -gt 25 ]; then
        echo "Numero $c_input é maior que 25"
        break
    else
        echo "Numero $c_input é menor que 25"
        break
    fi
done
```

# Funções

- O scripts em Shell também aceitam funções. 
- **Bash** e **sh** aceitam um mesmo padrão de funções, mas o **Bash** também aceita um outro formato que o sh não reconhece. 
- Ambos formatos são mostrados abaixo:

```bash
# Ambos aceitam esse formato
minha_função(){
    echo
}
# Esse formato apenas Bash aceitará
function minha_função(){
    echo
}
```

# Status de saída

- Variam entre 0 e 255
- `0 `significa que a execução foi bem sucedida
- exemplo

```bash
# Se não existir /bin/bash sai com status 2
[ ! -e /bin/bash ] && { exit 2; }

ping -c1 wikipedia..org
[ $? -ne 0 ] && echo "O comando ping emitiu algum erro."
```
