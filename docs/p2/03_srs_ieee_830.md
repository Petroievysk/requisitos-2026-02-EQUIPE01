# Especificação de Requisitos de Software (SRS)

> **Projeto:** Prepara ENADE - UNIFOR
> **Identificador:** SRS-ENADE-001
> **Padrão:** IEEE 830-1998 (Adaptado para especificação orientada a Casos de Uso)
> **Sprint:** 2 (Trabalho P2)
> **Versão:** 2.0 — 16/11/2026

---

## 1. Introdução

### 1.1 Propósito
Este documento especifica os requisitos funcionais, não-funcionais, regras de negócio e casos de uso detalhados do sistema **Prepara ENADE**. O objetivo é fornecer uma descrição formal, completa e rastreável da plataforma web e mobile focada em gestão de aprendizagem e preparação para o exame, servindo de base para a arquitetura, prototipagem e validação acadêmica.

### 1.2 Escopo
O **Prepara ENADE** permitirá que os estudantes de graduação da Unifor realizem simulados cronometrados com questões oficiais de edições anteriores do ENADE, consultem questões avulsas por filtros, acessem gabaritos comentados por docentes e interajam em fóruns de discussão vinculados a cada questão. Além disso, o sistema disponibilizará painéis analíticos (dashboards) de desempenho para estudantes, professores e coordenadores de curso, integrando-se ao serviço de autenticação institucional (SSO) da Unifor e à base pública de exames do INEP.

### 1.3 Definições, Acrônimos e Abreviações
* **ENADE:** Exame Nacional de Desempenho dos Estudantes.
* **INEP:** Instituto Nacional de Estudos e Pesquisas Educacionais Anísio Teixeira.
* **LGPD:** Lei Geral de Proteção de Dados Pessoais (Lei nº 13.709/2018).
* **RF:** Requisito Funcional.
* **RN:** Regra de Negócio.
* **RNF:** Requisito Não-Funcional.
* **SRS:** *Software Requirements Specification* (Especificação de Requisitos de Software).
* **SSO:** *Single Sign-On* (Autenticação Única Institucional).
* **UC:** *Use Case* (Caso de Uso).
* **UOL:** Unifor Online.

### 1.4 Visão Geral do Documento
Este documento está organizado em quatro seções:
1. **Introdução:** Contextualiza o propósito, escopo e terminologia do documento.
2. **Descrição Geral:** Apresenta a perspectiva do produto, funções principais, perfis de usuários e restrições.
3. **Requisitos Detalhados:** Especifica os Requisitos Funcionais (`RF-01` a `RF-15`), Regras de Negócio (`RN-01` a `RN-05`), Requisitos Não-Funcionais (`RNF-01` a `RNF-07`) e o detalhamento formal de todos os Casos de Uso (`UC-01` a `UC-07`).
4. **Matriz de Rastreabilidade e Consistência:** Comprova o alinhamento entre o Documento de Visão (`01_visao_e_requisitos.md`), os Diagramas UML (`02_diagramas_uml.md`), os Requisitos e os Protótipos (`04_prototipos.md`).

---

## 2. Descrição Geral

### 2.1 Perspectiva do Produto
O **Prepara ENADE** opera como uma aplicação web responsiva e mobile integrada ao ecossistema institucional da Unifor (Unifor Online / Google Workspace) para autenticação de usuários via protocolo OAuth 2.0 / SSO, garantindo acesso restrito à comunidade acadêmica. O acervo de provas e questões objetivas é alimentado a partir dos cadernos públicos divulgados pelo INEP.

### 2.2 Funções do Produto
* **Autenticação Institucional (`F-01`):** Controle de acesso baseado em perfis (Estudante, Professor, Coordenador e Administrador) via credencial `@unifor.br`.
* **Consulta e Filtragem de Questões (`F-02`):** Pesquisa facetada no banco de questões por ano, curso/área, componente (Formação Geral ou Conhecimento Específico) e palavra-chave.
* **Motor de Simulados Cronometrados (`F-03`):** Geração e execução de simulados com contagem regressiva e submissão automática ao término do tempo.
* **Gabarito Comentado (`F-04`):** Exibição da alternativa correta e de justificativas pedagógicas elaboradas por professores.
* **Fórum Colaborativo por Questão (`F-05`):** Espaço de discussão vinculado a cada questão para esclarecimento de dúvidas entre estudantes e docentes.
* **Painéis Analíticos de Desempenho (`F-06`):** Relatórios e gráficos estatísticos individuais (Estudante) e consolidados por disciplina/curso (Professor e Coordenador).
* **Importação de Provas do INEP (`F-07`):** Módulo administrativo para ingestão, catalogação e publicação de novas provas e gabaritos oficiais.

