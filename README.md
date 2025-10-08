
Artigo referente aos tipos de dados e modelagem SQL

### Faculdade Senac - ADS


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
