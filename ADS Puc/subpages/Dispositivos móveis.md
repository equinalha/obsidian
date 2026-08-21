---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2024-07-13T07:58:00
Status: Not started
Description: ""
---
SQLite

Toast → SetOnClickListener

Intent

[CONSULPLAN - 2018 - Câmara de Belo Horizonte – MG – Adaptada] Classe do Android que pode ser utilizada para enviar uma mensagem para o sistema operacional, solicitar ao sistema operacional que ligue para determinado número de celular etc.

Assinale a alternativa que apresenta a classe descrita.

A)
Service

B) - correta
Intent

C)
Content

D)
Receiver

Para executar uma consulta na tabela pessoa de um banco de dados interno do Android, foi utilizada a seguinte linha de execução:

c = db.rawQuery("SELECT * FROM pessoa", null);

Considerando esse contexto, nesta instrução, os objetos c e db são, respectivamente, dos tipos:

A)
int e SQLiteDatabase.

B)
ResultSet e SQLDatabase.

C)
RecordSet e Statement.

D) - correta
Cursor e SQLiteDatabase.

E)
ResultSet e Statement.

```java
// Para utilizar o SQLite, é necessário primeiramente extender a classe SQLiteOpenHelper:

public class MinhaDB extends SQLiteOpenHelper { ...

// Então sobrescrever o método onCreate, lançando os comandos para criação dos objetos do banco

@Override
    public void onCreate(SQLiteDatabase db) {
        String query = "CREATE TABLE IF NOT EXISTS "+DB_TABLE+" (" +
                COL_ID+" INTEGER PRIMARY KEY AUTOINCREMENT, " +
                COL_DATA+" TEXT, " +
                COL_DESCRICAO+ " TEXT, " +
                COL_QUILOMETRAGEM+" INTEGER, "+
                COL_VALOR+" NUMERIC)";
        Log.d("Query: ",query);
        db.execSQL(query);
    }

// Por fim, criar os métodos de manipulação dos dados

    public long insereRevisao(Revisao r) {
        SQLiteDatabase database = getWritableDatabase();
        ContentValues values = new ContentValues();

        values.put(COL_DATA, formattedDate);
        values.put(COL_DESCRICAO, r.getDescricao());
        values.put(COL_QUILOMETRAGEM, r.getQuilometragem());
        values.put(COL_VALOR, r.getValor());

        long id = -1;
        try{
            id = database.insertOrThrow(DB_TABLE, null, values);
            Log.d("Inseriu!", "Id: "+ String.valueOf(id));
        }catch (Exception e){
            Log.d("Erro: ",e.getMessage());
        }
        database.close();
        return id;
    }

// Métodos de consulta

// Resumindo:

Criar banco:
	- Sobrescrever onCreate()
	- db.execSQL(String query) // Objeto SQLiteDatabase (SQLiteDatabase database = getWritableDatabase();)

Inserir dados:
	- ContentValues values = new ContentValues();
	- values.put(COL_DESCRICAO, r.getDescricao());
	- id = database.insertOrThrow(DB_TABLE, null, values); // Retorna um long

Ler dados:
	- Cursor cursor = database.query(DB_TABLE,columns,selection,selectionArgs,groupBy,having,orderBy);

Atualizar:
	- int count = database.update(DB_TABLE,values,COL_ID + "=?",new String[]{id});

Buscar usando rawQuery:

ArrayList<Pessoa> listaPessoas = new ArrayList<>();
Cursor c = db.rawQuery("SELECT * FROM pessoa", null);

if (c != null) {
    if (c.moveToFirst()) {
        do {
            int id = c.getInt(c.getColumnIndex("id"));
            String nome = c.getString(c.getColumnIndex("nome"));
            int idade = c.getInt(c.getColumnIndex("idade"));

            Pessoa pessoa = new Pessoa(id, nome, idade);
            listaPessoas.add(pessoa);
        } while (c.moveToNext());
    }
    c.close();
}

```

Os aplicativos Android são desenvolvidos usando as diretrizes do material design. Essas diretrizes abordam tudo o que você precisa saber sobre como desenvolver seu aplicativo, desde o fluxo da experiência do usuário até o design visual, o movimento, as fontes e muito mais.

Sobre o Android, está correto afirmar que uma activity:

I. Realiza operações na tela, representando a interface gráfica com o usuário.

II. Define em sua estrutura XML informações essenciais da aplicação, como acesso ao banco de dados.