### 2.3 Características dos Usuários
* **Estudante (`AT-01`):** Aluno regularmente matriculado na Unifor. Possui familiaridade básica com aplicações web/mobile e busca praticidade, feedback imediato e acompanhamento de evolução.
* **Coordenador de Curso (`AT-02`):** Gestor acadêmico com foco analítico, interessado em indicadores consolidados por turma, semestre e área de conhecimento para planejamento pedagógico.
* **Professor (`AT-03`):** Docente vinculado a disciplinas/cursos, responsável por comentar gabaritos, moderar fóruns e analisar lacunas de aprendizagem de suas turmas.
* **Administrador do Sistema (`AT-04`):** Usuário técnico responsável pela importação de provas do INEP, manutenção do catálogo de questões e gestão de permissões.

### 2.4 Restrições
* **R-01 (Escopo Conceitual):** Na etapa atual da disciplina, o projeto contempla a engenharia de requisitos, modelagem arquitetural e prototipação navegável (Figma), não havendo implantação em ambiente de produção.
* **R-02 (Conformidade Legal - LGPD):** Dados individuais de desempenho de estudantes não podem ser expostos nominalmente a terceiros; visões gerenciais de coordenação devem respeitar critérios de anonimização quando aplicável.
* **R-03 (Padronização de Exames):** Os simulados oficiais completos devem seguir a estrutura padrão adotada pelo ENADE (35 questões objetivas distribuídas entre Formação Geral e Componente Específico, com duração total de 4 horas).

---

## 3. Requisitos Detalhados

### 3.1 Requisitos Funcionais (RF)

