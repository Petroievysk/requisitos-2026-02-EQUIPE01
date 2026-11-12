# Visão da Demanda (VD) — ENADE

> **Projeto de Extensão — Plataforma de Gestão do Conhecimento e Aprendizagem (ENADE)**
> Natureza: Estudo de caso para a disciplina de Requisitos e Modelagem de Sistemas da Unifor.

## Identificação e Histórico

| Campo | Informação |
| :--- | :--- |
| **Nome e identificador** | Prepara ENADE — VD-ENADE-001 |
| **Tipo** | Novo sistema web/mobile com integrações institucionais |
| **Sistema relacionado** | Autenticação Unifor Online (UOL), Portal INEP |
| **Área solicitante** | Coordenação Acadêmica / Disciplina de Extensão |
| **Responsável pela elaboração** | Diego Rodrigues (@Petroievysk) e José Guilherme (@DrwGuikkz) |
| **Responsável pela aprovação** | Prof. Marcelo Bezerra (@marcelobezerra-dotcom) |
| **Situação** | Versão Inicial de Elicitação |
| **Versão e data** | 1.0 — 12/11/2026 |

## 1. Objetivo
Proporcionar aos estudantes de graduação da Unifor um ambiente integrado de preparação realista para o ENADE[cite: 22]. O sistema visa suprir a falta de materiais organizados por meio de simulados cronometrados com questões oficiais, fóruns de discussão para aprendizagem colaborativa e painéis estatísticos de desempenho, subsidiando também o corpo docente com métricas para ações de reforço pedagógico.

## 2. Contexto, Problema e Descrição Sumária
### 2.1 Situação atual — entendimento inicial
Atualmente, os estudantes preparam-se para o ENADE utilizando arquivos em PDF isolados das provas anteriores do INEP. Não há validação imediata de tempo de resolução nem métricas de aproveitamento consolidadas.

### 2.2 Problema ou oportunidade
A falta de simulados práticos e materiais centralizados dificulta a autoavaliação do aluno. Além disso, a coordenação e os professores não possuem visibilidade sobre as áreas de maior defasagem (formação geral vs. específica) antes da realização do exame oficial.

### 2.3 Públicos afetados e impactos
Estudantes (público-alvo primário), Coordenadores de curso e Professores. O impacto esperado inclui a democratização do acesso a materiais de estudo, melhoria nos indicadores institucionais no ENADE e maior integração comunidade-universidade.

### 2.4 Evidências disponíveis
A elicitação baseou-se em **pesquisa exploratória** (benchmarking em sistemas como QConcursos e Estuda.com) e **análise documental** das diretrizes de necessidades educacionais fornecidas pela instituição.

### 2.5 Descrição sumária
Disponibilizar consultas a bancos de questões do INEP filtradas por área/ano; permitir a execução de simulados cronometrados; fornecer gabaritos comentados e fórum interativo; e produzir dashboards de desempenho por aluno e por turma.

## 3. Proposta de Valor e Sucesso da Demanda

| Benefício esperado | Indicador ou evidência | Resultado desejado (proposta) |
| :--- | :--- | :--- |
| **Preparação realista** | Conclusão de simulados no sistema | Reduzir a ansiedade e familiarizar o aluno com o formato e tempo de prova. |
| **Feedback imediato** | Acessos aos gabaritos comentados | Acelerar a correção de falhas de conceito através de explicações detalhadas. |
| **Aprendizado colaborativo** | Volume de interações no fórum | Fomentar discussões acadêmicas sobre questões complexas. |
| **Apoio à decisão pedagógica** | Relatórios de desempenho por área | Permitir que coordenadores direcionem revisões e aulas de reforço com base em dados. |

## 4. Partes Interessadas

| Parte interessada | Papel e interesse | Responsabilidade |
| :--- | :--- | :--- |
| **Coordenação de Curso** | Unidade beneficiária institucional | Priorizar necessidades e validar métricas de desempenho. |
| **Estudantes da Unifor** | Usuários finais | Consumir os simulados, relatar bugs e gerar os dados de uso. |
| **Professores** | Apoio pedagógico | Moderar fóruns e utilizar as estatísticas para revisão em sala. |
| **Equipe Discente (Desenvolvedores)** | Equipe do projeto | Especificar, modelar e prototipar a solução de estudo. |
| **Portal INEP** | Provedor de dados (Externo) | Fonte das questões, alternativas e gabaritos originais. |

## 5. Usuários e Atores Externos

