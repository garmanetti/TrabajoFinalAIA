# 📊 Diagrama del Flujo del Workflow

## Diagrama Principal

```mermaid
graph TD
    A[👤 Usuario] --> B[📝 Formulario Web<br/>Email + CV]
    B --> C[🔄 Execute Workflow<br/>TF_SW_Extraccion_Texto]
    
    C --> D{📁 Switch<br/>Tipo de archivo?}
    D -->|🖼️ Imagen| E[🤖 Mistral AI<br/>Extrae texto de imagen]
    D -->|📄 PDF| F[🤖 Mistral AI<br/>Extrae texto de PDF]
    
    E --> G[🧠 AI Agent<br/>Análisis de CV]
    F --> G
    
    G --> H[📊 Genera perfiles<br/>de búsqueda]
    G --> I[📋 Análisis de CV<br/>Fortalezas y mejoras]
    
    H --> J[🔀 SplitOut<br/>Separa perfiles]
    J --> K[🌐 HTTP Request<br/>Búsqueda en RapidAPI]
    
    I --> L[🔗 Merge1<br/>Combina CV + Ofertas]
    K --> L
    
    L --> M[⚙️ Prepara para scoring<br/>Extrae requisitos]
    M --> N[🎯 OpenAI<br/>Calcula compatibilidad]
    
    N --> O[🔗 Merge2<br/>Combina scoring + ofertas]
    O --> P[🎨 Formatea HTML<br/>Genera reporte]
    P --> Q[📧 Gmail<br/>Envía resultados]
    
    Q --> R[✅ Usuario recibe<br/>email con ofertas]
    
    style A fill:#e1f5fe
    style B fill:#f3e5f5
    style C fill:#fff3e0
    style G fill:#e8f5e8
    style N fill:#e8f5e8
    style Q fill:#fce4ec
    style R fill:#e1f5fe
```

## Subworkflow: Extracción de Texto

```mermaid
graph TD
    A[🔄 Execute Workflow Trigger] --> B{📁 Switch<br/>Tipo de archivo?}
    B -->|🖼️ Imagen| C[🤖 Mistral AI<br/>image_url]
    B -->|📄 PDF| D[🤖 Mistral AI<br/>document]
    
    C --> E[📤 Retorna texto extraído]
    D --> E
    
    style A fill:#fff3e0
    style B fill:#f3e5f5
    style C fill:#e8f5e8
    style D fill:#e8f5e8
    style E fill:#e1f5fe
```

## Flujo de Datos Detallado

```mermaid
sequenceDiagram
    participant U as Usuario
    participant F as Formulario
    participant SW as Subworkflow
    participant AI as AI Agent
    participant API as RapidAPI
    participant S as Scoring
    participant E as Email
    
    U->>F: Sube CV + Email
    F->>SW: Execute Workflow
    SW->>AI: Texto extraído
    AI->>AI: Analiza CV
    AI->>F: Perfiles + Feedback
    
    loop Para cada perfil
        F->>API: Busca ofertas
        API->>F: Lista de ofertas
    end
    
    loop Para cada oferta
        F->>S: Datos CV + Oferta
        S->>S: Calcula compatibilidad
        S->>F: Score + Matched skills
    end
    
    F->>E: Genera HTML
    E->>U: Envía reporte
```

## Arquitectura de Componentes

```mermaid
graph TB
    subgraph "Workflow Principal (TF_Main)"
        A[Formulario Web]
        B[Execute Workflow]
        C[AI Agent]
        D[SplitOut]
        E[HTTP Request]
        F[Merge1]
        G[Prepara Scoring]
        H[OpenAI Scoring]
        I[Merge2]
        J[Formatea HTML]
        K[Gmail]
    end
    
    subgraph "Subworkflow (TF_SW_Extraccion_Texto)"
        L[Execute Trigger]
        M[Switch]
        N[Mistral AI Imagen]
        O[Mistral AI PDF]
    end
    
    subgraph "Servicios Externos"
        P[Mistral AI]
        Q[OpenAI]
        R[RapidAPI JSearch]
        S[Gmail API]
    end
    
    B --> L
    L --> M
    M --> N
    M --> O
    N --> P
    O --> P
    
    C --> Q
    H --> Q
    E --> R
    K --> S
    
    style A fill:#f9f9f9
    style L fill:#f0f8ff
    style P fill:#fff0f5
    style Q fill:#fff0f5
    style R fill:#fff0f5
    style S fill:#fff0f5
```

## Estados del Proceso

```mermaid
stateDiagram-v2
    [*] --> Formulario: Usuario accede
    Formulario --> Extraccion: CV subido
    Extraccion --> Analisis: Texto extraído
    Analisis --> Busqueda: Perfiles generados
    Busqueda --> Scoring: Ofertas encontradas
    Scoring --> Formato: Scores calculados
    Formato --> Email: HTML generado
    Email --> [*]: Reporte enviado
    
    Extraccion --> Error: Archivo inválido
    Analisis --> Error: Error de IA
    Busqueda --> Error: API no disponible
    Scoring --> Error: Error de cálculo
    Email --> Error: Error de envío
    
    Error --> [*]: Proceso fallido
```

## Métricas y Monitoreo

```mermaid
graph LR
    A[Workflow Execution] --> B[Logs de n8n]
    A --> C[Métricas de APIs]
    A --> D[Errores y Excepciones]
    
    B --> E[Dashboard de Monitoreo]
    C --> E
    D --> E
    
    E --> F[Alertas]
    E --> G[Reportes]
    
    style A fill:#e3f2fd
    style E fill:#f3e5f5
    style F fill:#ffebee
    style G fill:#e8f5e8
```
