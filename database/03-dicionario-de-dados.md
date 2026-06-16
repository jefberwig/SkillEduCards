# SkillEduCards

# 03 - Dicionário de Dados

Versão: 0.1.0-alpha

---

# Objetivo

Documentar todos os campos utilizados pelo banco de dados do SkillEduCards, padronizando nomenclaturas, descrições, tipos de dados e regras de negócio.

---

# Convenções

## Nome das tabelas

Sempre em minúsculo e no plural.

Exemplo:

* estudantes
* professores
* cartas
* eventos

---

## Nome dos campos

Sempre em snake_case.

Exemplo:

nome_heroico

xp_total

created_at

---

## Chaves Primárias

Todas as tabelas utilizam:

id (UUID)

---

## Datas

Todos os registros possuem:

created_at

updated_at

---

# Tabela: escolas

| Campo      | Tipo         | Obrigatório | Descrição           |
| ---------- | ------------ | ----------- | ------------------- |
| id         | UUID         | Sim         | Identificador único |
| nome       | VARCHAR(150) | Sim         | Nome da escola      |
| cidade     | VARCHAR(100) | Não         | Cidade              |
| estado     | VARCHAR(2)   | Não         | UF                  |
| created_at | TIMESTAMP    | Sim         | Data de criação     |
| updated_at | TIMESTAMP    | Sim         | Última atualização  |

---

# Tabela: temporadas

| Campo     | Tipo         | Obrigatório | Descrição         |
| --------- | ------------ | ----------- | ----------------- |
| id        | UUID         | Sim         | Identificador     |
| escola_id | UUID         | Sim         | Escola vinculada  |
| nome      | VARCHAR(100) | Sim         | Nome da temporada |
| ano       | INTEGER      | Sim         | Ano letivo        |
| ativa     | BOOLEAN      | Sim         | Temporada ativa   |

---

# Tabela: turmas

| Campo     | Tipo        | Obrigatório | Descrição     |
| --------- | ----------- | ----------- | ------------- |
| id        | UUID        | Sim         | Identificador |
| escola_id | UUID        | Sim         | Escola        |
| nome      | VARCHAR(50) | Sim         | Nome da turma |
| serie     | VARCHAR(20) | Sim         | Série         |
| turno     | VARCHAR(20) | Sim         | Turno         |

---

# Tabela: professores

| Campo     | Tipo         | Obrigatório | Descrição         |
| --------- | ------------ | ----------- | ----------------- |
| id        | UUID         | Sim         | Identificador     |
| escola_id | UUID         | Sim         | Escola            |
| nome      | VARCHAR(150) | Sim         | Nome interno      |
| email     | VARCHAR(150) | Sim         | Login             |
| perfil    | VARCHAR(50)  | Sim         | Perfil do usuário |

---

# Tabela: estudantes

| Campo          | Tipo         | Obrigatório | Descrição           |
| -------------- | ------------ | ----------- | ------------------- |
| id             | UUID         | Sim         | Identificador       |
| turma_id       | UUID         | Sim         | Turma               |
| codigo_publico | VARCHAR(30)  | Sim         | Código público      |
| nome_real      | VARCHAR(150) | Sim         | Uso interno         |
| nome_heroico   | VARCHAR(80)  | Sim         | Nome exibido        |
| avatar         | TEXT         | Não         | Avatar escolhido    |
| classe         | VARCHAR(50)  | Sim         | Classe do estudante |
| elemento       | VARCHAR(50)  | Sim         | Elemento narrativo  |
| ativo          | BOOLEAN      | Sim         | Situação            |

---

# Tabela: cartas

| Campo        | Tipo        | Obrigatório | Descrição        |
| ------------ | ----------- | ----------- | ---------------- |
| id           | UUID        | Sim         | Identificador    |
| estudante_id | UUID        | Sim         | Estudante        |
| temporada_id | UUID        | Sim         | Temporada        |
| nivel        | INTEGER     | Sim         | Nível atual      |
| xp_total     | INTEGER     | Sim         | XP acumulado     |
| titulo       | VARCHAR(80) | Sim         | Título evolutivo |

---

# Tabela: eventos

(Esta é a tabela principal do sistema.)

| Campo        | Tipo        | Obrigatório | Descrição             |
| ------------ | ----------- | ----------- | --------------------- |
| id           | UUID        | Sim         | Identificador         |
| estudante_id | UUID        | Sim         | Estudante             |
| professor_id | UUID        | Não         | Professor responsável |
| tipo_evento  | VARCHAR(80) | Sim         | Tipo do evento        |
| descricao    | TEXT        | Sim         | Descrição             |
| xp           | INTEGER     | Sim         | XP gerado             |
| data_evento  | TIMESTAMP   | Sim         | Data do evento        |

---

# Tabela: missoes

| Campo         | Tipo         | Obrigatório | Descrição     |
| ------------- | ------------ | ----------- | ------------- |
| id            | UUID         | Sim         | Identificador |
| temporada_id  | UUID         | Sim         | Temporada     |
| titulo        | VARCHAR(150) | Sim         | Nome          |
| descricao     | TEXT         | Sim         | Objetivo      |
| xp_recompensa | INTEGER      | Sim         | XP concedido  |

---

# Tabela: estudante_missoes

| Campo        | Tipo        | Obrigatório | Descrição          |
| ------------ | ----------- | ----------- | ------------------ |
| estudante_id | UUID        | Sim         | Estudante          |
| missao_id    | UUID        | Sim         | Missão             |
| status       | VARCHAR(20) | Sim         | Pendente/Concluída |
| concluida_em | TIMESTAMP   | Não         | Data conclusão     |

---

# Tabela: medalhas

| Campo     | Tipo         | Obrigatório | Descrição     |
| --------- | ------------ | ----------- | ------------- |
| id        | UUID         | Sim         | Identificador |
| nome      | VARCHAR(100) | Sim         | Nome          |
| descricao | TEXT         | Sim         | Explicação    |
| icone     | VARCHAR(100) | Não         | Ícone         |

---

# Tabela: estudante_medalhas

| Campo          | Tipo      | Obrigatório | Descrição      |
| -------------- | --------- | ----------- | -------------- |
| estudante_id   | UUID      | Sim         | Estudante      |
| medalha_id     | UUID      | Sim         | Medalha        |
| conquistada_em | TIMESTAMP | Sim         | Data conquista |

---

# Tabela: especialidades

| Campo     | Tipo         | Obrigatório | Descrição     |
| --------- | ------------ | ----------- | ------------- |
| id        | UUID         | Sim         | Identificador |
| nome      | VARCHAR(100) | Sim         | Especialidade |
| descricao | TEXT         | Sim         | Definição     |

---

# Tabela: estudante_especialidades

| Campo            | Tipo    | Obrigatório | Descrição               |
| ---------------- | ------- | ----------- | ----------------------- |
| estudante_id     | UUID    | Sim         | Estudante               |
| especialidade_id | UUID    | Sim         | Especialidade           |
| nivel            | INTEGER | Sim         | Grau de desenvolvimento |

---

# Regras Gerais

* Toda informação deve possuir significado pedagógico.
* Nenhum dado deve expor estudantes publicamente.
* O Nome Heroico será utilizado nas interfaces do sistema.
* O XP será sempre calculado a partir dos eventos registrados.
* Nenhum evento será excluído fisicamente do banco de dados.

---

# Política de Privacidade

O SkillEduCards adota o princípio da minimização de dados.

Serão armazenadas apenas as informações necessárias para apoiar o processo pedagógico, preservar a identidade do estudante e registrar sua evolução ao longo da jornada escolar.