| ID | Ator | Responsabilidade e acesso |
| :--- | :--- | :--- |
| **AT-01** | Estudante de Graduação | Realiza simulados, pesquisa questões, comenta no fórum e visualiza seu próprio desempenho. |
| **AT-02** | Coordenador de Curso | Consulta painéis estatísticos agregados por turma/área; não responde a simulados. |
| **AT-03** | Professor | Acessa estatísticas de suas disciplinas vinculadas e modera/comenta no fórum. |
| **AT-04** | Administrador do Sistema | Mantém o catálogo de questões e a estabilidade técnica; perfil técnico. |
| **AT-05** | Autenticação Google / UOL | Sistema externo (SSO) para validar login com credencial da instituição. |
| **AT-06** | Portal INEP | Sistema externo (Fonte de dados em PDF/estruturados). |

## 6. Necessidades e Catálogo de Funcionalidades

### 6.1 Necessidades (NEC)
| ID | Necessidade | Atores relacionados |
| :--- | :--- | :--- |
| **NEC-01** | Praticar resolução de provas em condições similares às reais. | AT-01 |
| **NEC-02** | Encontrar questões rapidamente por assunto, ano ou curso. | AT-01, AT-03 |
| **NEC-03** | Compreender erros e sanar dúvidas de forma colaborativa. | AT-01, AT-03 |
| **NEC-04** | Acompanhar a evolução e diagnosticar lacunas de aprendizagem. | AT-01, AT-02, AT-03 |
| **NEC-05** | Garantir acesso seguro exclusivo à comunidade acadêmica. | AT-04, AT-05 |

### 6.2 Funcionalidades (F)
| ID | Funcionalidade e resultado esperado | Necessidade | Atores | Prioridade |
| :--- | :--- | :--- | :--- | :--- |
| **F-01** | **Autenticar via SSO Institucional:** Permitir login seguro via Google Workspace / UOL. | NEC-05 | AT-01, AT-02, AT-03 | Essencial |
| **F-02** | **Filtrar Banco de Questões:** Busca facetada por ano, área e componente (Geral/Específico). | NEC-02 | AT-01, AT-03 | Essencial |
| **F-03** | **Motor de Simulados:** Gerar exame com tempo cronometrado e auto-submissão ao fim do tempo. | NEC-01 | AT-01 | Essencial |
| **F-04** | **Gabarito Comentado:** Exibir justificativa detalhada da resposta correta após a submissão. | NEC-03 | AT-01, AT-03 | Essencial |
| **F-05** | **Fórum por Questão:** Interface de comentários vinculada a cada questão para discussão. | NEC-03 | AT-01, AT-03 | Média |
| **F-06** | **Painel de Desempenho (Dashboards):** Gráficos de acertos por área de conhecimento (individual e global). | NEC-04 | AT-01, AT-02 | Essencial |
| **F-07** | **Importação INEP:** Rotina administrativa para carga de novas provas no banco de dados. | NEC-02 | AT-04, AT-06 | Essencial |

### 6.3 Regras de Negócio e Premissas
* **RN-01 (Direitos Autorais e LGPD):** A extração de provas deve preservar a fonte (INEP) e os relatórios estatísticos dos coordenadores devem anonimizar os alunos se exigido pela instituição.
* **RN-02 (Cronômetro):** Se o tempo do simulado esgotar, o sistema deve submeter imediatamente as respostas preenchidas até o momento.
* **RN-03 (Projeto Conceitual):** Esta etapa abrange documentação, arquitetura e prototipagem (Figma/Wireframes). Não é exigida implementação de código-fonte.

## 7. Visão Geral da Solução e Impactos

A plataforma foi arquitetada de forma modular, dividindo as responsabilidades para facilitar a rastreabilidade na modelagem UML:
1. **Módulo de Prática (Motor de Simulados):** Centraliza a lógica de tempo e submissão (F-03).
2. **Módulo de Conteúdo:** Gere as buscas e os gabaritos (F-02, F-04, F-07).
3. **Módulo Colaborativo:** Sustenta o fórum e as notificações (F-05).
4. **Módulo Analítico:** Consome os resultados para gerar relatórios e gráficos (F-06).

> **Nota de Modelagem:** Os diagramas arquiteturais (Casos de Uso, Componentes e Implantação) exigidos para esta fase de requisitos foram extraídos deste documento e estão detalhados no arquivo de acompanhamento `02_diagramas_uml.md`.
