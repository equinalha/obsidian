---

---
# java.io

- **Stream: **Input stream of bytes
- **Reader: **reading character streams

![[SubPages/Pessoal/images/Untitled 120.png]]

```java
public class TesteLeitura {

	public static void main(String[] args) throws IOException {
		
		// Fluxo de Entrada com Arquivo
		FileInputStream fis = new FileInputStream("lorem.txt"); // O método read de FileInputStram devolve bytes
		InputStreamReader isr = new InputStreamReader(fis); // Converte o inputStream de bytes para char[]
		BufferedReader br = new BufferedReader(isr); // Converte a cadeia de caractéres em String 
	
		String linha = br.readLine();
		
		while(linha != null) {
			
			System.out.println(linha);
			linha = br.readLine();
			
		}
			
		br.close();
		
	}

}
```

Usando as referências mais genéricas (polimorfismo)

```java
public class TesteLeitura {

	public static void main(String[] args) throws IOException {
		
		// Fluxo de Entrada com Arquivo
		InputStream fis = new FileInputStream("lorem.txt"); // O método read de FileInputStram devolve bytes
		Reader isr = new InputStreamReader(fis); // Converte o inputStream de bytes para char[]
		BufferedReader br = new BufferedReader(isr); // Converte a cadeia de caractéres em String 
	
		String linha = br.readLine();
		
		while(linha != null) {
			
			System.out.println(linha);
			linha = br.readLine();
			
		}
			
		br.close();
		
	}

}
```

```java
public class TesteEscrita {

	public static void main(String[] args) throws IOException {
		
		// Fluxo de Entrada com Arquivo
		OutputStream fos = new FileOutputStream("lorem2.txt"); // O método read de FileInputStram devolve bytes
		Writer osw = new OutputStreamWriter(fos); // Converte o inputStream de bytes para char[]
		BufferedWriter bw = new BufferedWriter(osw); // Converte a cadeia de caractéres em String 
	
		bw.write("Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod");
		bw.newLine();
		bw.newLine();
		bw.write("Teste teste teste");
			
		bw.close();
		
	}

}
```

## Uso de properties

```java
//import deve ser java.util.Properties
Properties props = new Properties(); 
props.setProperty("login", "alura"); //chave, valor
props.setProperty("senha", "alurapass");
props.setProperty("endereco", "www.alura.com.br");
```

```java
props.store(new FileWriter("conf.properties"), "algum comentário");
```

```java
#algum comentário
#Thu May 10 14:29:38 BRT 2018
senha=alurapass
login=alura
endereco=www.alura.com.br
```

```java
Properties props = new Properties();        
props.load(new FileReader("conf.properties"));

String login = props.getProperty("login");
String senha = props.getProperty("senha");
String endereco = props.getProperty("endereco");

System.out.println(login + ", " + senha  + ", " +  endereco);
```