| ID | Requisito Funcional | Descrição Detalhada (Entrada, Processamento e Saída) | Atores | Prioridade | Rastreabilidade |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **RF-01** | **Autenticação via SSO Institucional** | O sistema deve redirecionar o usuário para o provedor de identidade institucional (Google Workspace / UOL via OAuth 2.0), validar se o e-mail pertence ao domínio ativo `@unifor.br` e iniciar uma sessão autenticada com token válido. | Todos os perfis | Essencial | `F-01` / `UC-01` |
| **RF-02** | **Controle de Acesso Baseado em Perfil (RBAC)** | Após a autenticação, o sistema deve identificar o vínculo institucional do usuário (Estudante, Professor, Coordenador ou Administrador) e restringir menus, telas e operações de acordo com as permissões de seu perfil. | Todos os perfis | Essencial | `F-01` / `UC-01` |
| **RF-03** | **Pesquisa e Filtragem Facetada de Questões** | O sistema deve permitir consultar o banco de questões aplicando filtros combinados por: Ano da Edição, Curso/Área do ENADE, Componente (Formação Geral ou Conhecimento Específico) e busca textual por palavra-chave no enunciado, retornando lista paginada. | Estudante, Professor | Essencial | `F-02` / `UC-02` |
| **RF-04** | **Resolução Avulsa de Questões** | O sistema deve permitir que o estudante selecione qualquer questão filtrada fora do modo simulado, marque uma alternativa (`A` a `E`), submeta a resposta individualmente e receba retorno visual imediato de acerto (verde) ou erro (vermelho). | Estudante | Importante | `F-02` / `UC-02` |
| **RF-05** | **Configuração de Simulado** | O sistema deve disponibilizar tela de parametrização onde o estudante seleciona o Ano da Prova e a Área de Conhecimento, exibindo antes do início o resumo das regras da prova (35 questões e tempo limite de 4 horas). | Estudante | Essencial | `F-03` / `UC-03` |
| **RF-06** | **Execução de Simulado com Cronômetro e Mapa de Questões** | Ao iniciar o simulado, o sistema deve carregar as 35 questões (8 de Formação Geral e 27 de Componente Específico), exibir cronômetro regressivo (`04:00:00`) fixo no topo, permitir navegação sequencial ("Anterior"/"Próxima") ou direta via mapa lateral de status (respondida/em branco) e salvar respostas automaticamente. | Estudante | Essencial | `F-03` / `UC-03` |
| **RF-07** | **Submissão Manual e Automática por Tempo Esgotado** | O sistema deve permitir que o estudante finalize o simulado manualmente a qualquer momento (com alerta caso existam questões em branco) e deve executar a submissão automática imediata caso o cronômetro atinja `00:00:00`, bloqueando alterações posteriores. | Estudante | Essencial | `F-03` / `UC-03` |
| **RF-08** | **Apuração de Resultados e Persistência de Histórico** | Ao encerrar o simulado, o sistema deve contabilizar o total e o percentual de acertos separados por Formação Geral e Componente Específico (considerando questões em branco como erro) e gravar a tentativa no histórico permanente do estudante. | Estudante | Essencial | `F-03` / `UC-03` |
| **RF-09** | **Consulta de Gabarito Oficial e Comentado** | Após a finalização de um simulado ou resposta avulsa, o sistema deve exibir a alternativa oficial correta do INEP e uma seção expansível com a resolução comentada elaborada por professores. | Estudante, Professor | Essencial | `F-04` / `UC-04` |
| **RF-10** | **Cadastro e Edição de Gabarito Comentado** | O sistema deve disponibilizar um editor de texto formatado para que professores vinculados à área de conhecimento cadastrem ou atualizem a justificativa pedagógica das questões, registrando nome do docente e data da atualização. | Professor | Importante | `F-04` / `UC-04` |
| **RF-11** | **Publicação de Comentários no Fórum da Questão** | O sistema deve exibir uma thread de discussão cronológica abaixo de cada questão liberada, permitindo que estudantes e professores publiquem dúvidas, respostas e comentários com identificação de nome, selo de perfil e data/hora. | Estudante, Professor | Importante | `F-05` / `UC-05` |
| **RF-12** | **Moderação de Comentários no Fórum** | O sistema deve permitir que professores e administradores ocultem ou removam postagens que contenham spam, linguagem imprópria ou conteúdo fora do escopo acadêmico, mantendo registro de auditoria da moderação. | Professor, Administrador | Desejável | `F-05` / `UC-05` |
| **RF-13** | **Dashboard Analítico Individual (Estudante)** | O sistema deve gerar painel visual para o estudante contendo média geral de acertos, total de questões resolvidas, gráfico de radar/barras comparando Formação Geral vs. Conhecimento Específico e gráfico de evolução histórica por simulado. | Estudante | Essencial | `F-06` / `UC-06` |
| **RF-14** | **Dashboard Analítico Docente e Institucional** | O sistema deve gerar painéis consolidados para professores (por disciplina/área vinculada) e coordenadores (por curso/semestre), destacando taxa de adesão, média geral e ranking dos tópicos com maior índice de erro, respeitando a anonimização da LGPD. | Professor, Coordenador | Essencial | `F-06` / `UC-06` |
| **RF-15** | **Importação Estruturada de Provas do INEP** | O sistema deve fornecer módulo administrativo para upload de provas e gabaritos oficiais do INEP (JSON/CSV/PDF processado), realizando validação estrutural (enunciado, imagens, 5 alternativas e gabarito), pré-visualização para ajustes manuais e publicação no banco. | Administrador | Essencial | `F-07` / `UC-07` |

### 3.2 Regras de Negócio (RN)

* **RN-01 (Exclusividade Institucional):** Somente usuários autenticados com domínio institucional ativo da Unifor (`@unifor.br`) podem acessar o sistema.
* **RN-02 (Estrutura Padrão do Simulado Completo):** Um simulado completo corresponde a 35 questões objetivas (8 de Formação Geral e 27 de Componente Específico) com tempo limite de 4 horas (240 minutos).
* **RN-03 (Submissão Irreversível e Auto-envio):** Após a finalização do simulado — seja por ação do estudante ou por esgotamento do cronômetro — as respostas são bloqueadas para edição e computadas definitivamente no histórico. Questões não respondidas são contabilizadas como erro.
* **RN-04 (Liberação do Gabarito Comentado):** Durante a execução de um simulado ativo, o gabarito oficial e os comentários permanecem ocultos, sendo liberados somente após a submissão da prova.
* **RN-05 (Direitos Autorais e Anonimização LGPD):** Toda questão importada deve manter a referência oficial do ano e caderno do INEP. Nos relatórios gerenciais de coordenadores, os dados individuais dos estudantes devem ser agregados ou anonimizados conforme diretrizes da LGPD.

