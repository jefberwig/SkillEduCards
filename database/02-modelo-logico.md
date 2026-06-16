# SkillEduCards

# Modelo Lógico do Banco de Dados

Versão: 0.1.0-alpha

---

# Objetivo

Definir a estrutura lógica do banco de dados do SkillEduCards, identificando tabelas, atributos, chaves primárias e relacionamentos.

---

# Tabela: escolas

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| nome | Texto |
| cidade | Texto |
| estado | Texto |
| criada_em | DataHora |

---

# Tabela: temporadas

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| escola_id | UUID |
| nome | Texto |
| ano | Inteiro |
| ativa | Boolean |

Relacionamento:

Uma escola possui várias temporadas.

---

# Tabela: turmas

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| escola_id | UUID |
| nome | Texto |
| serie | Texto |
| turno | Texto |

---

# Tabela: professores

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| escola_id | UUID |
| nome | Texto |
| email | Texto |
| perfil | Texto |

---

# Tabela: estudantes

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| turma_id | UUID |
| codigo_publico | Texto |
| nome_heroico | Texto |
| avatar | Texto |
| classe | Texto |
| elemento | Texto |
| ativo | Boolean |

Observação:

O nome real poderá existir apenas para uso administrativo.

O sistema público utilizará apenas o Nome Heroico.

---

# Tabela: cartas

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| estudante_id | UUID |
| temporada_id | UUID |
| nivel | Inteiro |
| xp_total | Inteiro |
| titulo | Texto |

Cada estudante possui uma carta por temporada.

---

# Tabela: eventos

(Esta será a tabela mais importante do sistema.)

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| estudante_id | UUID |
| professor_id | UUID |
| tipo_evento | Texto |
| descricao | Texto |
| xp | Inteiro |
| data_evento | DataHora |

Exemplo:

Entrega de atividade

Participação

Projeto

Leitura

Colaboração

---

# Tabela: missoes

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| temporada_id | UUID |
| titulo | Texto |
| descricao | Texto |
| xp_recompensa | Inteiro |

---

# Tabela: estudante_missoes

| Campo | Tipo |
|----------------|----------------|
| estudante_id | UUID |
| missao_id | UUID |
| status | Texto |
| concluida_em | DataHora |

---

# Tabela: medalhas

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| nome | Texto |
| descricao | Texto |
| icone | Texto |

---

# Tabela: estudante_medalhas

| Campo | Tipo |
|----------------|----------------|
| estudante_id | UUID |
| medalha_id | UUID |
| conquistada_em | DataHora |

---

# Tabela: especialidades

| Campo | Tipo |
|----------------|----------------|
| id | UUID |
| nome | Texto |
| descricao | Texto |

---

# Tabela: estudante_especialidades

| Campo | Tipo |
|----------------|----------------|
| estudante_id | UUID |
| especialidade_id | UUID |
| nivel | Inteiro |

---

# Relacionamentos

Escola

↓

Temporada

↓

Turma

↓

Estudante

↓

Carta

↓

Eventos

↓

XP

↓

Missões

↓

Medalhas

↓

Especialidades

---

# Princípios

Todo XP será calculado a partir da tabela EVENTOS.

Nenhum valor de XP será digitado manualmente.

Toda evolução será rastreável e auditável.

Toda informação pedagógica será construída a partir do histórico de eventos.
