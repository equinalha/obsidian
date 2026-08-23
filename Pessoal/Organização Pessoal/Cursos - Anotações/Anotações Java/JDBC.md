---

---
```java
// Usando Prepared Statement

String nome = "Mouse";
		String descricao = "Mouse sem fio";
		
		ConnectionFactory cf = new ConnectionFactory();
		Connection connection = cf.recuperarConexao();

		PreparedStatement stm = connection.prepareStatement("INSERT INTO produto (nome, descricao) VALUES (?, ?)", Statement.RETURN_GENERATED_KEYS);
		
		stm.setString(1, nome);
		stm.setString(2, descricao);
		
		stm.execute();

		ResultSet rst = stm.getGeneratedKeys();

		while (rst.next()) {
			Integer id = rst.getInt(1);
			System.out.println("O id criado foi: " + id);
		}
```

> [!tip] 💡
> Por padrão, objetos da interface ***Connection()*** já vem com o Auto Commit habilitado. Desta forma, a medida que os *statements* vão sendo executados, eles são ***commitados*** no banco.
Isto pode ser uma desvantagem quando ocorrem exceções durante a execução do código, sendo que desta forma pode resultar em dados inconsistentes no banco. Sendo assim, é possível desabilitar o ***auto commit ***e executar um ***commit ***manual no final da execução.

```java
ConnectionFactory cf = new ConnectionFactory();
		Connection connection = cf.recuperarConexao();

		connection.setAutoCommit(false);

		try (PreparedStatement stm = connection.prepareStatement("INSERT INTO produto (nome, descricao) VALUES (?, ?)",
				Statement.RETURN_GENERATED_KEYS)) {

			adicionarVariavel("Mouse", "Mouse sem fio", stm);
			adicionarVariavel("SmarTV", "45 polegadas", stm);

			connection.commit();

		} catch (Exception e) {
			e.printStackTrace();
			connection.rollback();
			System.out.println("Rollback executado");
		}
```

# Pool de Conexões e Data Sources

> [!tip] 💡
> Quando utilizamos diretamente o JDBC para obter a conexão com o banco de dados, duas coisas podem acontecer:
1- Cada chamada gera uma nova conexão com o banco;
2- Os statements são enfileirados para serem executados um de cada vez;

Em aplicações de grande porte, ambas as situações podem ser um problema. Para isso, utilizamos ***pool de conexões*** em conjunto com ***Data Sources***.

> [!tip] 💡
> Uma solução comum para o uso de pool de conexões em java para bancos MySQL é a biblioteca **c3p0**

```java
// Connection Factory Utilizando Pool de Conexões e Data Source

public class ConnectionFactory {

	public DataSource ds;

	public ConnectionFactory() {
		ComboPooledDataSource comboPooledDS = new ComboPooledDataSource();
		comboPooledDS.setJdbcUrl("jdbc:mysql://localhost/loja_virtual?useTimezone=true&serverTimezone=UTC");
		comboPooledDS.setUser("root");
		comboPooledDS.setPassword("root");

		this.ds = comboPooledDS;
	}

	public Connection recuperarConexao() throws SQLException {
		return this.ds.getConnection();
	}
}
```

```java
// Teste de pool de conexões

public class TestaPoolConexoes {

	public static void main(String[] args) throws SQLException {
		ConnectionFactory cf = new ConnectionFactory();
		
		for (int i = 0; i < 20; i++) {
			cf.recuperarConexao();
			System.out.println("Conexao " + i);
		}
	}
}
```

# DAO

> [!tip] 💡
> DAO é onde se programa as operações (CRUD) da entidade relacionada. Exemplos:
ProdutoDAO:
- produto.listar()
- produto.buscar()
- produto.deletar()
- produto.alterar()
- produto.salvar()

```java
public class ProdutoDAO {
	private Connection conn;
	public ProdutoDAO(Connection connection) {
		this.conn = connection;
	}
	
	public void salvar(Produto produto) {
		String sql = "INSERT INTO produto (NOME, DESCRICAO) VALUES (?, ?)";
		
		try (PreparedStatement stm = conn.prepareStatement(sql, Statement.RETURN_GENERATED_KEYS)) {
			
			stm.setString(1, produto.getNome());
			stm.setString(2, produto.getDescricao());
			stm.execute();
			
			try(ResultSet rst = stm.getGeneratedKeys()) {
				while (rst.next()) {
					int id = rst.getInt(1);
					produto.setId(id);
					System.out.println(produto);
				}
			} catch (Exception e) {
				System.out.println(e.getMessage());
				e.printStackTrace();
			}
			
		} catch (Exception e) {
			System.out.println(e.getMessage());
			e.printStackTrace();
		}
	}
}
```

# Querys N+1

> [!tip] 💡
> Ocorrem quando se faz busca em duas tabelas relacionadas (chave estrangeira) sem o uso de *JOIN***. 
**Por exemplo:
Para cada categoria, buscar os produtos desta categoria:
A query ocorre uma vez para buscar todas as categorias e mais uma vez para cada item retornado → **N+1**