### 3.3 Requisitos Não-Funcionais (RNF)

| ID | Categoria | Requisito Não-Funcional | Critério de Aceitação / Métrica |
| :--- | :--- | :--- | :--- |
| **RNF-01** | Segurança | Autenticação Delegada e Criptografia | Toda comunicação cliente-servidor deve utilizar HTTPS (TLS 1.2+) e a autenticação deve seguir o padrão OAuth 2.0 via provedor institucional, sem armazenamento de senhas no banco local. |
| **RNF-02** | Privacidade (LGPD) | Proteção e Anonimização de Dados | Os painéis de coordenadores devem exibir indicadores estatísticos agregados sem expor informações pessoais sensíveis dos estudantes. |
| **RNF-03** | Desempenho | Tempo de Resposta e Carregamento | O carregamento de uma prova completa (35 questões com imagens) e a transição entre questões durante o simulado devem ocorrer em no máximo **2 segundos**. |
| **RNF-04** | Confiabilidade | Precisão e Persistência do Cronômetro | O cronômetro do simulado deve ser sincronizado com o relógio do servidor e salvar automaticamente o progresso das respostas a cada interação, evitando perda de dados em caso de queda de conexão. |
| **RNF-05** | Usabilidade | Interface Responsiva e Intuitiva | A interface deve seguir o guia de estilos institucional da Unifor, permitindo que um estudante inicie seu primeiro simulado em até **3 cliques** após o login. |
| **RNF-06** | Portabilidade | Compatibilidade Web e Mobile | A aplicação deve operar de forma responsiva nos principais navegadores desktop (Chrome, Edge, Firefox, Safari) e dispositivos móveis (Android e iOS). |
| **RNF-07** | Disponibilidade | Continuidade do Serviço | O sistema deve garantir disponibilidade mínima de **99,5%** durante os períodos letivos e semanas preparatórias que antecedem o ENADE. |

### 3.4 Especificação Detalhada dos Casos de Uso (UC-01 a UC-07)

#### UC-01: Autenticar via SSO Institucional
* **Identificador:** UC-01 (Rastreável a `F-01`, `RF-01`, `RF-02`)
* **Ator Primário:** Estudante, Professor, Coordenador, Administrador.
* **Ator Secundário:** Serviço de Autenticação Institucional (Google Workspace / UOL).
* **Pré-condições:** O usuário deve possuir uma conta institucional ativa da Unifor (`@unifor.br`) e conexão com a internet.
* **Pós-condições:** Sessão autenticada criada com token válido e usuário redirecionado para a interface correspondente ao seu perfil.
* **Regras de Negócio:** `RN-01`.
* **Fluxo Principal:**
  1. O usuário acessa a página inicial do **Prepara ENADE** e seleciona a opção *"Entrar com Conta Unifor (Google)"*.
  2. O sistema redireciona o navegador para o provedor de identidade institucional (OAuth 2.0).
  3. O usuário informa suas credenciais institucionais no provedor.
  4. O provedor valida as credenciais e retorna o token de autenticação ao sistema.
  5. O sistema verifica o domínio `@unifor.br`, identifica o perfil vinculado ao usuário (Estudante, Professor, Coordenador ou Administrador) e carrega o respectivo painel inicial.
* **Fluxos Alternativos:**
  * *3a. Usuário já possui sessão ativa no Google/UOL no navegador:* O provedor valida automaticamente o vínculo e executa diretamente o passo 4.
* **Fluxos de Exceção:**
  * *4a. Credenciais inválidas ou domínio não institucional:* O provedor recusa a autenticação ou o sistema bloqueia o acesso, exibindo a mensagem *"Acesso permitido apenas para contas institucionais @unifor.br"*.
  * *4b. Indisponibilidade do serviço SSO:* O sistema exibe mensagem informando falha temporária na autenticação institucional e orienta tentar novamente.

---

