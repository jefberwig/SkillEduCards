# SkillEduCards

# Diagrama Entidade Relacionamento (ER)

Versão: 0.1.0-alpha

---

```mermaid
erDiagram

ESCOLAS ||--o{ TURMAS : possui
ESCOLAS ||--o{ PROFESSORES : possui
ESCOLAS ||--o{ TEMPORADAS : possui

TURMAS ||--o{ ESTUDANTES : contem

ESTUDANTES ||--|| CARTAS : possui

ESTUDANTES ||--o{ EVENTOS : gera

PROFESSORES ||--o{ EVENTOS : registra

TEMPORADAS ||--o{ MISSOES : possui

ESTUDANTES ||--o{ ESTUDANTE_MISSOES : participa

MISSOES ||--o{ ESTUDANTE_MISSOES : pertence

MEDALHAS ||--o{ ESTUDANTE_MEDALHAS : concede

ESTUDANTES ||--o{ ESTUDANTE_MEDALHAS : conquista

ESPECIALIDADES ||--o{ ESTUDANTE_ESPECIALIDADES : define

ESTUDANTES ||--o{ ESTUDANTE_ESPECIALIDADES : desenvolve
```

---

# Filosofia

O SkillEduCards utiliza uma arquitetura baseada em eventos.

Toda evolução do estudante é registrada como um evento.

O XP, nível, medalhas e dashboards são derivados desses registros.

---

# Entidade Central

ESTUDANTE

↓

EVENTOS

↓

XP

↓

CARTA

↓

DASHBOARD

---

# Benefícios

- Histórico completo
- Auditoria
- Evolução permanente
- Dashboards inteligentes
- Futuras análises por IA
