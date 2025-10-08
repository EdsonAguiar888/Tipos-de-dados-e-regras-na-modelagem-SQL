
Artigo referente aos tipos de dados e modelagem SQL




# Tipos de Dados e Regras na Modelagem SQL

Os tipos de dados de uma coluna definem quais valores ela pode conter, como:

- Inteiro
- Caractere
- Dinheiro
- Data e Hora
- Binário

Um desenvolvedor deve decidir quais tipos de dados serão armazenados em cada coluna ao criar uma tabela.  
Os 3 tipos principais são:

- String
- Numérico
- Data e Hora

---

## Tipos de Dados de String

| Tipo de Dados       | Descrição |
|---------------------|-----------|
| **CHAR(tamanho)** | String de comprimento fixo (0 a 255). Padrão: 1. |
| **VARCHAR(tamanho)** | String de comprimento variável (0 a 65.535). |
| **BINARY(tamanho)** | Igual a CHAR(), mas armazena bytes binários. |
| **VARBINARY(tamanho)** | Igual a VARCHAR(), mas armazena bytes binários. |
| **TINYBLOB** | Para BLOBs pequenos, até 255 bytes. |
| **TINYTEXT** | String até 255 caracteres. |
| **TEXT(tamanho)** | String até 65.535 bytes. |
| **BLOB(tamanho)** | BLOB até 65.535 bytes. |
| **MEDIUMTEXT** | String até 16.777.215 caracteres. |
| **MEDIUMBLOB** | BLOB até 16.777.215 bytes. |
| **LONGTEXT** | String até 4.294.967.295 caracteres. |
| **LONGBLOB** | BLOB até 4.294.967.295 bytes. |
| **ENUM(val1, ...)** | String com valor único de uma lista (até 65.535 valores). |
| **SET(val1, ...)** | String com zero ou mais valores de uma lista (até 64 valores). |

---

## Tipos de Dados Numéricos

| Tipo de Dados       | Descrição |
|---------------------|-----------|
| **BIT(tamanho)** | Valores em bits (1 a 64). |
| **TINYINT(tamanho)** | Inteiro pequeno. Com sinal: -128 a 127. Sem sinal: 0 a 255. |
| **BOOL / BOOLEAN** | 0 = falso, !=0 = verdadeiro. |
| **SMALLINT(tamanho)** | Inteiro pequeno. Com sinal: -32.768 a 32.767. Sem sinal: 0 a 65.535. |
| **MEDIUMINT(tamanho)** | Inteiro médio. Com sinal: -8.388.608 a 8.388.607. |
| **INT / INTEGER(tamanho)** | Inteiro padrão. Com sinal: -2.147.483.648 a 2.147.483.647. |
| **BIGINT(tamanho)** | Inteiro grande. Com sinal: -9.22e18 a 9.22e18. |
| **FLOAT(tamanho, d)** | Ponto flutuante (obsoleto no MySQL 8+). |
| **FLOAT(p)** | FLOAT() se p de 0–24, DOUBLE() se 25–53. |
| **DOUBLE(tamanho, d)** | Número de ponto flutuante normal. |
| **DECIMAL(tamanho, d)** | Número de ponto fixo exato (até 65 dígitos, 30 casas decimais). |
| **DEC(tamanho, d)** | Igual a DECIMAL. |

---

## Tipos de Dados de Data e Hora

| Tipo de Dados       | Descrição |
|---------------------|-----------|
| **DATE** | Data no formato YYYY-MM-DD (1000-01-01 a 9999-12-31). |
| **DATETIME(fsp)** | Data e hora (YYYY-MM-DD hh:mm:ss). Suporta valores padrão e auto-atualização. |
| **TIMESTAMP(fsp)** | Carimbo de data/hora desde 1970-01-01 UTC até 2038. |
| **TIME(fsp)** | Intervalo de tempo (hh:mm:ss), de -838:59:59 a 838:59:59. |
| **YEAR** | Ano de 1901 a 2155 ou 0000. |

---

## Outros Tipos de Dados

