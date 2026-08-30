# Primeiros passos em PowerBI | PowerBI Analyst

## Atividade do módulo 04 do curso "Primeiros passos em PowerBI" e "PowerBI Analyst" pela Universia em parceria com a DIO

### Desafio prático de Limpeza e Transformação de dados

- ELT (Extract, Load, Transform)
- Importação de um *data set* do PostgreSQL para PowerBI.
- Transformação de dados com **Power Query**.

---

**Importando a base de dados do PostgreSQL para o PowerBI.**

![Conectando ao PostgreSQL](/img/db_import_01.png "Conectando ao PostgreSQL")

![Tabelas](/img/db_import_02.png "Selecionando as Tabelas")

![Modelo no PowerBI](/img/db_import_02.png "Modelo no PowerBI")

---
	
#### Transformações aplicadas no Power Query:

1. Remoção de colunas nas tabelas (Colunas de junção usadas no PostgreSQL).
2. Renomeando colunas na tabela "employee". *fname* foi renomeado para *name* e *lname* foi renomeado para *surname*.
3. Substituição do tipo de dados da coluna *salary* na tabela "employee" de Decimal para Decimal fixo.
4. Substituição de valores da coluna *super_ssn* na tabela "employee". Substituindo Null por N/A. (Um empregado que também é gerente mas não é gerenciado por ninguém).
5. Divisão da coluna *address* na tabela *employee* que continha dados multivalorados. A coluna foi dividida em quatro: *adress_num, location, city* e *state*.
6. Mescla das colunas *name, minit* e *surname* da tabela "employee" para uma coluna chamada *full_name*.
7. Mescla de consulta das tabelas "employee" e "departament", gerando a nova tabela "emp_departament" para incluir o departamento de cada funcionário.
8. Mescla de consulta das tabelas "departament" e "dept_locations" na mesma tabela "dept_locations". Agora todos os locais dos departamentos podem ser consultados.
9. Mescla de consulta das tabelas "employee" e "works_on" para uma nova tabela chamada *hours_project*. Após agrupar , foi definido a quantidade de horas dos projetos.
10. Para associar os nomes dos Funcionários e seus respectivos Gerentes em uma nova tabela de nome "emp_manager", foi utilizada a seguinte *query*:
	
	![Identificando os Gerentes](/img/emp_mng_query.png "Identificando os gerentes dos funcionários")
	
	- E importado como instrução SQL
	
	![Importando para PowerBI como instrução SQL](/img/emp_mng_imp.png "Instrução SQL")
	
	![Tabela importada pronta no PowerBI](/img/emp_mng_pbi.png "Importação da instrução como tabela no POwerBI")
	
11. Remoção de uma linha da tabela "emp_manager" (O super-gerente que tem o valor Null na coluna *manager_name*, o mesmo do item 4)
	- Esta ação já poderia ter sido executada na importação de instrução da tabela com o comando LIMIT do SQL, mas deixei para experimentar a versatilidade do *Power Query*.
12. Uma série de mesclas de consulta e agrupamentos para formar a tabela "hours_employee", que define a quantidade de horas de cada funcionário nos projetos.
	
---

![Aplicando as Visualizações com os dados limpos](/img/company_report.png "Visualizações")
