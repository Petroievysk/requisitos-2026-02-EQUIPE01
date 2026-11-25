# Protótipos de Interface — Prepara ENADE
 
> **Projeto:** Prepara ENADE - UNIFOR
>
> **Sprint:** 2 (Trabalho P2)
>
> **Ferramenta:** Canva (protótipo web interativo)
>
> **Plataforma:** aplicação exclusivamente web, com layout responsivo (Desktop e Celular)
 
## 🔗 Links de Acesso
 
*   **Protótipo Navegável / Apresentação (Canva):** [https://gazelle-853dkc.my.canva.site/](https://gazelle-853dkc.my.canva.site/)
---
 
## 🧭 Visão Geral do Protótipo
 
O protótipo é uma **aplicação web interativa com dados fictícios**, que simula os principais fluxos do Prepara ENADE para os quatro perfis do sistema. Ele pode ser visualizado em **Desktop** e em **Celular**, demonstrando o layout responsivo exigido no `RNF-06`. Como não há aplicativo nativo, todo o acesso ocorre pelo navegador.
 
*   Os enunciados são **demonstrativos** e não correspondem a provas oficiais do INEP; cada questão traz a indicação "INEP · referência demonstrativa".
*   As respostas marcadas ficam registradas no navegador durante a demonstração.
*   Nenhum dado pessoal é coletado ou enviado.
## 🎨 Identidade Visual
 
*   **Marca:** logotipo "Prepara ENADE" com ícone de capelo (formatura).
*   **Paleta:** azul e branco, com tons de azul-gelo para fundos e cards, azul médio para ações principais e azul marinho para títulos.
*   **Tipografia:** Inter (sans-serif).
*   **Princípios de UX aplicados:** uma ação principal por tela, muito espaço em branco, textos curtos, avisos de estado (tempo restante, questão atual, resposta registrada), confirmação antes de ações irreversíveis e estados vazios com mensagem clara ("Nenhuma questão encontrada").
---
 
## 📱 Estrutura das Interfaces
 
### 1. Acesso Institucional (Referência UC-01 / RF-01 e RF-02)
*   **Elementos:** logotipo, selo "Acesso institucional", título **"Seu preparo começa aqui."**, cartão **"Protótipo demonstrativo"**, campo **"Explorar como"** (Estudante, Professor, Coordenador ou Administrador), botão **"Explorar protótipo"** e a nota "Dados fictícios. Não informe dados pessoais neste protótipo."
*   **Aviso institucional (RN-01):** informa que o acesso real seria via Google Workspace / UOL, exclusivamente com conta `@unifor.br`.
*   **Comportamento:** o protótipo **não autentica usuários**. O perfil escolhido define o menu e as telas exibidas (controle de acesso por perfil, `RF-02`). Na versão real, esta etapa é substituída pelo SSO institucional.
### 2. Perfil Estudante
 
O menu lateral (no celular, o ícone "hambúrguer") contém: **Início**, **Banco de Questões**, **Meu Desempenho** e **Sair da demonstração**.
 
#### 2.1 Início — Painel do Estudante (UC-06)
*   Saudação "Olá, estudante." e card de destaque "Pronto para seu próximo simulado?" com o botão **"Iniciar Novo Simulado"**.
*   Seção "Seu desempenho" com os cards **Média geral**, **Simulados concluídos** e **Questões resolvidas**, e o link "Ver detalhes".
*   Card "Banco de Questões" com o botão **"Explorar questões"**.
#### 2.2 Banco de Questões (Referência UC-02 / RF-03 e RF-04)
*   **Filtros:** Ano da edição, Área / curso, Componente (Formação Geral ou Conhecimento Específico) e busca por palavra-chave no enunciado, com os botões **"Filtrar"** e **"Limpar filtros"**.
*   **Resultado:** lista "Questões encontradas" com contador, indicação do componente, ano, área e fonte, e o botão **"Abrir questão"**.
*   **Estado vazio:** mensagem "Nenhuma questão encontrada" com sugestão de ampliar os critérios.
*   **Resolução avulsa:** ao abrir uma questão, o estudante marca uma alternativa e vê o gabarito oficial e o resultado ("Sua resposta: A · Erro").
#### 2.3 Configurar Simulado (Referência UC-03 / RF-05)
*   Seleção de **Ano da prova** e **Área de conhecimento**.
*   Card **"Como funciona"** (RN-02): 35 questões objetivas (8 de Formação Geral e 27 de Conhecimento Específico), tempo máximo de 4 horas e questões em branco contadas como erro.
*   Botão **"Começar Simulado"**.
#### 2.4 Ambiente do Simulado (Referência UC-03 / RF-06 e RF-07)
*   **Cabeçalho:** identificação do simulado ("2023 · Administração") e **cronômetro regressivo** (a partir de 04:00:00).
*   **Corpo:** identificação do componente (Formação Geral ou Conhecimento Específico), "Questão N de 35", enunciado e cinco alternativas (A a E).
*   **Mapa de questões:** grade de 1 a 35, com destaque para as respondidas e contorno azul para a questão atual. Em telas grandes aparece ao lado da questão; no celular, abre como gaveta pelo botão **"Mapa"**.
*   **Navegação:** botões "Anterior" e "Próxima" e botão **"Finalizar Simulado"**, que abre a confirmação.
*   **Confirmação de envio:** diálogo "Finalizar simulado?" avisando a quantidade de questões em branco ("Você ainda tem 32 questões em branco. Elas serão contabilizadas como erro. O envio não pode ser desfeito."), com os botões "Voltar" e "Confirmar envio".
#### 2.5 Resultado do Simulado (Referência UC-03 / RF-08)
*   Cards **Acertos totais** (ex.: 3/35), **Formação Geral** (x/8) e **Conhecimento Específico** (x/27), cada um com o percentual de acertos.
*   Aviso de que as questões não respondidas foram contabilizadas como erro e de que o resultado foi registrado no histórico.
*   Botões **"Ver gabarito oficial e comentado"** e **"Meu Desempenho"**.
#### 2.6 Revisão da Questão: Gabarito Comentado e Fórum (Referência UC-04 e UC-05 / RF-09 e RF-11)
*   Enunciado com a alternativa marcada pelo estudante em destaque e o quadro **"Gabarito oficial demonstrativo"** com a alternativa correta e o resultado ("Sua resposta: A · Erro" ou "Sem resposta registrada").
*   Seção expansível **"Gabarito comentado / Explicação do Professor"**.
*   Painel **"Fórum da Questão"** com os comentários (nome, perfil e data), campo "Sua contribuição" e botão **"Publicar Comentário"**.
*   Navegação "Questão anterior" e "Próxima questão" entre as questões do simulado.
#### 2.7 Meu Desempenho (Referência UC-06 / RF-13)
*   Cards **Média geral de acertos**, **Questões respondidas** e **Simulados concluídos**.
*   Gráfico **"Acertos por componente"** (Formação Geral e Conhecimento Específico).
*   Gráfico **"Evolução por simulado"**, com uma barra por simulado concluído, em ordem cronológica.
### 3. Perfil Professor (Referência UC-06 / RF-14)
*   Menu: **Desempenho das Disciplinas**, **Banco de Questões** e **Sair da demonstração**.
*   **Desempenho das Disciplinas:** filtro por **Área vinculada**, cards de Média geral, Adesão e Simulados analisados, gráfico de acertos por componente e lista de **tópicos com maior índice de erro**. A tela traz o aviso de que os dados são agregados e anonimizados.
### 4. Perfil Coordenador (Referência UC-06 / RF-14)
*   Menu: **Painel Institucional** e **Sair da demonstração**.
*   **Painel Institucional do Curso:** filtros de **Curso** e **Semestre**, cards de **Média geral**, **Adesão** e **Simulados analisados**, gráfico **"Acertos por componente"** (Formação Geral e Conhecimento Específico) e lista **"Tópicos com maior índice de erro"** em ranking com o percentual de erro de cada tópico.
*   **Privacidade (`RN-05` / LGPD):** a tela informa que os dados são agregados e que nenhum estudante é identificado ("Visualização demonstrativa anonimizada").
### 5. Perfil Administrador (Referência UC-07 / RF-15)
*   **Importar Provas INEP** (Gestão de conteúdo): campos Ano da edição, Área / curso, **Prova estruturada (JSON)** e **Gabarito oficial (JSON)**, nota do formato esperado (são exigidas 35 questões e 35 respostas) e botão **"Processar e Pré-visualizar"**.
*   A tela informa que se trata de uma pré-visualização conceitual e que nenhum arquivo é enviado ao INEP.
*   **Validação:** ao processar arquivos fora do formato esperado, o sistema interrompe a importação e exibe "Importação interrompida. Corrija as inconsistências antes de publicar.", listando os problemas (ex.: "A prova deve conter exatamente 35 questões" e "O gabarito deve conter exatamente 35 respostas").
### 6. Versão Celular (RNF-06)
*   O menu vira o ícone "hambúrguer", que abre uma gaveta de navegação; cards e indicadores são empilhados em coluna única; botões têm largura total e área de toque ampliada.
*   No simulado, o cronômetro permanece no cabeçalho e o mapa de questões abre em gaveta pelo botão "Mapa".
---
 
## 🕹️ Roteiro do Protótipo Navegável (Fluxo de Interação)
 
Para a apresentação do projeto (Critério de Avaliação P2), a jornada principal do aluno é:
 
1. Na tela de acesso, escolher **"Estudante"** em "Explorar como" e clicar em **"Explorar protótipo"**.
2. No **Início**, clicar em **"Iniciar Novo Simulado"**.
3. Em **Configurar simulado**, escolher ano e área e clicar em **"Começar Simulado"**.
4. No ambiente do simulado, marcar alternativas, navegar pelas questões ou pelo **Mapa de questões** e clicar em **"Finalizar Simulado"**.
5. Na confirmação, ler o aviso de questões em branco e clicar em **"Confirmar envio"**.
6. Em **Seu resultado**, ver os acertos por componente e clicar em **"Ver gabarito oficial e comentado"**.
7. Na revisão, abrir a explicação do professor e publicar um comentário no fórum.
8. Abrir **Meu Desempenho** para ver os indicadores e a evolução por simulado.
Jornadas complementares: **Banco de Questões** (filtrar e abrir uma questão) e os perfis **Professor**, **Coordenador** e **Administrador**, escolhidos na tela de acesso.
 
---
 
## 🔎 Rastreabilidade: Protótipo × Requisitos
 
| Requisito / Caso de Uso | Onde aparece no protótipo | Cobertura |
| :--- | :--- | :--- |
| `UC-01` / `RF-01` — Autenticação SSO | Tela de Acesso Institucional | **Parcial** (o aviso descreve o SSO Google/UOL com `@unifor.br`, mas o protótipo não autentica; o erro para conta fora do domínio não foi desenhado) |
| `UC-01` / `RF-02` — Controle de acesso por perfil | Campo "Explorar como" e menus distintos por perfil | **Atendido** |
| `UC-02` / `RF-03` — Pesquisa e filtragem de questões | Banco de Questões | **Atendido** (filtros, contador, limpar filtros e estado vazio) |
| `UC-02` / `RF-04` — Resolução avulsa | Abrir questão no Banco | **Atendido** |
| `UC-03` / `RF-05` — Configuração de simulado | Configurar simulado | **Atendido** |
| `UC-03` / `RF-06` — Cronômetro e mapa de questões | Ambiente do Simulado | **Atendido** |
| `UC-03` / `RF-07` — Submissão manual e automática | Confirmação de envio | **Parcial** (confirmação com alerta de questões em branco demonstrada; o envio automático ao zerar o cronômetro não foi demonstrado) |
| `UC-03` / `RF-08` — Apuração e histórico | Resultado do Simulado | **Atendido** (total e por componente, com registro no histórico) |
| `UC-04` / `RF-09` — Gabarito oficial e comentado | Revisão da Questão | **Atendido** |
| `UC-04` / `RF-10` — Cadastro e edição do comentário pelo professor | — | **Não demonstrado** |
| `UC-05` / `RF-11` — Fórum da questão | Fórum da Questão | **Atendido** |
| `UC-05` / `RF-12` — Moderação de comentários | — | **Não demonstrado** |
| `UC-06` / `RF-13` — Dashboard do estudante | Início e Meu Desempenho | **Atendido** |
| `UC-06` / `RF-14` — Dashboard docente e institucional | Desempenho das Disciplinas e Painel Institucional | **Parcial** (filtros por área, curso e semestre; não há filtro por edição do simulado) |
| `UC-07` / `RF-15` — Importação de provas do INEP | Importar Provas INEP | **Parcial** (formulário e validação com mensagem de erro demonstrados; pré-visualização de uma importação válida, ajuste manual, publicação e alerta de prova duplicada não demonstrados) |
| `RNF-06` — Web responsiva com compatibilidade para celular | Visualização Desktop e Celular | **Atendido** |
 
---
 
## ⚠️ Escopo e Limitações do Protótipo
 
*   Os dados (indicadores, resultados, comentários, painéis de professor e coordenador) são **fictícios**; os painéis agregados não derivam das respostas registradas no protótipo.
*   O protótipo não autentica usuários e não envia dados a nenhum servidor.
*   A persistência real do progresso, a sincronização do cronômetro com o servidor (`RNF-04`) e o desempenho (`RNF-03`) pertencem à implementação.
*   Os itens marcados como **Parcial** ou **Não demonstrado** na matriz são evoluções previstas para o protótipo.
 
