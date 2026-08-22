---

---
Os módulos de gerenciamento de transações local e global, junto com o gerenciador de controle de concorrência e recuperação de dados de um SGBDD garantem as propriedades **ACID**. É necessário um gerenciador de transação global, que geralmente utiliza-se dos protocolos *Two Phase Commit* e *Three Phase Commit**** (2PC e 3PC)*** para cumprir esta tarefa.