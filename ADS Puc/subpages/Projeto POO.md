---
base: "[[ADS - PUC-PR.base]]"
Class: POO
Reviewed: false
Created: 2022-05-27T11:20:00
Type: Study Group
Status: Not started
Description: ""
---
```java
public class Acompanhamento extends Item {

	private String descricao;
	private int codigo;

	public Acompanhamento(String nome, double preco, String descricao) {
		super(nome, preco);
		this.codigo = super.getCodigo();
		this.descricao = descricao;
	}

	public String getDescricao() {
		return descricao;
	}

	public int getCodigo() {
		return codigo;
	}

}
```

```java
public class Bebida extends Item {
	
	int tamanho; //em ml
	int codigo;
	
	public Bebida(String descricao, double preco, int tamanho) {
		super(descricao, preco);
		this.tamanho = tamanho;
		this.codigo = super.getCodigo();
	}

	public int getCodigo() {
		return codigo;
	}

	public int getTamanho() {
		return tamanho;
	}

}
```

```java
import java.util.ArrayList;
import java.util.Formatter;

public class Cardapio {
	ArrayList<Acompanhamento> acompanhamentos = new ArrayList<>();
	ArrayList<Bebida> bebidas = new ArrayList<>();
	ArrayList<Lanche> lanches = new ArrayList<>();

	public ArrayList<Acompanhamento> getAcompanhamentos() {
		return acompanhamentos;
	}

	public ArrayList<Bebida> getBebidas() {
		return bebidas;
	}

	public ArrayList<Lanche> getLanches() {
		return lanches;
	}

	@Override
	public String toString() {

		Formatter fmt = new Formatter();
		fmt.format("\n", "");
		fmt.format("%30s", "Lanches\n\n");
		for (Lanche lanche : lanches) {
			fmt.format("%4s. %-30s R$ %.2f (%20s)\n", lanche.getCodigo(), lanche.getNome(), lanche.getPreco(), lanche.getDescricao());
		}
		fmt.format("\n", "");
		fmt.format("%30s", "Bebidas\n\n");
		for (Bebida bebida : bebidas) {
			fmt.format("%4s. %-30s R$ %.2f\n", bebida.getCodigo(), bebida.getNome() + " " + bebida.getTamanho(), bebida.getPreco());
		}
		fmt.format("\n", "");
		fmt.format("%30s", "Acompanhamentos\n\n");
		for (Acompanhamento acompanhamento : acompanhamentos) {
			fmt.format("%4s. %-30s R$ %.2f (%15s)\n", acompanhamento.getCodigo(), acompanhamento.getNome(), acompanhamento.getPreco(), acompanhamento.getDescricao());
		}

		String cardapio = fmt.toString();
		fmt.close();
		return cardapio;
	}

	public void insereNovoAcompanhamento(Acompanhamento acompanhamento) {
		this.acompanhamentos.add(acompanhamento);
	}

	public void insereNovaBebida(Bebida bebida) {
		this.bebidas.add(bebida);
	}

	public void insereNovoLanche(Lanche lanche) {
		this.lanches.add(lanche);
	}

}
```

```java
public class Item {
	private String nome;
	static private int codigo = 1;
	private double preco;

	public Item(String nome, double preco) {
		super();
		this.nome = nome;
		this.preco = preco;
		Item.codigo++;
	}

	public String getNome() {
		return nome;
	}

	public int getCodigo() {
		return codigo;
	}

	public double getPreco() {
		return preco;
	}

}
```

```java
public class Lanche extends Item {
	private int codigo;
	private String descricao;

	public Lanche(String nome, double preco, String descricao) {
		super(nome, preco);
		this.codigo = super.getCodigo();
		this.descricao = descricao;
	}

	public String getDescricao() {
		return descricao;
	}

	public int getCodigo() {
		return codigo;
	}

}
```

```java
public class Main {

	public static void main(String[] args) {
		
		Cardapio cardapio = new Cardapio();
		
		cardapio.insereNovaBebida(new Bebida("Coca-cola", 10.0, 500));
		cardapio.insereNovaBebida(new Bebida("Sprite", 10.0, 500));
		cardapio.insereNovaBebida(new Bebida("Chopp IPA", 25.0, 700));
		cardapio.insereNovaBebida(new Bebida("Chopp Lager", 20.0, 700));
		cardapio.insereNovaBebida(new Bebida("Chopp Pale Ale", 20.0, 700));
		
		cardapio.insereNovoLanche(new Lanche("X-burger", 15.0, "Pão francês, queijo mussarela e hambúrger de 200g"));
		cardapio.insereNovoLanche(new Lanche("X-salada", 17.0, "Pão francês, queijo mussarela, salada e hambúrger de 200g"));
		cardapio.insereNovoLanche(new Lanche("duplo X-burger", 20.0, "Pão francês, queijo mussarela e dois hambúrgeres de 200g"));
		cardapio.insereNovoLanche(new Lanche("Hot Dog", 13.0, "Pão especial, salsicha, molho"));
		
		cardapio.insereNovoAcompanhamento(new Acompanhamento("Batatas rústicas", 12.0, "Porção de 200g"));
		cardapio.insereNovoAcompanhamento(new Acompanhamento("Onion rings", 18.0, "Porção de 200g"));
		cardapio.insereNovoAcompanhamento(new Acompanhamento("Mini pastéis", 20.0, "10 unidades"));

		System.out.println(cardapio);
		
	}

}
```