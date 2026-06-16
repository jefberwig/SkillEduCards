# SkillEduCards

# Modelo Conceitual do Banco de Dados

Versão: 0.1.0-alpha

---

# Objetivo

Definir as principais entidades do sistema e seus relacionamentos, servindo como base para toda a arquitetura do banco de dados.

---

# Visão Geral

O SkillEduCards é organizado em torno da jornada do estudante.

Todas as informações armazenadas têm como finalidade apoiar o acompanhamento pedagógico, reconhecer conquistas e promover o protagonismo estudantil.

---

# Entidades Principais

## Escola

Representa uma instituição cadastrada no sistema.

Relacionamentos:

- possui várias temporadas;
- possui várias turmas;
- possui vários professores;
- possui vários estudantes.

---

## Temporada

Representa um ano letivo ou ciclo de aprendizagem.

Relacionamentos:

- pertence a uma escola;
- possui várias missões;
- possui várias medalhas;
- possui várias cartas.

---

## Turma

Representa uma turma da escola.

Relacionamentos:

- pertence a uma escola;
- possui vários estudantes;
- possui vários professores.

---

## Professor

Representa um usuário com permissões pedagógicas.

Relacionamentos:

- pertence a uma escola;
- acompanha uma ou mais turmas;
- cria missões;
- registra eventos pedagógicos.

---

## Estudante

Entidade central do sistema.

Relacionamentos:

- pertence a uma turma;
- possui uma carta por temporada;
- possui missões;
- possui medalhas;
- possui especialidades;
- possui eventos registrados;
- possui histórico de XP.

---

## Carta

Representa a identidade gamificada do estudante.

Componentes:

- Avatar
- Nome Heroico
- Classe
- Elemento
- Título Evolutivo
- XP
- Nível

Relacionamentos:

- pertence a um estudante;
- pertence a uma temporada.

---

## Evento

Representa qualquer ação positiva registrada.

Exemplos:

- entrega de atividade;
- participação;
- leitura;
- projeto;
- colaboração.

Todo evento poderá gerar XP.

---

## Missão

Objetivo pedagógico.

Pode ser:

- individual;
- coletiva.

Relacionamentos:

- criada por professor;
- executada por estudantes.

---

## Medalha

Reconhecimento por competências desenvolvidas.

Relacionamentos:

- pode ser conquistada por vários estudantes.

---

## Especialidade

Área de destaque desenvolvida pelo estudante.

Exemplos:

- Matemática
- Ciências
- Comunicação
- Tecnologia

---

## Histórico XP

Registra toda evolução do estudante.

Nunca é apagado.

---

## Responsável

Usuário que acompanha um estudante.

Permissões:

- visualizar evolução;
- visualizar cartas;
- acompanhar missões.

---

# Fluxo Principal

Escola

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

Nível

↓

Medalhas

↓

Especialidades

↓

Dashboard

---

# Princípios

Nenhuma entidade existe para punir estudantes.

Todas existem para registrar evolução, apoiar decisões pedagógicas e reconhecer conquistas.

---

# Filosofia do Modelo

Todo dado armazenado deve responder uma pergunta pedagógica útil.

Se um dado não contribui para melhorar a aprendizagem ou apoiar professores, ele não deve existir no sistema.
