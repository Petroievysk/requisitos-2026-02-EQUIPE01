# Modelagem UML Inicial — Prepara ENADE

> **Projeto de Extensão — Plataforma de Gestão do Conhecimento e Aprendizagem (ENADE)**
> Artefatos da Sprint 1: Diagramas de Casos de Uso, Componentes e Implantação[cite: 16].

## 1. Diagrama de Casos de Uso

Este diagrama ilustra as interações entre os atores principais (Estudante, Coordenador, Professor e Administrador) e os casos de uso mapeados no Documento de Visão[cite: 15].

```mermaid
flowchart LR
  %% Atores
  EST(["👤 Estudante"])
  COORD(["👤 Coordenador"])
  PROF(["👤 Professor"])
  ADMIN(["👤 Administrador"])
  
  %% Sistemas Externos
  SSO(["🖥️ Autenticação (UOL/Google)"])
  INEP(["🖥️ Portal INEP"])

  %% Fronteira do Sistema
  subgraph SistemaENADE["Sistema Prepara ENADE"]
    UC1(["F-01: Autenticar via SSO"])
    UC2(["F-02: Filtrar Banco de Questões"])
    UC3(["F-03: Realizar Simulado Cronometrado"])
    UC4(["F-04: Acessar Gabarito Comentado"])
    UC5(["F-05: Interagir no Fórum da Questão"])
    UC6(["F-06: Visualizar Painel de Desempenho"])
    UC7(["F-07: Importar Provas e Questões"])
  end

  %% Relacionamentos Estudante
  EST --> UC1
  EST --> UC2
  EST --> UC3
  EST --> UC4
  EST --> UC5
  EST --> UC6

  %% Relacionamentos Coordenador e Professor
  COORD --> UC1
  COORD --> UC6
  PROF --> UC1
  PROF --> UC2
  PROF --> UC5
  PROF --> UC6

  %% Relacionamentos Administrador e Externos
  ADMIN --> UC1
  ADMIN --> UC7
  
  UC1 -. include .-> SSO
  UC7 -. include .-> INEP
```

## 2. Diagrama de Componentes

Descreve a estrutura modular da plataforma e como os subsistemas se comunicam para atender aos requisitos arquiteturais de uma aplicação web/mobile focada na gestão pedagógica[cite: 15, 22].

```mermaid
graph TB
    subgraph Camada_Cliente["🖥️ Camada de Apresentação (Frontend)"]
        UI_Simulado["Módulo de Simulação<br/>(Cronômetro e Questões)"]
        UI_Dashboard["Módulo de Dashboards<br/>(Gráficos de Desempenho)"]
        UI_Forum["Módulo do Fórum<br/>(Comentários e Gabaritos)"]
    end
    
    subgraph Camada_Servidor["⚙️ Camada de Aplicação (Backend API REST)"]
        Auth["Gerenciador de Autenticação"]
        Motor["Motor de Simulados e Correção"]
        Analytics["Motor de Analytics e Estatísticas"]
        Conteudo["Gerenciador de Questões e Importação"]
    end
    
    subgraph Camada_Dados["💾 Persistência de Dados"]
        DB["Banco de Dados Relacional<br/>(Questões, Usuários, Histórico)"]
    end
    
    subgraph Sistemas_Externos["🔗 Integrações Externas"]
        API_SSO["Autenticação Institucional<br/>(UOL / Google)"]
        API_INEP["Fonte de Dados<br/>(Portal INEP)"]
    end
    
    %% Conexões Frontend -> Backend
    UI_Simulado --> Motor
    UI_Dashboard --> Analytics
    UI_Forum --> Conteudo
    UI_Simulado --> Auth
    
    %% Conexões Backend -> Dados
    Auth --> DB
    Motor --> DB
    Analytics --> DB
    Conteudo --> DB
    
    %% Conexões Backend -> Externo
    Auth --> API_SSO
    Conteudo --> API_INEP
```

## 3. Diagrama de Implantação

Representa a infraestrutura física e topológica necessária para hospedar a aplicação web/mobile, garantindo segurança e conformidade com as regras de negócio de proteção de dados[cite: 22].

```mermaid
graph TB
    subgraph Dispositivos_Clientes["📱 Dispositivos Clientes"]
        Mobile["Smartphone / App Mobile<br/>(Estudantes)"]
        Desktop["Navegador Web<br/>(Estudantes, Coordenação, Docentes)"]
    end
    
    subgraph Nuvem_Institucional["🌐 Infraestrutura de Nuvem / Servidores Institucionais"]
        LoadBalancer["Load Balancer<br/>(Distribuição de Tráfego HTTPS)"]
        
        subgraph Cluster_Aplicacao["Cluster de Aplicação"]
            Node1["Servidor Web/API 01<br/>(Node.js / Express)"]
            Node2["Servidor Web/API 02<br/>(Node.js / Express)"]
        end
        
        subgraph Cluster_Banco["Cluster de Dados"]
            DB_Primary["Servidor PostgreSQL<br/>(Primário)"]
            DB_Replica["Servidor PostgreSQL<br/>(Réplica/Backup)"]
        end
    end
    
    subgraph Servicos_Externos["🔗 Serviços de Terceiros"]
        GoogleSSO["Servidor de Identidade<br/>(Google Workspace / UOL)"]
    end
    
    %% Comunicações
    Mobile -- "HTTPS / JSON" --> LoadBalancer
    Desktop -- "HTTPS / JSON" --> LoadBalancer
    
    LoadBalancer --> Node1
    LoadBalancer --> Node2
    
    Node1 -- "TCP/IP (Porta 5432)" --> DB_Primary
    Node2 -- "TCP/IP (Porta 5432)" --> DB_Primary
    DB_Primary -. "Replicação" .-> DB_Replica
    
    Node1 -- "OAuth 2.0 / HTTPS" --> GoogleSSO
    Node2 -- "OAuth 2.0 / HTTPS" --> GoogleSSO
```

## 4. Mapa de Histórias de Usuário (User Journey)

Uma visão cronológica da interação do estudante com o sistema para a realização de um ciclo completo de estudo para o ENADE[cite: 13, 15].

```mermaid
journey
    title Jornada de Preparação do Estudante — Prepara ENADE
    section 1. Acesso e Configuração
      Realizar login institucional (SSO): 5
      Acessar o painel inicial: 4
      Filtrar questões por área/ano: 4
    section 2. Prática (Simulado)
      Iniciar simulado com cronômetro: 5
      Responder questões de formação geral: 3
      Responder questões específicas: 4
      Submeter simulado (ou esgotamento de tempo): 5
    section 3. Feedback e Correção
      Visualizar pontuação imediata: 5
      Consultar o gabarito comentado: 5
      Ler e postar dúvidas no fórum da questão: 4
    section 4. Acompanhamento
      Verificar atualização do dashboard de desempenho: 5
      Comparar resultados por área de conhecimento: 4
```
