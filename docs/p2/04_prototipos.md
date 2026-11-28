# Protótipos de Interface — Prepara ENADE

> **Projeto:** Prepara ENADE - UNIFOR
>
> **Sprint:** 2 (Trabalho P2)
>
> **Ferramenta:** Canva (protótipo web interativo), versão **VD 1.3**
>
> **Plataforma:** aplicação exclusivamente web, com layout responsivo (Desktop e Celular)
>
> **Revisão:** 28/11/2026, com base em gravações do protótipo em Desktop. Os itens em **"Pendências"** ainda precisam ser aplicados no Canva.

## 🔗 Links de Acesso

*   **Protótipo Navegável / Apresentação (Canva):** [https://gazelle-853dkc.my.canva.site/](https://gazelle-853dkc.my.canva.site/)

---

## 🧭 Visão Geral do Protótipo

O protótipo é uma **aplicação web interativa com dados fictícios**, que simula os principais fluxos do Prepara ENADE para os quatro perfis do sistema. Como não há aplicativo nativo, todo o acesso ocorre pelo navegador (`RNF-06`).

*   Os enunciados são **demonstrativos** e não correspondem a provas oficiais do INEP; as questões trazem o selo "Inspirada no ENADE · fictícia, não oficial".
*   Os registros demonstrativos **podem ser compartilhados entre visitantes**, e as telas avisam para não informar dados pessoais.
*   Não há autenticação real (SSO) nem integração com o INEP.

## 🎨 Identidade Visual

*   **Marca:** logotipo "Prepara ENADE" com ícone de capelo (formatura).
*   **Paleta:** azul e branco, com tons de azul-gelo para fundos e cards, azul médio para ações principais e azul marinho para títulos.
*   **Tipografia:** Inter (sans-serif).
*   **Princípios de UX:** uma ação principal por tela, espaço em branco, textos curtos, avisos de estado (tempo restante, questão atual, "Salvando...") e confirmação antes do envio do simulado.

---

## 📱 Estrutura das Interfaces

### 1. Acesso Institucional (UC-01 / RF-01 e RF-02)
*   **Elementos:** logotipo, selo "Acesso institucional · Demonstração", título **"Seu preparo começa aqui."**, quadro **"Como seria o acesso institucional"** (Google Workspace / UOL, contas `@unifor.br` previamente cadastradas), campo **"Explorar o perfil de"** e botão **"Explorar protótipo"**.
*   Cada perfil abre uma tela inicial com atalhos e menu próprio.

### 2. Perfil Estudante
Menu: **Início**, **Banco de questões**, **Simulados**, **Meu desempenho**, **Fórum** e **Sair da demonstração**.

| Tela | O que o protótipo mostra | Pendências |
| :--- | :--- | :--- |
| **Início** (UC-06) | Saudação, destaque "Pratique no seu ritmo" e atalhos para Banco de questões e Meu desempenho | — |
| **Banco de questões** (UC-02) | Filtros de ano, área/curso, componente e palavra-chave; "Aplicar filtros", "Limpar filtros", contador e "Abrir questão" | — |
| **Novo simulado** (UC-03) | Ano, área, duração demonstrativa (10 min ou 1 min) e aviso de prova curta | Informar as regras reais: **35 questões (8 FG e 27 CE) e 4 horas** (`RF-05`, `RN-02`) |
| **Ambiente do simulado** (UC-03) | Cronômetro regressivo, componente, 3 questões, "Anterior"/"Próxima", mapa lateral, "Entregar simulado", confirmação com questões em branco e envio automático ("Tempo esgotado") | **Retirar questões autorais do simulado** (`RN-09`) |
| **Resultado** (UC-03) | Acertos, respondidas, aproveitamento, registro da tentativa, "Ver gabarito comentado" e "Ver desempenho" | Separar acertos e percentual de **Formação Geral** e **Conhecimento Específico** (`RF-08`) |
| **Questão e gabarito** (UC-04) | Alternativa marcada, resposta correta, resultado em texto e comentário | Colocar o comentário em seção expansível (`RF-09`) |
| **Fórum** (UC-05) | Lista de questões com contagem de comentários, discussão com nome, perfil e data, e "Publicar comentário" | Exibir também a **hora** (`RF-11`) |
| **Meu desempenho** (UC-06) | Tentativas, questões respondidas, acertos registrados e barra de aproveitamento | Adicionar **média geral**, gráfico **FG × CE** e **evolução por simulado** (`RF-13`) |

### 3. Perfil Professor
Menu: **Visão geral**, **Painel por disciplina**, **Banco de questões**, **Moderar fórum**, **Cadastrar questão**, **Importação INEP** e **Sair da demonstração**.

| Tela | O que o protótipo mostra | Pendências |
| :--- | :--- | :--- |
| **Painel por disciplina** (UC-06) | Curso, disciplina, média, adesão, simulados, comparação por componente, leitura pedagógica e aviso de anonimização | Adicionar **ranking dos tópicos com maior erro**; trocar "Simulados" por **Questões respondidas** e retirar a comparação por componente (`RF-14`) |
| **Cadastrar questão** (UC-10) | Curso, disciplina, componente, ano de referência, enunciado, alternativas A a E, resposta correta, comentário do gabarito e aviso de campo obrigatório | Adicionar **Tópico** e **Imagem** (opcional) (`RF-19`) |
| **Minhas questões** (UC-10) | Não há a tela no menu | Criar lista com disciplina, tópico, data e "Editar" |
| **Banco de questões** (UC-02) | Mesmos filtros do estudante | Selo **"Questão autoral"** com o professor; ação **"Associar à disciplina"** (`RF-20`); "Editar comentário oficial" (`RF-10`); não exibir "Sua resposta" de estudante |
| **Moderar fórum** (UC-05) | Lista de discussões e "Ocultar comentário", com confirmação na tela | Pedir o **motivo** da ocultação (`RF-12`, UC-05) |
| **Importação INEP** (UC-07) | Ano, curso vinculado, arquivos JSON de prova e gabarito, formato esperado e "Validar e pré-visualizar" | Demonstrar erro de validação, pré-visualização com ajuste, publicação e alerta de prova duplicada (`RF-15`) |

### 4. Perfil Coordenador
Menu: **Visão geral**, **Painel do curso**, **Disciplinas** e **Sair da demonstração**.

| Tela | O que o protótipo mostra | Pendências |
| :--- | :--- | :--- |
| **Painel do curso** (UC-06) | Curso, disciplina, média, adesão, simulados, comparação por componente, leitura pedagógica e aviso de anonimização | **Fixar o curso** do coordenador (`RN-08`); opção "Todas" em disciplina; filtros **Semestre** e **Edição do simulado**; **ranking de tópicos**; gráfico por disciplina; rótulo da média conforme o recorte (`RF-14`) |
| **Disciplinas do curso** (UC-09) | Curso, lista de disciplinas, campo de nome, "Cadastrar disciplina" e mensagem de sucesso | **Fixar o curso** (`RN-08`); adicionar **Código**, **Editar** e **Inativar**; erro de código duplicado (`RF-18`) |

### 5. Perfil Administrador
Menu: **Visão geral**, **Cursos**, **Usuários e vínculos** e **Sair da demonstração**.

| Tela | O que o protótipo mostra | Pendências |
| :--- | :--- | :--- |
| **Visão geral** | Atalhos para Cursos, Usuários e vínculos e **Importação INEP** | **Remover o atalho de Importação INEP** e a menção a arquivos de questões no destaque (`RF-15`) |
| **Cursos** (UC-08) | Lista, campo de nome, "Cadastrar curso" e mensagem de sucesso | Adicionar **Código**, **Área do ENADE**, **Editar** e **Inativar** (`RF-16`) |
| **Usuários e vínculos** (UC-08) | Perfis de exemplo, identificador fictício, perfil, curso, disciplina e "Adicionar vínculo demonstrativo" | Nome e **e-mail fictício** `@unifor.br`; mostrar disciplinas só para Professor, com **seleção múltipla**; Editar, Inativar e erros de validação (`RF-17`) |

### 6. Versão Celular (RNF-06)
*   A versão em celular **não foi verificada nesta revisão** (as gravações são de Desktop). Conferir menu recolhível, mapa de questões em gaveta e ausência de rolagem horizontal a partir de 360 px.

---

## 🕹️ Roteiro do Protótipo Navegável (Fluxo de Interação)

Jornada principal do estudante:

1. Escolher **"Estudante"** e clicar em **"Explorar protótipo"**.
2. Abrir **Simulados**, escolher ano, área e duração e clicar em **"Começar simulado"**.
3. Marcar alternativas, navegar pelo mapa e clicar em **"Entregar simulado"**.
4. Em **"Entregar simulado?"**, clicar em **"Confirmar entrega"**.
5. No resultado, abrir **"Ver gabarito comentado"**.
6. Publicar um comentário no **Fórum** e abrir **Meu desempenho**.

Demonstração do envio automático: escolher a duração de **1 minuto** e aguardar a tela **"Tempo esgotado"**.

Jornada de cadastros:

1. **Administrador:** cadastrar um curso e os vínculos.
2. **Coordenador:** cadastrar uma disciplina.
3. **Professor:** cadastrar uma questão, moderar o fórum, abrir a Importação INEP e o painel por disciplina.
4. **Coordenador:** consultar o painel do curso.

---

## 🔎 Rastreabilidade: Protótipo × Requisitos

| Requisito / Caso de Uso | Onde aparece no protótipo | Cobertura |
| :--- | :--- | :--- |
| `UC-01` / `RF-01` — Autenticação SSO | Acesso Institucional | **Parcial** (SSO apenas descrito; sem erro de acesso) |
| `UC-01` / `RF-02` — Controle de acesso por perfil | Menus por perfil | **Parcial** (atalho de importação no Administrador; coordenador escolhe qualquer curso) |
| `UC-02` / `RF-03` — Pesquisa e filtragem | Banco de questões | **Atendido** (estado vazio não verificado) |
| `UC-02` / `RF-04` — Resolução avulsa | Abrir questão | **Atendido** (resultado exibido; a marcação não aparece nas gravações) |
| `UC-03` / `RF-05` — Configuração de simulado | Novo simulado | **Parcial** (não informa 35 questões e 4 horas) |
| `UC-03` / `RF-06` — Cronômetro e mapa | Ambiente do simulado | **Atendido em escala reduzida** (3 questões, 1 ou 10 minutos) |
| `UC-03` / `RF-07` — Submissão manual e automática | Confirmação e Tempo esgotado | **Atendido** |
| `UC-03` / `RF-08` — Apuração e histórico | Resultado | **Parcial** (sem separação por componente) |
| `UC-04` / `RF-09` — Gabarito oficial e comentado | Questão | **Parcial** (comentário sem seção expansível) |
| `UC-04` / `RF-10` — Comentário pelo professor | Cadastrar questão | **Parcial** (comentário só no cadastro; edição não demonstrada) |
| `UC-05` / `RF-11` — Fórum da questão | Fórum | **Parcial** (data sem hora) |
| `UC-05` / `RF-12` — Moderação | Moderar fórum | **Parcial** (oculta sem pedir motivo) |
| `UC-06` / `RF-13` — Dashboard do estudante | Meu desempenho | **Parcial** (sem gráficos por componente e de evolução) |
| `UC-06` / `RF-14` — Dashboard docente e institucional | Painéis por disciplina e do curso | **Parcial** (sem ranking, semestre e edição; curso não restrito) |
| `UC-07` / `RF-15` — Importação do INEP | Importação INEP (Professor) | **Parcial** (formulário demonstrado; processamento não demonstrado) |
| `UC-08` / `RF-16` — Cadastro de cursos | Cursos | **Parcial** (somente nome) |
| `UC-08` / `RF-17` — Usuários e vínculos | Usuários e vínculos | **Parcial** (sem e-mail, edição e múltiplas disciplinas) |
| `UC-09` / `RF-18` — Disciplinas | Disciplinas do curso | **Parcial** (somente nome; curso não restrito) |
| `UC-10` / `RF-19` — Cadastro de questões | Cadastrar questão | **Parcial** (sem tópico e imagem; questão autoral entra no simulado) |
| `UC-10` / `RF-20` — Classificação por disciplina | — | **Não demonstrado** |
| `RNF-06` — Web responsiva | — | **Não verificado nesta revisão** |

---

## ⚠️ Escopo e Limitações do Protótipo

*   Os indicadores dos painéis de professor e coordenador são **fictícios** e não derivam das tentativas registradas.
*   O protótipo não autentica usuários; o desempenho do estudante pode incluir tentativas de outros visitantes.
*   A persistência real, a sincronização do cronômetro com o servidor (`RNF-04`) e o desempenho (`RNF-03`) pertencem à implementação.
 
