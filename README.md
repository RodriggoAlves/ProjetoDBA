# Documentação do Banco de Dados de Óbitos

## Tabelas do Banco de Dados

O banco de dados foi projetado para armazenar informações sobre óbitos e seus detalhes. Ele é composto por várias tabelas relacionadas. Abaixo estão as tabelas e seus respectivos dados:

### 1. Tabela `Sexo`

Armazena as opções de sexo para o paciente.

| ID  | Descrição   |
| --- | ----------- |
| 1   | Masculino   |
| 2   | Feminino    |

### 2. Tabela `Especialidades`

Armazena as especialidades médicas.

| ID  | Descrição              |
| --- | ---------------------- |
| 1   | Bucomaxilofacial       |
| 2   | Cardiologia            |
| 3   | Clínica Médica         |
| 4   | Clínico Geral          |
| 5   | Cirurgia Plástica      |
| 6   | Cirurgia Cardiovascular|
| 7   | Ortopedia              |

### 3. Tabela `Local`

Armazena os locais onde o óbito pode ocorrer.

| ID  | Descrição  |
| --- | ---------- |
| 1   | UTI-A      |
| 2   | UTI-B      |
| 3   | UTI-C      |
| 4   | UTI-D      |
| 5   | EMERGÊNCIA |

### 4. Tabela `TipoObito`

Armazena os tipos de óbito.

| ID  | Descrição |
| --- | --------- |
| 1   | DO        |
| 2   | IML       |
| 3   | SVO       |
| 4   | SAD       |

### 5. Tabela Principal `Obitos`

A tabela `Obitos` é a tabela principal onde são armazenados os dados dos óbitos, com referências às outras tabelas através de chaves estrangeiras.

| Coluna              | Tipo de Dado | Descrição |
| ------------------- | ------------ | --------- |
| id                  | SERIAL       | Identificador único do óbito |
| nome                | VARCHAR(100) | Nome do paciente |
| dt_nascimento       | DATE         | Data de nascimento do paciente |
| prontuario          | VARCHAR(50)  | Número de prontuário do paciente |
| sexo_id             | INTEGER      | ID referente ao sexo (tabela `Sexo`) |
| especialidade_id    | INTEGER      | ID referente à especialidade (tabela `Especialidades`) |
| local_id            | INTEGER      | ID referente ao local (tabela `Local`) |
| tipo_obito_id       | INTEGER      | ID referente ao tipo de óbito (tabela `TipoObito`) |
| dt_obito            | DATE         | Data do óbito |

#### Exemplo de Inserção de Dados:

```sql
INSERT INTO Obitos (
    nome, 
    dt_nascimento, 
    prontuario, 
    sexo_id, 
    especialidade_id, 
    local_id, 
    tipo_obito_id, 
    dt_obito
)
VALUES (
    'João Silva', 
    '1980-05-20', 
    'PRT123456', 
    1,  -- Sexo: Masculino (ID 1)
    2,  -- Especialidade: Cardiologia (ID 2)
    1,  -- Local: UTI-A (ID 1)
    1,  -- Tipo de Óbito: DO (ID 1)
    '2024-11-21'
);
```

#### Exemplo de Update de Dados:

```sql
UPDATE Obitos
SET 
    nome = 'João Da Silva', 
    dt_nascimento = '1980-05-20', 
    prontuario = 'PRT123456', 
    sexo_id = 1,  -- Sexo: Masculino (ID 1)
    especialidade_id = 2,  -- Especialidade: Cardiologia (ID 2)
    local_id = 1,  -- Local: UTI-A (ID 1)
    tipo_obito_id = 1,  -- Tipo de Óbito: DO (ID 1)
    dt_obito = '2024-11-21'
WHERE id = 320;

