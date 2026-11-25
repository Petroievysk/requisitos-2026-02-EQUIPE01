# 🎓 Prepara ENADE — UNIFOR
 
> **Projeto de Extensão: Engenharia de Requisitos Aplicada ao Contexto Educacional**
 
Este repositório reúne os artefatos de **elicitação de requisitos, modelagem UML, especificação formal e prototipação** da plataforma **Prepara ENADE**, um sistema web de preparação para o Exame Nacional de Desempenho dos Estudantes (ENADE). O trabalho foi desenvolvido como requisito de avaliação da disciplina de **Requisitos e Modelagem de Sistemas** do curso de Análise e Desenvolvimento de Sistemas (ADS) da Universidade de Fortaleza (UNIFOR).
 
## 📋 Sobre o Projeto
 
O ENADE é um componente curricular obrigatório e um indicador fundamental da qualidade do ensino superior brasileiro. Na prática, os estudantes se preparam com PDFs soltos de provas anteriores, sem simulação do tempo de prova e sem retorno sobre o próprio desempenho. Já a coordenação e os professores não enxergam, antes do exame, em quais áreas há mais dificuldade.
 
O **Prepara ENADE** propõe um ambiente único de preparação, que oferece:
 
- 📚 **Banco de questões:** consulta por ano, área/curso, componente (Formação Geral ou Conhecimento Específico) e palavra-chave.
- ⏱️ **Simulados:** provas de 35 questões (8 de Formação Geral e 27 de Conhecimento Específico) com cronômetro de 4 horas e envio automático ao fim do tempo.
- 💬 **Gabaritos comentados e fóruns:** explicação elaborada por professores e discussão vinculada a cada questão.
- 📊 **Dashboards de desempenho:** painéis individuais para o estudante e painéis agregados e anonimizados para professores e coordenadores.
## 🎯 Escopo e Decisões do Projeto
 
- **Plataforma exclusivamente web:** o sistema é acessado pelo navegador, com layout **responsivo** para celulares e tablets. Não há aplicativo nativo.
- **Acesso institucional:** o login é feito por SSO (Google Workspace / UOL) e restrito a contas `@unifor.br`. Isso permite identificar o perfil de cada usuário, garantir a autoria dos comentários e proteger os dados de desempenho conforme a **LGPD**, sem armazenar senhas.
- **Projeto conceitual:** esta etapa cobre documentação, arquitetura e prototipação. Não há implementação de código-fonte do sistema.
- **Conteúdo:** as questões oficiais vêm das provas públicas do INEP, e a fonte é sempre preservada. No protótipo, os enunciados são fictícios.
## 👥 Perfis de Usuário
 
| Perfil | O que faz no sistema |
| :--- | :--- |
| **Estudante** | Resolve simulados e questões avulsas, consulta gabaritos comentados, participa do fórum e acompanha o próprio desempenho. |
| **Professor** | Comenta gabaritos, modera o fórum e analisa o desempenho agregado das disciplinas. |
| **Coordenador de Curso** | Consulta indicadores agregados e anonimizados por curso e semestre. |
| **Administrador** | Importa provas e gabaritos do INEP e mantém o catálogo de questões. |
 
## ✨ Funcionalidades
 
| ID | Funcionalidade | Prioridade |
| :--- | :--- | :--- |
| **F-01** | Autenticação via SSO institucional | Essencial |
| **F-02** | Banco de questões com filtros | Essencial |
| **F-03** | Simulados cronometrados | Essencial |
| **F-04** | Gabarito comentado | Essencial |
| **F-05** | Fórum por questão | Média |
| **F-06** | Painéis de desempenho | Essencial |
| **F-07** | Importação de provas do INEP | Essencial |
 
## 📂 Estrutura do Repositório
 
```text
.
├── README.md
└── docs/
    ├── 01_visao_e_requisitos.md
    ├── 02_diagramas_uml.md
    ├── 03_srs_ieee_830.md
    └── 04_prototipos.md
```
 
## 🧩 Entregáveis
 
### Trabalho P1 — Elicitação e Modelagem Inicial
* **[Documento de Visão, Stakeholders e Requisitos](docs/01_visao_e_requisitos.md):** problema, objetivos, partes interessadas, atores, necessidades, funcionalidades priorizadas e regras de negócio, com base em pesquisa exploratória e análise documental.
* **[Modelagem UML](docs/02_diagramas_uml.md):** diagramas de Casos de Uso, Componentes e Implantação e mapa da jornada do estudante, em sintaxe Mermaid.
### Trabalho P2 — Especificação Formal e Prototipação
* **[Especificação de Requisitos (SRS)](docs/03_srs_ieee_830.md):** documento no padrão IEEE 830 com requisitos funcionais (RF-01 a RF-15), regras de negócio (RN-01 a RN-05), requisitos não-funcionais (RNF-01 a RNF-07), casos de uso detalhados (UC-01 a UC-07) e matriz de rastreabilidade.
* **[Protótipos de Interface](docs/04_prototipos.md):** descrição das telas do protótipo web interativo para os quatro perfis, com a cobertura dos requisitos.
## 🖥️ Protótipo Interativo
 
- **Acesse:** [Protótipo web Prepara ENADE (Canva)](https://gazelle-853dkc.my.canva.site/)
- Na tela inicial, escolha o perfil em **"Explorar como"** (Estudante, Professor, Coordenador ou Administrador) e clique em **"Explorar protótipo"**. Não há autenticação real e todos os dados são fictícios.
- Jornada sugerida para o Estudante: **Iniciar Novo Simulado → Começar Simulado → Finalizar → Ver gabarito comentado → Meu Desempenho**.
- O protótipo pode ser visualizado em Desktop e em Celular.
## 🔗 Rastreabilidade
 
Os artefatos usam identificadores que se conectam entre si: **Necessidade (NEC) → Funcionalidade (F) → Caso de Uso (UC) → Requisito Funcional (RF) → Tela do protótipo**. A matriz completa está na seção 4 do [SRS](docs/03_srs_ieee_830.md), e a cobertura dos requisitos pelo protótipo está em [Protótipos de Interface](docs/04_prototipos.md).
 
## 🛠️ Tecnologias e Ferramentas Utilizadas
 
* **Markdown & Mermaid:** documentação estruturada e diagramas UML renderizados nativamente no GitHub.
* **Canva:** construção e publicação do protótipo web interativo.
* **GitHub Projects (Kanban):** gestão ágil do *backlog* e rastreabilidade de *issues*.
## 👨‍💻 Autores e Colaboradores
 
* **Diego Rodrigues** – [@Petroievysk](https://github.com/Petroievysk)
* **José Guilherme** – [@DrwGuikkz](https://github.com/DrwGuikkz)
## 🎓 Orientação
 
* **Professor Responsável:** Marcelo Bezerra ([@marcelobezerra-dotcom](https://github.com/marcelobezerra-dotcom))
* **Instituição:** Universidade de Fortaleza (UNIFOR) – Semestre 2026.2
 
