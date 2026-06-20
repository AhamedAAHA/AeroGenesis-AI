# AeroGenesis AI: Full-Stack Architecture



```mermaid

graph TD

    subgraph Frontend_Layer [Frontend: Next.js & Three.js]

        UI[Ops Command Center]

        Twin[3D Digital Twin Visualization]

        WS[WebSocket Real-time Sync]

    end



    subgraph Ingestion_Layer [Data Ingress]

        APIs[External Aviation APIs]

        Kafka[Kafka Event Bus]

    end



    subgraph Orchestration_Layer [Orchestration: Mastra TS]

        Brain[Aviation Brain: Mastra Supervisor]

    end



    subgraph Agent_Swarms [Specialist Swarms]

        direction TB

        Ops[Ops Supervisor] --> Flt[Flight/Gate Agents]

        Pass[Passenger Supervisor] --> Re[Rebooking Agents]

        Sim[Sim Supervisor] --> Wx[Weather/Scenario Agents]

        Safe[Safety Supervisor] --> Comp[Compliance Agents]

        Learn[Learning Supervisor] --> BBox[Black Box Agents]

    end



    subgraph Safety_Audit_Layer [Safety & Audit]

        Enkrypt[Enkrypt AI Safety Layer]

        Audit[Aviation Black Box Service]

    end



    subgraph Memory_Layer [Memory: Qdrant Cluster]

        Graph[(Global Knowledge Graph)]

        Storage[(Black Box Storage)]

    end



    %% Data Flow

    APIs --> Kafka

    Kafka --> Brain

    UI <--> WS

    WS <--> Brain

    

    Brain <--> Agent_Swarms

    Agent_Swarms <--> Graph

    

    Agent_Swarms --> Enkrypt

    Enkrypt --> Audit

    Audit --> Storage

    

    Storage -.-> Twin

    Storage -.-> Learn
