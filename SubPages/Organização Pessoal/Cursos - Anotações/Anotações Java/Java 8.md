---

---
# Métodos *default*

No java 8 surgiram os métodos default. Até então, interfaces só podiam ter métodos abstratos, que deveriam ser obrigatoriamente implementados pelas classes que a implementa.

Com os métodos default, é possível existir métodos com corpo dentro de uma interface. Com isso é possível adicionar funcionalidades nas interfaces, sem quebrar o código legado.

Métodos default também podem ser estáticos

# Classes anônimas

É possível dar um ***new *** em uma interface, apenas se os métodos fores sobrescritos no momento da instanciação.

Na prática, é como se fosse criada uma classe que implementasse a interface. Esta classe é chamada de classe anônima.

```java
Consumer<String> consumidor = new Consumer<String>(){
	@Override
	public void accept(String s) {
		System.out.printls(s);
	}
}
```

# Lambdas

```java
palavras.forEach((String s) -> {
	System.out.println(s);
});

// De forma mais enxuta
palavras.forEach (s -> System.out.println(s));

// Outro exemplo
palavras.sort(Comparator.comparing(String::lenght));
```

# Trabalhando com stream()

```java
public class ExemploCursos {
	public static void main(String[] args) {
		List<Curso> cursos = new ArrayList<Curso>();
		
		cursos.add(new Curso("Python", 45));
		cursos.add(new Curso("JavaScript", 150));
		cursos.add(new Curso("Java 8", 113));
		cursos.add(new Curso("C", 55));
		
		cursos.sort(Comparator.comparing(Curso::getAlunos));
		cursos.forEach(c -> System.out.println(c.getNome()));
		
		// Stream gera um fluxo de objetos
		// filter retornará somente os objetos cujo lâmbda retornar true
		cursos.stream().filter(c -> c.getAlunos() >= 100).forEach(c -> System.out.println(c.getNome()));
		
		// Detalhe, a saída de um Stream não é compatível com collections!!!
		cursos.stream()
			.filter(c -> c.getAlunos() >= 100)
			.map(Curso::getAlunos) //Usando Method Reference
			.forEach(System.out::println);

		// Convertendo um stream de objeto para um stream de String
		Stream<String> nomes = cursos.stream().map(Curso::getNome);

		// Para voltar de um Stream para uma Collection, é necessário utilizar um Collector
		List<Curso> cursosOrdenados = cursos.stream()
											.filter(c -> c.getAlunos() > 100)
											.collect(Collectors.toList());

		// É possível trabalhar com paralellStream e tirar proveito do paralelismo de multiplos processadores
		// Só vale a pena mesmo em listas muito grandes, senão o overhead do parallelStream() pode até deixar o código mais lento
		cursos.parallelStream()
			.filter(c -> c.getAlunos() >= 100)
			.map(Curso::getAlunos)
			.forEach(System.out::println);
	}
}
```

# Classe Optional()

```java
// Usando Optional. Optional é uma classe que envolve um elemento de um stream
		Optional<Curso> optCurso = cursos.stream()
			.filter(c -> c.getAlunos() > 100)
			.findAny();
		
		Curso curso = optCurso.get();
		System.out.println(curso.getNome());
		
		// Usando tudo na mesma linha de comando
		cursos.stream()
			.filter(c -> c.getAlunos() > 100)
			.findAny()
			.ifPresent(c -> System.out.println(c.getNome()));
```

```java
// Outro Exemplo
public void removeEmpresa(int empresaId) {
		
		Optional<Empresa> empresaOptional = empresas.stream().filter( e -> e.getId().equals(empresaId)).findFirst();
		if(empresaOptional.isPresent()) {
			empresas.remove(empresaOptional.get());
		}
	}
```

# Trabalhando com Datas

```java
// Classe LocalDate -> Apenas datas
		LocalDate hoje = LocalDate.now();
		System.out.println(hoje);
		
		LocalDate olimpiadas = LocalDate.of(2022, Month.DECEMBER, 31);
		
		int anos = olimpiadas.getYear() - hoje.getYear();
		System.out.println(anos);
		
		Period periodo = Period.between(hoje, olimpiadas);
		System.out.println(periodo);
		System.out.println(periodo.getDays());
		
		LocalDate proximasOlimpiadas = olimpiadas.plusYears(4);
		DateTimeFormatter formatador = DateTimeFormatter.ofPattern("dd/MM/yyyy");
		
		String valorFormatado = proximasOlimpiadas.format(formatador);
		System.out.println(valorFormatado);
		
		// Classe LocalDateTime -> Data, hora, minutos e segundos
		LocalDateTime agora = LocalDateTime.now();
		
		DateTimeFormatter formatadorComHoras = DateTimeFormatter.ofPattern("dd/MM/yyyy hh:mm:ss");
		System.out.println(agora.format(formatadorComHoras));
		
		// Data e hora com zona		
		ZonedDateTime horaBrasil = ZonedDateTime.now();
		System.out.println(horaBrasil.format(formatadorComHoras));
```
