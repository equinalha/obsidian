---

---
- Padrão para testes automatizados em Java
- Gratuito e open source
- Testes unitários

```java
import org.junit.Assert;
import org.junit.jupiter.api.Test;

public class CalculadoraTest {
	
	@Test
	public void deveriaSomar() {
		Calculadora calc = new Calculadora();
		int soma = calc.somar(3, 7);
		
		Assert.assertEquals(10, soma);
	}
}
```

```java
class BonusServiceTest {

	@Test
	void bonusDeveriaSerZeroParaFuncionarioComSalarioMuitoAlto() {
		BonusService service = new BonusService();

		// Forma 1
//		assertThrows(IllegalArgumentException.class,
//				() -> service.calcularBonus(new Funcionario("Rodrigo", LocalDate.now(), new BigDecimal("25000"))));

		// Forma 2
		try {
			service.calcularBonus(new Funcionario("Rodrigo", LocalDate.now(), new BigDecimal("25000")));
			fail("Não ocorreu a exception esperada");
		} catch (Exception e) {

		}

	}

	@Test
	void bonusDeveriaSerDezPorcento() {
		BonusService service = new BonusService();
		BigDecimal bonus = service.calcularBonus(new Funcionario("Rodrigo", LocalDate.now(), new BigDecimal("2500")));

		assertEquals(new BigDecimal("250.00"), bonus);

	}

	@Test
	void bonusDeveriaSerMil() {
		BonusService service = new BonusService();
		BigDecimal bonus = service.calcularBonus(new Funcionario("Rodrigo", LocalDate.now(), new BigDecimal("10000")));

		assertEquals(new BigDecimal("1000.00"), bonus);

	}

}
```

```java
public class ReajusteServiceTest {

	private ReajusteService service;
	private Funcionario funcionario;

	@BeforeEach
	public void inicializar() {
		this.service = new ReajusteService();
		this.funcionario = new Funcionario("Joao", LocalDate.now(), new BigDecimal("1000.00"));
	}

	@AfterEach
	public void finalizar() {
		System.out.println("Fim");
	}
	
	@BeforeAll
	public static void antesDeTodos() {
		System.out.println("Início dos testes");
	}
	
	@AfterAll
	public static void depoisDeTodos() {
		System.out.println("Depois de todos");
	}
	
	@Test
	public void reajusteDeveriaSerTresPorcentoParaDesempenhoInsuficiente() {

		service.concederReajuste(funcionario, Desempenho.INSUFICIENTE);

		assertEquals(new BigDecimal("1030.00"), funcionario.getSalario());
	}

	@Test
	public void reajusteDeveriaSerQuinzePorcentoParaDesempenhoBom() {

		service.concederReajuste(funcionario, Desempenho.BOM);

		assertEquals(new BigDecimal("1150.00"), funcionario.getSalario());
	}

	@Test
	public void reajusteDeveriaSerVintePorcentoParaDesempenhoOtimo() {

		service.concederReajuste(funcionario, Desempenho.OTIMO);

		assertEquals(new BigDecimal("1200.00"), funcionario.getSalario());
	}
}
```