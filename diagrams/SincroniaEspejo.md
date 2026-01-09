sequenceDiagram
    autonumber
    participant BE_DB as F1: Base de Datos
    participant BE_Logic as F2-F3: API & Contrato
    participant Mirror as [ Sincronía de Espejo ]
    participant FE_Logic as F1-F2: Contrato & Comm
    participant FE_UI as F3-F4: Hooks & UI

    Note over BE_DB, BE_Logic: CICLO BACKEND (Origen)
    BE_DB->>BE_Logic: Estructura de Datos Definida
    BE_Logic->>BE_Logic: Generación de Contrato (Interfaces/DTOs)
    
    rect rgb(30, 41, 59)
    Note over BE_Logic, Mirror: FASE CRÍTICA: Exportación de Tipos
    BE_Logic-->>Mirror: Contrato de Datos (JSON/TS)
    Mirror-->>FE_Logic: Réplica Exacta (Espejo)
    end

    Note over FE_Logic, FE_UI: CICLO FRONTEND (Reflejo)
    FE_Logic->>FE_Logic: Mapeo de Tipos Inmutables
    FE_Logic->>FE_UI: Inyección de Lógica con Tipado Estricto
    FE_UI->>FE_UI: Renderizado con Certeza Técnica

    Note blue over Mirror: Garantía MEFH: Si el Backend cambia,<br/>el Frontend rompe en compilación, no en ejecución.