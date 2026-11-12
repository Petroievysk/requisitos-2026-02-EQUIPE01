# Especificação de Requisitos de Software (SRS)

> **Projeto:** Prepara ENADE - UNIFOR
> **Padrão:** IEEE 830-1998 (Adaptado para especificação orientada a Casos de Uso)
> **Sprint:** 2 (Trabalho P2)

---

## 1. Introdução

### 1.1 Propósito
Este documento especifica os requisitos de software para o sistema **Prepara ENADE**. O objetivo é fornecer uma descrição detalhada da plataforma web/mobile focada em gestão de aprendizagem, detalhando as interações dos usuários e o comportamento do sistema por meio de Casos de Uso, servindo de base para a arquitetura e prototipagem.

### 1.2 Escopo
O **Prepara ENADE** permitirá que os estudantes da Unifor realizem simulados cronometrados com questões reais de exames anteriores do ENADE, acessem gabaritos comentados e interajam em fóruns de discussão. Além disso, o sistema gerará dashboards de desempenho (Analytics) para estudantes, coordenadores e professores. O sistema integrará com a autenticação institucional (SSO) da Unifor.

### 1.3 Definições, Acrônimos e Abreviações
*   **ENADE:** Exame Nacional de Desempenho dos Estudantes.
*   **INEP:** Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira.
*   **SSO:** *Single Sign-On* (Autenticação Única Institucional).
*   **LGPD:** Lei Geral de Proteção de Dados.
*   **SRS:** *Software Requirements Specification*.

### 1.4 Visão Geral do Documento
Este documento está estruturado em três seções principais: Introdução, Descrição Geral (perspectiva, funções e restrições) e Requisitos Detalhados (especificação formal dos Casos de Uso). Ao final, apresenta-se a Revisão de Consistência com a modelagem UML da Sprint 1.

---

## 2. Descrição Geral

### 2.1 Perspectiva do Produto
O sistema opera como uma plataforma independente, mas fortemente integrada ao ecossistema da Unifor (Unifor Online/Google Workspace) para autenticação de usuários, garantindo que apenas a comunidade acadêmica tenha acesso aos dados de desempenho. As questões são alimentadas a partir do banco de dados público do INEP.

### 2.2 Funções do Produto
*   Autenticação segura institucional.
*   Busca e filtragem de banco de questões.
*   Execução de simulados com motor de tempo (cronômetro).
*   Exibição de gabaritos comentados por professores.
*   Fórum de discussão colaborativo por questão.
*   Painéis de relatórios estatísticos de desempenho.

### 2.3 Características dos Usuários
*   **Estudante:** Possui conhecimentos básicos de navegação web/mobile. Busca praticidade, interfaces limpas e feedback imediato.
*   **Professor/Coordenador:** Usuários com foco analítico, interessados em métricas consolidadas para suporte a decisões pedagógicas.
*   **Administrador:** Possui conhecimento técnico para gerenciar a base de dados (importação do INEP).

### 2.4 Restrições
*   O sistema é um projeto conceitual de engenharia de requisitos, não havendo implementação de código-fonte em nível de produção nesta fase.
*   Deve seguir as normas da LGPD, anonimizando dados de alunos em visões macro se exigido pela universidade.

---

## 3. Requisitos Detalhados (Casos de Uso)

Abaixo estão detalhados os principais Casos de Uso (UC) mapeados no diagrama UML da Sprint 1.

### UC-01: Autenticar via SSO Institucional
*   **Ator Primário:** Estudante, Professor, Coordenador, Administrador.
*   **Pré-condições:** O usuário deve possuir um e-mail institucional ativo (`@unifor.br`).
*   **Fluxo Principal:**
    1. O usuário acessa a página inicial e clica em "Entrar com Unifor".
    2. O sistema redireciona para o provedor de identidade (Google/UOL).
    3. O usuário insere suas credenciais.
    4. O provedor valida e retorna o token de acesso.
    5. O sistema identifica o perfil do usuário (Aluno, Professor, etc.) e redireciona para o painel correspondente.