| Tipo de Dados       | Descrição |
|---------------------|-----------|
| **sql_variant** | Armazena até 8.000 bytes de vários tipos. |
| **uniqueidentifier** | Identificador global exclusivo (GUID). |
| **xml** | Dados XML (até 2 GB). |
| **cursor** | Referência a cursor de banco de dados. |
| **table** | Conjunto de resultados para processamento posterior. |



# Regras na Modelagem SQL

Este artigo tem como objetivo trazer boas práticas no processo de modelagem de dados. 
Construir bancos de dados eficientes e que apresentem uma excelente consistência 
dos dados é fundamental para garantir o bom funcionamento das aplicações que 
utilizam bancos de dados.

O processo de modelagem de dados realizado de forma adequada e normalizada 
proporciona que a criação do banco de dados já comece bem e diminui o risco de 
problemas de inconsistências.

## Nome da Entidade
- Deve ser escrito no singular e em maiúsculo;  
- O nome deve ser o mais descritível possível e deve identificar a utilidade e aplicação da entidade;  
- Não se deve utilizar acentos e nem o cedilha;  
- Deve ter no máximo 30 caracteres por conta de limitações de alguns bancos de dados (Oracle e Firebird).  

## PK — Chave Primária
- Usar chave primária sempre com um campo;  
- Não utilizar chaves compostas;  
- A chave primária deve sempre ser o primeiro campo da tabela;  
- A chave deve sempre ser referenciada como “ID”;  
- Deve ser autoincremento.  

## Índices
- O índice da chave primária deve ser nomeado apenas como PRIMARY;  
- Os índices que serão criados na própria tabela para otimização de consultas devem seguir o padrão `IX_NOME_TABELAn`, onde o “n” é um número que vai sendo incrementado de acordo com a quantidade de índices.  

## Chaves Estrangeiras
- O nome do campo deve ser igual à chave primária da tabela de origem concatenado com o nome da tabela.  
- Exemplo: a tabela `PAGAMENTO` deverá ter um relacionamento com a tabela `AUTOR`. O campo que será utilizado na tabela `LIVRO` será `ID_AUTOR`.  
- O nome do índice será `FK_LIVRO_AUTOR`.  
- Caso o nome fique muito grande e não seja possível a criação por parte do banco de dados, é permitido fazer a abreviação.  

## Tipos de Dados
- Deve-se respeitar o tipo de dado para o campo definido.  
- Serão escolhidos os tipos que sejam comuns a todos os bancos de dados.  

## Sequence e Generator
- Para os bancos que necessitam da criação de uma Sequence ou Generator a parte da tabela, deve-se seguir o seguinte padrão: `SEQ_NOME_TABELA`.  

## Views
- Deve-se criar a view com um prefixo para que ela seja identificada como tal.  
- Exemplo: `VIEW_CONTROLE_ACESSO`.  

## Procedures, Functions, Triggers
- Não serão utilizados, a princípio.  
- Caso haja a necessidade de criação, deve-se utilizar um prefixo para identificação:  
  - Procedure — `SP_`  
  - Function — `FUNCTION_`  
  - Trigger — `TRIGGER_`  

## Comentários
- Deve-se ter como hábito fazer os devidos comentários para as tabelas e os campos na ferramenta utilizada para a modelagem do DER.  
- Dessa forma as tabelas e campos ficam bem documentados.  

## Referências
- [Medium - Modelagem de Bancos de Dados](https://medium.com/@alberteije/modelagem-de-bancos-de-dados-sem-segredos-parte-04-cbb40a1db4a7)  
- [DevMedia - Modelagem de Dados](https://www.devmedia.com.br/modelagem-de-dados-tutorial/20398)  
- [PM3 - Modelagem de Dados](https://pm3.com.br/blog/modelagem-de-dados/)  
- [IBM - Data Modeling](https://www.ibm.com/br-pt/think/topics/data-modeling)  
- [W3Schools - SQL Data Types](https://www.w3schools.com/sql/sql_datatypes.asp)  
"""

# Gerar arquivo markdown
output_file = "/mnt/data/regras_modelagem_sql.md"
pypandoc.convert_text(artigo_texto, 'md', format='md', outputfile=output_file, extra_args=['--standalone'])

output_file
