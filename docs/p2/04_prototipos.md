# Protótipos de Interface — Prepara ENADE

> **Projeto:** Prepara ENADE - UNIFOR
> **Sprint:** 2 (Trabalho P2)
> **Ferramenta de Design:** Figma

## 🔗 Links de Acesso
*(Cole aqui o link público do seu arquivo Figma e do protótipo apresentável)*

*   **Figma (Área de Design/Wireframes):** `[INSERIR_LINK_AQUI]`
*   **Figma (Protótipo Navegável / Apresentação):** `[INSERIR_LINK_AQUI]`

---

## 📱 Estrutura das Interfaces Desenhadas

Com base no Documento SRS (IEEE 830), o design das telas foi planejado para atender aos fluxos primários dos Casos de Uso. As seguintes telas de média/alta fidelidade foram criadas para o perfil do **Estudante**:

### 1. Tela de Login Institucional (Referência UC-01)
*   **Elementos:** Logo da Unifor, texto de boas-vindas, botão em destaque "Entrar com Conta Unifor (Google)".
*   **Comportamento:** Tela limpa que direciona para a verificação de identidade.

### 2. Dashboard Inicial do Estudante (Referência UC-06)
*   **Elementos:** Menu lateral de navegação (Visão Geral, Simulados, Histórico, Desempenho).
*   **Conteúdo Principal:** Gráfico de Radar ou Barras mostrando a proficiência do aluno em "Formação Geral" e "Conhecimentos Específicos".
*   **Call-to-Action:** Botão primário "Iniciar Novo Simulado".

### 3. Configuração de Simulado (Referência UC-03)
*   **Elementos:** Dropdowns para selecionar Ano da Prova (Ex: 2021, 2023) e Área do Conhecimento (Ex: Análise e Desenvolvimento de Sistemas).
*   **Aviso:** Card informando as regras ("Você terá 4 horas para responder 35 questões").

### 4. Ambiente de Simulado (Motor de Tempo) (Referência UC-03)
*   **Elementos Críticos:**
    *   **Header fixo:** Cronômetro com contagem regressiva em destaque.
    *   **Corpo:** Texto base/imagem da questão, enunciado e *Radio Buttons* (A, B, C, D, E).
    *   **Rodapé:** Botões de navegação "Anterior", "Próxima" e o botão final "Finalizar Simulado".
    *   **Lateral/Grid:** Mapa de questões (1 a 35) mostrando o status (respondida/em branco).

### 5. Gabarito Comentado e Fórum (Referência UC-04 e UC-05)
*   **Elementos:**
    *   Indicador visual de Erro/Acerto (Vermelho/Verde).
    *   Caixa expansível: "Explicação do Professor" (Gabarito oficial).
    *   Abaixo, a seção "Discussão", contendo um campo de *input* para o aluno escrever sua dúvida e a lista de comentários (estilo rede social acadêmica) de outros alunos e professores.

---

## 🕹️ Roteiro do Protótipo Navegável (Fluxo de Interação)

Para a apresentação do projeto (Critério de Avaliação P2), o protótipo no Figma está linkado seguindo a jornada do aluno:

1. O avaliador clica no botão "Entrar" na tela de Login.
2. É levado ao Dashboard Inicial, onde visualiza os gráficos fictícios.
3. Clica em "Iniciar Novo Simulado", passa pela tela de Configuração.
4. Entra no Ambiente de Simulado, clica em 2 alternativas simulando a resolução.
5. Clica em "Finalizar".
6. O fluxo termina na tela de Gabarito Comentado, provando a viabilidade da plataforma.