#### UC-02: Filtrar Banco de Questões
* **Identificador:** UC-02 (Rastreável a `F-02`, `RF-03`, `RF-04`)
* **Ator Primário:** Estudante, Professor.
* **Pré-condições:** Usuário autenticado no sistema (`UC-01`) e banco de questões previamente alimentado (`UC-07`).
* **Pós-condições:** Lista de questões filtradas exibida na tela; caso o estudante responda uma questão avulsa, o resultado é registrado em seu histórico.
* **Regras de Negócio:** `RN-05`.
* **Fluxo Principal:**
  1. O usuário acessa a seção *"Banco de Questões"* no menu principal.
  2. O sistema exibe os filtros disponíveis: Ano da Prova, Área/Curso, Componente (Formação Geral ou Específico) e campo de busca por palavra-chave.
  3. O usuário seleciona os critérios desejados e clica em *"Filtrar"*.
  4. O sistema consulta a base de dados e exibe a lista paginada de questões correspondentes, indicando ano, área e enunciado resumido.
  5. O usuário seleciona uma questão para visualização completa (e, no caso do Estudante, pode marcar uma alternativa para resolução avulsa e acionar o `UC-04`).
* **Fluxos Alternativos:**
  * *3a. Limpar filtros:* O usuário aciona *"Limpar Filtros"* e o sistema retorna à listagem padrão ordenada pelas edições mais recentes.
* **Fluxos de Exceção:**
  * *4a. Nenhuma questão encontrada:* O sistema exibe a mensagem *"Nenhuma questão encontrada para os filtros selecionados"* e sugere ampliar os critérios de busca.

---

#### UC-03: Realizar Simulado Cronometrado
* **Identificador:** UC-03 (Rastreável a `F-03`, `RF-05`, `RF-06`, `RF-07`, `RF-08`)
* **Ator Primário:** Estudante.
* **Pré-condições:** Usuário autenticado com perfil de Estudante (`UC-01`).
* **Pós-condições:** Simulado encerrado, respostas bloqueadas, pontuação calculada por componente e histórico de desempenho atualizado (`UC-06`).
* **Regras de Negócio:** `RN-02`, `RN-03`, `RN-04`.
* **Fluxo Principal:**
  1. No painel inicial, o estudante aciona *"Iniciar Novo Simulado"*.
  2. O sistema apresenta a tela de configuração com seleção de Ano da Prova e Área de Conhecimento, além do aviso das regras (35 questões e duração de 4 horas).
  3. O estudante confirma os parâmetros e clica em *"Começar Simulado"*.
  4. O sistema carrega as 35 questões (8 de Formação Geral e 27 de Componente Específico), inicia o cronômetro regressivo (`04:00:00`) no cabeçalho fixo e exibe o mapa lateral de questões.
  5. O estudante navega entre as questões (botões *"Anterior"*, *"Próxima"* ou mapa de questões) e seleciona as alternativas desejadas (`A` a `E`).
  6. A cada alternativa marcada, o sistema salva automaticamente o progresso no servidor.
  7. Ao concluir, o estudante clica em *"Finalizar Simulado"* e confirma o envio na caixa de diálogo.
  8. O sistema encerra o cronômetro, computa os acertos por componente, grava o resultado no histórico e exibe o resumo do desempenho com acesso ao gabarito (`UC-04`).
* **Fluxos Alternativos:**
  * *7a. Encerramento com questões em branco:* O sistema alerta quantas questões ainda estão sem resposta; caso o estudante confirme, prossegue para o passo 8 contabilizando as não respondidas como erro (`RN-03`).
* **Fluxos de Exceção:**
  * *5a. Tempo Esgotado (`00:00:00`):* Se o cronômetro chegar a zero antes da finalização manual, o sistema bloqueia imediatamente a marcação de respostas, executa automaticamente o passo 8 e exibe o aviso *"Tempo esgotado! Seu simulado foi finalizado automaticamente"*.
  * *5b. Queda temporária de conexão durante a prova:* O sistema mantém o estado local temporário e ressincroniza as respostas e o tempo restante com o servidor assim que a conexão for restabelecida.

---

#### UC-04: Acessar e Gerenciar Gabarito Comentado
* **Identificador:** UC-04 (Rastreável a `F-04`, `RF-09`, `RF-10`)
* **Ator Primário:** Estudante, Professor.
* **Pré-condições:** Usuário autenticado (`UC-01`). Para o Estudante, o simulado deve estar finalizado (`RN-04`) ou a questão deve estar sendo visualizada em modo de estudo avulso (`UC-02`).
* **Pós-condições:** Gabarito oficial e explicação exibidos ao usuário; caso editado pelo Professor, nova justificativa persistida na base de dados.
* **Regras de Negócio:** `RN-04`, `RN-05`.
* **Fluxo Principal (Consulta — Estudante e Professor):**
  1. Após finalizar um simulado (`UC-03`) ou abrir uma questão no banco (`UC-02`), o usuário acessa a tela de revisão da questão.
  2. O sistema exibe o enunciado completo, a alternativa marcada pelo estudante (se houver) destacada em verde (acerto) ou vermelho (erro), e a alternativa oficial correta.
  3. O usuário expande a seção *"Gabarito Comentado / Explicação do Professor"*.
  4. O sistema apresenta a justificativa pedagógica detalhada explicando o porquê da alternativa correta e o motivo de incorreção das demais.
