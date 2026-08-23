---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-12T07:48:00
Owner:
  - Eduardo Quinalha
---
# Características

- Alguns frameworks possuem database migration (schema migration) embutidos como Django e Rails
- Existem bibliotecas standalone
	- Flyway
	- Liquibase
- A ideia é mapear cada alteração granular do schema de uma base de dados em um arquivo de script que possa ser versionado
- Os scripts de versionamento são gerados automaticamente

# Liquibase

- Pode produzir versionamentos em múltiplos formatos, como XML e JSON

# Flyway

# Riscos

- As seguintes práticas devem ser evitadas
	- Mudança de ferramenta (ou framework) de database migration
	- Mudança de banco de dados (MySQL, PostgreSQL, etc…)
	- Exclusão de colunas
	- Renomear colunas
	- Alterar tipo de dado de colunas que já contenha dados