---

---
# Exceções

**Pilha de execução: **Visível a partir da perspectiva** Debug **no eclipse;

**NullPointerException**: Objeto não inicializado

**ArithmeticException:** Por exemplo, divisão por zero

```java
try {
	// Bloco de código que pode gerar exceção
} catch(ArithmeticException | NullPointerException e) {  // Java permite múltiplo catch
	// Tratamento da exceção
}
```

![[SubPages/Pessoal/images/Untitled 116.png]]

Classes que herdam diretamente de **Exception** são do tipo **checked** (verificadas pelo compilador) e necessitam que seja declarado na assinatura do método o tipo de exceção que ele “joga”, ou a mesma deve ser tratada com **try/catch**:

```java
private static void metodo2() throws MinhaExcecao {
    System.out.println("Ini do metodo2");
    throw new MinhaExcecao("deu muito errado");

    //System.out.println("Fim do metodo2");
}
```

Classes que herdam através de **RuntimeException **são do tipo **unchecked** e não necessitam que seja declarado na assinatura do método o tipo de exceção que ele joga. Caso não haja tratamento, estas exceções unchecked vão para o **stack trace**.

> [!tip] 💡
> ***try-with-resources*****:**
Desde a versão 1.7, o java permite o try com criação do objeto e fechamento automatico, sem a necessidade de explicitar no finally (**finally implícito**)

A exception deve implementar a interface **AutoCloseable**

```java
try (Conexao conexao = new Conexao()) {
				conexao.leDados();
    } catch(exception ex){
				System.out.println("Deu erro");
}
```
