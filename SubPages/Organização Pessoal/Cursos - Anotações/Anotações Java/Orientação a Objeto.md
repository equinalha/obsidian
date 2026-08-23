---

---
# Orientação a Objeto

> [!tip] 💡
> Em uma classe java, o **this** retorna a referência p/ a própria instância (objeto) e é a mesma coisa que dar um println(<nomeDoObjeto>).

O formato desta referência é:
classe@<Hash Calculado da Classe>
exemplo: Conta@78308db1

> [!tip] 💡
> **static - **Define atributos e métodos que pertencem exclusivamente à classe. Não podem ser acessados a partir das instâncias. É útil, por exemplo, para implementar um contador de quantas instâncias daquela classe existem, desde que este contador seja incrementado no construtor da classe.

> [!tip] 💡
> **Construtor**
Quando não especificado, o java atribui um construtor padrão (vazio)
Pode existir mais de um construtor.
Quando um construtor é especificado, o java elimina o construtor padrão

# Visibilidade e modificadores de acesso

![[Orientação a Objeto synced block]]

# Herança e Polimorfismo

![[SubPages/Pessoal/images/Untitled 115.png]]

> [!tip] 💡
> Sugestão de leitura: ***Clean Code****, do autor ****Robert C Martin****,*

> [!tip] 💡
> **Herança: **A classe filha herda os atributos e métodos, mas **Não herda os construtores
**Se na classe mãe existir um construtor específico e não existir o construtor padrão, é necessário reescrever o construtor específico na classe filha (com os mesmos parâmetros)
**OBS: **Em Java, **não existe** herança múltipla.

> [!tip] 💡
> **Polimorfismo** permite que um objeto seja de um tipo mais genérico, instanciado por uma classe mais específica.

```java
Class Veiculo() {
	public void liga(){
		System.out.println("Ligando o Veículo");
	}
}

Class Carro() extends veiculo {
	public void liga(){
		System.out.println("Ligando o Carro");
	}
}

Class Moto() extends veiculo {
	public void liga(){
		System.out.println("Ligando a Moto");
	}
}

public static void main(String[] args){
	Veiculo c = new Carro();
	c.liga(); //Ligando o Carro
}
```

No exemplo acima, mesmo c sendo do tipo Veiculo, ele foi instanciado com a classe Carro, por consequência o método liga() a ser executado é o da classe mais específica.

No entanto, se a classe mãe não tiver o método, a classe filha também não terá.

Isto é útil quando precisamos passar objetos de classes diferentes como parâmetro de um outro método.

```java
Class Lavar(Veiculo v){
	// ...
}

//Vai funcionar com qualquer tipo relacionado.
```

> [!tip] 💡
> **Polimorfismo** permite que a referência para um objeto seja genérico.
Levando em consideração que as classes diversas sejam herdeiras de uma mesma classe genérica.

> [!tip] 💡
> **Classe Abstrata** faz com que a classe não possa ser instanciada diretamente. Na pratica ela só serve para servir de herança para as classes filhas. Exemplo:

**Funcionário (abstrata)**
> > [!tip] 💡
> > **Gerente
> Programador
> Designer
> AuxiliarAdministrativo**

> [!tip] 💡
> **Interface** é uma classe abstrata com todos os métodos abstratos. Funciona como um contrato em que as classes que o assinam, devem implementar os métodos da interface.

```java
public abstract interface Autenticavel {
	
	public abstract void setSenha(int senha);
	public abstract boolean autentica(int senha);

}
```

```java
public class Administrador extends Funcionario implements Autenticavel{

	private int senha;
	@Override
	public double getBonificacao() {
		// TODO Auto-generated method stub
		return 0;
	}

	@Override
	public void setSenha(int senha) {
		this.senha = senha;
		
	}

	@Override
	public boolean autentica(int senha) {
		if(this.senha == senha) {
			return true;
		}
		return false;
	}

}
```

# Enumerações

```java
public enum Prioridade {
	
	MIN(1),NORMAL(5),MAX(10);
	private int valor;
	
	Prioridade(int valor){
		this.valor = valor;
	}
	
	public int getValor() {
		return valor;
	}
}
```