*   **Fluxos Alternativos:**
    *   *4a. Credenciais inválidas:* O provedor exibe mensagem de erro e o acesso é negado.

### UC-03: Realizar Simulado Cronometrado
*   **Ator Primário:** Estudante.
*   **Pré-condições:** Usuário autenticado como Estudante.
*   **Fluxo Principal:**
    1. O estudante seleciona a opção "Novo Simulado".
    2. O estudante define os filtros (Ex: Área de ADS, Ano 2023).
    3. O sistema carrega 35 questões e inicia o cronômetro (4 horas).
    4. O estudante navega pelas questões, marcando as alternativas.
    5. O estudante clica em "Finalizar Simulado".
    6. O sistema computa os acertos, grava o histórico e exibe o resultado final.
*   **Fluxos Alternativos:**
    *   *3a. Tempo Esgotado:* Se o cronômetro chegar a zero, o sistema executa automaticamente o passo 5 e 6 com as respostas preenchidas até o momento.

### UC-04 e UC-05: Acessar Gabarito e Interagir no Fórum
*   **Ator Primário:** Estudante, Professor.
*   **Pré-condições:** Simulado finalizado ou acesso avulso à questão.
*   **Fluxo Principal:**
    1. O sistema exibe o enunciado da questão e a resposta correta.
    2. O sistema exibe o texto explicativo (gabarito comentado).
    3. O usuário visualiza a seção de comentários logo abaixo.
    4. O usuário digita uma dúvida/comentário e clica em "Enviar".
    5. O sistema registra o comentário com o nome e horário, atualizando a thread.

### UC-06: Visualizar Painel de Desempenho (Dashboards)
*   **Ator Primário:** Estudante, Coordenador.
*   **Pré-condições:** Usuário autenticado.
*   **Fluxo Principal (Estudante):**
    1. Acessa a aba "Meu Desempenho".
    2. O sistema exibe um gráfico de radar comparando Formação Geral vs. Específica.
*   **Fluxo Principal (Coordenador):**
    1. Acessa a aba "Visão Institucional".
    2. Seleciona o curso e semestre.
    3. O sistema exibe a média da turma, identificando os tópicos com menor taxa de acerto.

---

## 4. Revisão de Consistência (Alinhamento UML e Requisitos)

Para garantir a rastreabilidade e integridade arquitetural do projeto, a matriz abaixo comprova o alinhamento entre a elicitação (Documento de Visão), a modelagem (Diagramas UML) e a especificação (SRS).

| ID / Funcionalidade (Visão) | Caso de Uso UML (Sprint 1) | Requisito Detalhado (SRS) | Validação / Consistência |
| :--- | :--- | :--- | :--- |
| **F-01:** Autenticar SSO | `UC1: Autenticar via SSO` | Específico no **UC-01** | **OK**. Fluxo de Token coberto. |
| **F-02:** Filtrar Questões | `UC2: Filtrar Banco` | Passo 2 do **UC-03** | **OK**. Integrado na jornada de simulado. |
| **F-03:** Simulado Tempo | `UC3: Realizar Simulado` | Específico no **UC-03** | **OK**. Regra do cronômetro aplicada. |
| **F-04:** Gabarito Comentado | `UC4: Acessar Gabarito` | Específico no **UC-04** | **OK**. Exibição pós-submissão. |
| **F-05:** Fórum por Questão | `UC5: Fórum da Questão` | Específico no **UC-05** | **OK**. Thread colaborativa garantida. |
| **F-06:** Dashboards | `UC6: Visualizar Painel` | Específico no **UC-06** | **OK**. Diferenciado por perfil (Aluno/Coord). |
| **F-07:** Importar Provas | `UC7: Importar INEP` | Requisito de Admin (Backstage) | **OK**. Módulo de conteúdo (UML) persistido. |

> **Conclusão da Revisão:** Todos os requisitos elicitados na Fase 1 possuem representação visual nos diagramas de Casos de Uso, Componentes e Implantação, e foram formalmente especificados em cenários principais e alternativos neste SRS. Não há requisitos órfãos.