* **Fluxos Alternativos:**
  * *3a. Cadastro ou Edição de Explicação (Ator: Professor):*
    1. O professor clica no botão *"Editar Comentário Oficial"* na questão de sua área.
    2. O sistema abre um editor de texto formatado.
    3. O professor redige ou atualiza a resolução comentada e clica em *"Salvar Explicação"*.
    4. O sistema valida o conteúdo, registra a autoria docente e atualiza o gabarito comentado da questão.
* **Fluxos de Exceção:**
  * *4a. Questão ainda sem gabarito comentado:* O sistema exibe a alternativa oficial correta do INEP e informa *"Explicação comentada ainda não cadastrada por um professor para esta questão"*.

---

#### UC-05: Interagir no Fórum da Questão
* **Identificador:** UC-05 (Rastreável a `F-05`, `RF-11`, `RF-12`)
* **Ator Primário:** Estudante, Professor.
* **Pré-condições:** Usuário autenticado (`UC-01`) visualizando uma questão liberada para revisão (`UC-04`).
* **Pós-condições:** Novo comentário publicado e exibido na thread da questão (ou comentário moderado/ocultado pelo Professor).
* **Regras de Negócio:** `RN-01`, `RN-04`.
* **Fluxo Principal:**
  1. Na tela de visualização da questão, o usuário rola até a seção *"Discussão / Fórum da Questão"*.
  2. O sistema exibe a lista de comentários existentes em ordem cronológica, identificando nome, perfil (Estudante ou selo de Professor) e data/hora da postagem.
  3. O usuário digita sua dúvida, contribuição ou resposta no campo de texto e clica em *"Publicar Comentário"*.
  4. O sistema valida que o campo não está vazio, persiste o comentário vinculado ao ID da questão e atualiza a lista em tela.
* **Fluxos Alternativos:**
  * *2a. Moderação de Comentário (Ator: Professor/Administrador):*
    1. O moderador identifica um comentário ofensivo, spam ou fora do contexto acadêmico.
    2. O moderador seleciona a opção *"Ocultar/Remover Comentário"* e informa o motivo.
    3. O sistema oculta o conteúdo público e registra o log de moderação.
* **Fluxos de Exceção:**
  * *4a. Envio de comentário vazio:* O sistema impede o envio e destaca o campo informando *"Digite uma mensagem antes de publicar"*.

---

#### UC-06: Visualizar Painel de Desempenho (Dashboards)
* **Identificador:** UC-06 (Rastreável a `F-06`, `RF-13`, `RF-14`)
* **Ator Primário:** Estudante, Professor, Coordenador.
* **Pré-condições:** Usuário autenticado (`UC-01`).
* **Pós-condições:** Indicadores estatísticos e gráficos renderizados conforme o perfil do usuário.
* **Regras de Negócio:** `RN-05` (LGPD).
* **Fluxo Principal (Visão Estudante):**
  1. O estudante acessa a aba *"Meu Desempenho"* no menu lateral.
  2. O sistema consulta o histórico de simulados e questões avulsas do estudante.
  3. O sistema exibe cards com média geral, total de questões resolvidas, gráfico de radar/barras comparando **Formação Geral** vs. **Conhecimento Específico** e gráfico de linha da evolução temporal.
* **Fluxos Alternativos:**
  * *1a. Visão Professor:*
    1. O professor acessa a aba *"Desempenho das Disciplinas"*.
    2. O sistema exibe os indicadores agregados das áreas/disciplinas vinculadas ao docente, destacando os temas com menor percentual de acerto pelos alunos para orientar aulas de revisão.
  * *1b. Visão Coordenador de Curso:*
    1. O coordenador acessa a aba *"Painel Institucional do Curso"*.
    2. O coordenador filtra por curso, semestre e edição do simulado.
    3. O sistema exibe a média geral do curso, taxa de adesão dos estudantes e ranking de tópicos críticos, mantendo os dados individuais anonimizados conforme a LGPD (`RN-05`).
