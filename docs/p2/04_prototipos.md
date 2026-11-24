# Protótipos de Interface — Prepara ENADE

> **Projeto:** Prepara ENADE - UNIFOR
>
> **Sprint:** 2 (Trabalho P2)
>
> **Ferramentas de Design:** Figma (telas) e Canva (publicação do protótipo navegável)
>
> **Plataforma:** aplicação exclusivamente web, com layout responsivo (Desktop e Celular)

## 🔗 Links de Acesso

*   **Protótipo Navegável / Apresentação (Canva):** [https://gazelle-853dkc.my.canva.site/](https://gazelle-853dkc.my.canva.site/)

---

## 🎨 Identidade Visual

O protótipo segue uma identidade limpa, em **azul e branco**, com foco em clareza e pouca poluição visual.

*   **Marca:** logotipo "Prepara ENADE" com ícone de capelo (formatura) e tipografia serifada, apresentado em um cartão no topo da tela de login.
*   **Paleta:** azul marinho (fundos de destaque e títulos), azul royal (ações principais), azul claro (barras de progresso e gráficos), azul-gelo e branco (fundos e cards).
*   **Tipografia:** Inter (Regular, Medium, Semi Bold e Bold).
*   **Princípios de UX aplicados:** uma ação principal por tela, textos curtos, muito espaço em branco, feedback de estado (cronômetro, questão atual, progresso) e rótulos de ação com verbo ("Iniciar novo simulado", "Finalizar simulado").

---

## 📱 Estrutura das Interfaces Desenhadas

Com base no Documento SRS (IEEE 830), as telas foram planejadas para atender aos fluxos primários dos Casos de Uso do perfil **Estudante**. O Prepara ENADE é uma **aplicação exclusivamente web**: não há aplicativo nativo. Cada tela principal possui duas versões do mesmo layout responsivo: *Desktop* e *Celular* (a partir de 360 px).

> **Adaptações para celular (RNF-06):** o menu lateral vira menu recolhível (ícone "hambúrguer") que abre a gaveta "Sua jornada"; cards e indicadores são empilhados em coluna única; botões e alternativas têm área de toque ampliada; o cronômetro permanece fixo no cabeçalho; não há rolagem horizontal.

### 1. Tela de Acesso Institucional (Referência UC-01 / RF-01 e RF-02)
*   **Elementos:** logotipo com capelo, selo "Acesso institucional", título **"Seu preparo começa aqui."**, subtítulo "Simulados, questões e desempenho em um só lugar.", cartão **"Protótipo demonstrativo"**, campo **"Explorar como"** (perfil padrão: *Estudante*), botão em destaque **"Explorar protótipo"** e a nota "Dados fictícios. Não informe dados pessoais neste protótipo."
*   **Aviso institucional (RN-01):** o cartão informa que o acesso real seria feito via Google Workspace / UOL, exclusivamente com conta `@unifor.br`.
*   **Comportamento:** como se trata de uma demonstração, o protótipo **não autentica usuários**: o avaliador escolhe o perfil em "Explorar como" e entra direto na plataforma. Na versão real, essa etapa é substituída pelo SSO institucional.

### 2. Dashboard Inicial do Estudante (Referência UC-06 / RF-13)
*   **Navegação:** menu lateral com *Visão geral*, *Simulados*, *Histórico* e *Desempenho*, além do atalho "Aprenda em conjunto" para os fóruns.
*   **Conteúdo principal:** card de destaque "Treine hoje. Vá mais longe." com o botão primário **"Iniciar novo simulado"**; indicadores (simulados feitos, aproveitamento e horas de estudo); gráfico de barras "Seu desempenho por área" (Formação Geral e Conhecimentos Específicos); card "Último simulado" com o botão "Revisar gabarito".
*   **Observação:** os valores exibidos são ilustrativos.

### 3. Configuração de Simulado (Referência UC-03 / RF-05)
*   **Elementos:** seleção de **Ano da prova** (ex.: 2023) e **Área do conhecimento** (ex.: Análise e Desenvolvimento de Sistemas), botão **"Começar simulado"** e link "Voltar à visão geral".
*   **Aviso (RN-02):** card "Seu treino, no ritmo do ENADE" informando **35 questões · 4 horas** e que, ao fim do tempo, as respostas serão enviadas automaticamente.

### 4. Ambiente de Simulado (Referência UC-03 / RF-06 e RF-07)
*   **Cabeçalho fixo:** nome do simulado, área e **cronômetro regressivo** em destaque.
*   **Corpo:** identificação da questão ("Questão 01 / 35"), enunciado e cinco alternativas (A a E) em *radio buttons*.
*   **Painel "Seu progresso":** mapa de questões numerado de 01 a 35, com destaque para a questão atual, e a mensagem de que as respostas são mantidas ao navegar.
*   **Rodapé:** botões "Anterior" (na primeira questão, "Configuração"), **"Próxima"** e **"Finalizar simulado"**.
*   **Observação:** o protótipo apresenta duas questões navegáveis, com cronômetro estático e conteúdo autoral demonstrativo.

### 5. Gabarito Comentado e Fórum (Referência UC-04 e UC-05 / RF-09 e RF-11)
*   **Resumo do resultado:** card "Simulado concluído" com total de acertos (24 de 35) e percentual (69%).
*   **Resolução:** indicação da alternativa correta com ícone de check e texto, e seção "Explicação do professor".
*   **Fórum "Aprenda em comunidade":** comentários identificados por perfil (Estudante e Professor), campo "Escreva sua dúvida..." e botão "Praticar novamente".

### 6. Versão Celular
*   Telas disponíveis em coluna única: Login, Dashboard, Configuração de Simulado, Ambiente de Simulado (questões 1 e 2) e Gabarito Comentado com Fórum.
*   Menu "hambúrguer" abrindo a gaveta **"Sua jornada"** (Visão geral, Simulados, Histórico e gabarito, Desempenho).

---

## 🕹️ Roteiro do Protótipo Navegável (Fluxo de Interação)

Para a apresentação do projeto (Critério de Avaliação P2), o protótipo publicado no Canva segue a jornada do aluno:

1. O avaliador escolhe o perfil em **"Explorar como"** (padrão: Estudante) e clica em **"Explorar protótipo"** na tela de acesso.
2. É levado ao Dashboard Inicial, onde visualiza os indicadores e o desempenho por área.
3. Clica em **"Iniciar novo simulado"** e passa pela tela de Configuração.
4. Clica em **"Começar simulado"** e entra no Ambiente de Simulado, onde marca alternativas e navega entre as questões.
5. Clica em **"Finalizar simulado"**.
6. O fluxo chega à tela de Gabarito Comentado e Fórum, demonstrando a viabilidade da plataforma. Dali é possível voltar com "Praticar novamente".

> O mesmo roteiro existe nas versões Desktop e Celular, demonstrando a compatibilidade responsiva da plataforma web.

---

## 🔎 Rastreabilidade: Protótipo × Requisitos

| Requisito / Caso de Uso | Tela do protótipo | Cobertura |
| :--- | :--- | :--- |
| `UC-01` / `RF-01`, `RF-02` — Autenticação SSO e perfis | Tela 1: Acesso Institucional | **Parcial** (o aviso descreve o SSO Google/UOL com `@unifor.br`, mas o protótipo não autentica e usa o seletor "Explorar como"; o estado de erro para conta fora de `@unifor.br` não foi desenhado) |
| `UC-03` / `RF-05` — Configuração de simulado | Tela 3: Configuração | **Atendido** |
| `UC-03` / `RF-06` — Execução com cronômetro e mapa | Tela 4: Ambiente de Simulado | **Parcial** (mapa mostra só a questão atual; faltam os estados respondida/em branco; no celular o mapa ainda não aparece como gaveta) |
| `UC-03` / `RF-07` — Submissão manual e automática | Tela 4: botão "Finalizar simulado" | **Parcial** (faltam a confirmação com alerta de questões em branco e a mensagem de tempo esgotado) |
| `UC-03` / `RF-08` — Apuração de resultados | Tela 5: resumo do resultado | **Parcial** (exibe o total; falta a separação por Formação Geral e Componente Específico) |
| `UC-04` / `RF-09` — Gabarito oficial e comentado | Tela 5: resolução e explicação | **Parcial** (falta destacar a alternativa marcada pelo estudante como acerto/erro) |
| `UC-05` / `RF-11` — Fórum da questão | Tela 5: "Aprenda em comunidade" | **Atendido** |
| `UC-06` / `RF-13` — Dashboard do estudante | Tela 2: Dashboard | **Parcial** (faltam o total de questões resolvidas e o gráfico de evolução por simulado) |
| `UC-02` / `RF-03`, `RF-04` — Banco de questões | — | **Não contemplado** no protótipo (item de menu e telas a desenhar) |
| `UC-04` / `RF-10`, `UC-05` / `RF-12`, `UC-06` / `RF-14`, `UC-07` / `RF-15` — Perfis Professor, Coordenador e Administrador | — | **Fora do escopo do protótipo** (a prototipação cobre o perfil Estudante) |

---

## ⚠️ Escopo e Limitações do Protótipo

*   Os dados (indicadores, resultado, comentários) são **ilustrativos** e as questões são autorais, apenas para demonstrar a interface.
*   O cronômetro é estático; a contagem real e a sincronização com o servidor (RNF-04) pertencem à implementação.
*   O protótipo cobre apenas o perfil **Estudante**; as telas de Professor, Coordenador e Administrador são tratadas nos casos de uso do SRS.
*   Os itens marcados como **Parcial** ou **Não contemplado** na matriz acima são evoluções previstas para o protótipo.