III. Executa funcionalidades em background sem interação com a interface do usuário.

Está correto o que se afirma apenas em:

A) - correta
I.

B)
II e III.

C)
III.

D)
I e II.

E)
I e III.

A classe AsyncTask foi criada com o objetivo de facilitar as execuções de chamada de rede em background, encapsulando todo o processo de criação de threads e handler. Esta classe possui quatro métodos para a sua execução, nos quais os quatro métodos não necessariamente são obrigatórios.

Considerando esse contexto, identifique os nomes dos quatro métodos.

Está correto o que se afirma em:

A)
onPreExecute, onProgressUpdate, onReturnExecute e doInBackground.

B)
onPreExecute, onProgressUpdate, onReturnExecute e doOnBackground.

C) - correta
onPreExecute, onProgressUpdate, onPostExecute e doInBackground.

D)
inPreExecute, onProgressUpdate, onPostExecute e doOnBackground.

E)
inPreExecute, onProgressUpdate, onReturnExecute e doInBackground.


No Android, pode-se criar um banco de dados interno em qualquer aplicação. Porém, existem algumas regras e limitações para este banco de dados.

Considerando esse contexto, analise as afirmativas a seguir:

I. Não há como criar um banco de dados interno em MySQL para o Android.

II. A sintaxe do SQLite e MySQL são exatamente as mesmas, pois as duas utilizam a linguagem SQL.

III. Como utilizamos Java para o desenvolvimento de aplicativos Android, é necessário importar um conector para realizar a conexão com banco de dados.

Está correto o que se afirma em:

A) - correta
I, apenas.

B)
III, apenas.

C)
I e II, apenas.

D)
II e III, apenas.

E)
II, apenas.

O SQLite dá todo o poder da linguagem de consulta SQL aos aplicativos Android.

Considere seus conhecimentos sobre essa tecnologia e analise as afirmativas a seguir.

I - Para utilizar o SQLite, precisamos de um serviço de banco de dados que rode no próprio dispositivo.
II - Para a criação de uma tabela de nome Aluno no SQLite, utilizamos o comando new database Aluno;
III - Para selecionar e filtrar registros do banco de dados, utilizamos o comando SQL select junto do where.
Assinale a alternativa que apresenta apenas a(s) afirmativa(s) correta(s).

A)
I.

B)
II.

C) - correra
III.

D)
II e III.

Para um app Android interagir com o usuário, ele precisa de diversos recursos.

A partir de seus conhecimentos em Android, analise as afirmativas a seguir.

I - Uma activity deve sempre ter um ou mais fragments, de forma a compor a interface a ser mostrada ao usuário.
II - Um fragment possui um ciclo de vida próprio, que é igual ao da activity.
III - O Android possui uma ferramenta chamada ADB para se comunicar com um emulador/dispositivo.


Assinale a alternativa que apresenta apenas a(s) afirmativa(s) correta(s).

A)
I.

B) -correta
III.

C)
II e III.

D)
II.

Sobre a estrutura de arquivos Android, considere as afirmativas a seguir.

I - Na pasta res/values, ficam os arquivos de configuração de textos e estilos, dentre outros.
II - A pasta res/images contém os arquivos de imagens da aplicação.
III - Na pasta res/layout, ficam os arquivos de layout que estão no formato JSON.
Assinale a alternativa que apresenta apenas a(s) afirmativa(s) correta(s).

A)
II.

B) -correta
I.

C)
III.

D)
I e III.

Muitos apps precisam exibir coleções de itens. O listView exibe uma coleção de exibições com rolagem vertical, sendo cada exibição posicionada imediatamente abaixo da exibição anterior na lista. Para uma abordagem mais moderna, flexível e de alto desempenho para exibir listas, usamos o recyclerView.

A partir dos seus conhecimentos em Android e como funciona a construção de listas nos apps, avalie as afirmativas.

I - O recyclerView permite o scrolling tanto horizontal quanto vertical.
II - Para mudar o conteúdo de um item do listView, é necessário recriar todos os itens.
III - O recyclerView possui um método para reconhecer slides e deletar o item de forma automática.
Assinale a alternativa que apresenta apenas a(s) afirmativa(s) correta(s).

A)
I e II.

B)
II e III.

C)
I, II e III.

D) - correta
I.

Pra mim caiu sobre sqllite, listview, reclycerView, orientação ao objeto, estrutura das pastas de Android o que vai em cada, e tiveram umas 3 que não fazia ideia, uma delas era a sintaxe do Toast.maketest