* **Fluxos de Exceção:**
  * *2a. Ausência de dados históricos:* Caso o estudante ainda não tenha concluído nenhum simulado (ou não existam respostas registradas para o curso filtrado), o sistema exibe estado vazio educativo com o botão *"Iniciar Primeiro Simulado"*.

---

#### UC-07: Importar Provas e Questões do INEP
* **Identificador:** UC-07 (Rastreável a `F-07`, `RF-15`)
* **Ator Primário:** Administrador.
* **Ator Secundário:** Portal INEP (Fonte de dados).
* **Pré-condições:** Usuário autenticado com perfil de Administrador (`UC-01`).
* **Pós-condições:** Nova edição de prova, questões, imagens e gabaritos oficiais cadastrados e disponíveis no banco de questões (`UC-02` e `UC-03`).
* **Regras de Negócio:** `RN-02`, `RN-05`.
* **Fluxo Principal:**
  1. O administrador acessa o módulo *"Gestão de Conteúdo > Importar Provas INEP"*.
  2. O sistema exibe o formulário de importação solicitando: Ano da Edição, Área/Curso do ENADE, arquivo estruturado da prova (JSON/CSV/PDF processado) e arquivo de gabarito oficial.
  3. O administrador anexa os arquivos e aciona *"Processar e Pré-visualizar"*.
  4. O sistema realiza o parsing dos dados, valida a estrutura das questões (enunciado, imagens, 5 alternativas e gabarito oficial) e apresenta uma tela de conferência.
  5. O administrador revisa os dados extraídos e clica em *"Confirmar e Publicar no Banco"*.
  6. O sistema persiste as questões com a tag oficial da fonte INEP e exibe confirmação de sucesso.
* **Fluxos Alternativos:**
  * *5a. Ajuste manual antes da publicação:* Caso alguma imagem ou formatação apresente desajuste na pré-visualização, o administrador edita o item diretamente na tela de conferência antes de confirmar o passo 6.
* **Fluxos de Exceção:**
  * *4a. Arquivo corrompido ou fora do layout esperado:* O sistema interrompe a importação, destaca as linhas/questões com inconsistência (ex.: questão sem alternativa correta definida) e impede a publicação incompleta.
  * *6a. Prova duplicada:* Caso já exista uma prova cadastrada para o mesmo Ano e Área, o sistema alerta o administrador e solicita confirmação explícita para sobrescrever ou cancelar.

---

## 4. Matriz de Rastreabilidade e Consistência

A tabela abaixo consolida a rastreabilidade bidirecional entre os artefatos da Sprint 1 (`01_visao_e_requisitos.md` e `02_diagramas_uml.md`) e os artefatos da Sprint 2 (`03_srs_ieee_830.md` e `04_prototipos.md`), assegurando que não existam requisitos órfãos ou divergentes.

| Funcionalidade (Visão) | Caso de Uso UML | Requisito Funcional (SRS) | Caso de Uso Detalhado (SRS) | Tela no Protótipo (`04_prototipos.md`) | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **F-01:** Autenticar via SSO | `UC1: Autenticar via SSO` | `RF-01`, `RF-02` | **UC-01** | Tela 1: Login Institucional | **Consistente** |
| **F-02:** Filtrar Banco de Questões | `UC2: Filtrar Banco de Questões` | `RF-03`, `RF-04` | **UC-02** | Tela 3: Configuração / Filtros | **Consistente** |
| **F-03:** Motor de Simulados | `UC3: Realizar Simulado` | `RF-05` a `RF-08` | **UC-03** | Tela 3 e Tela 4: Ambiente de Simulado | **Consistente** |
| **F-04:** Gabarito Comentado | `UC4: Acessar Gabarito` | `RF-09`, `RF-10` | **UC-04** | Tela 5: Gabarito Comentado | **Consistente** |
| **F-05:** Fórum por Questão | `UC5: Fórum da Questão` | `RF-11`, `RF-12` | **UC-05** | Tela 5: Seção Discussão | **Consistente** |
| **F-06:** Painel de Desempenho | `UC6: Visualizar Painel` | `RF-13`, `RF-14` | **UC-06** | Tela 2: Dashboard Inicial | **Consistente** |
| **F-07:** Importar Provas INEP | `UC7: Importar Provas` | `RF-15` | **UC-07** | Módulo Administrativo (Backoffice) | **Consistente** |
