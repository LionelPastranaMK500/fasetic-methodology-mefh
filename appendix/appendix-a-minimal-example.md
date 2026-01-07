# Apéndice A — Ejemplo Mínimo de Implementación (EMI)

Este apéndice presenta la demostración más pequeña posible de que la  
**Metodología Fasética de Ejecución Horizontal (MEFH)** puede aplicarse sin contradicciones estructurales.

El EMI **no es un tutorial**, ni una guía de código, ni una implementación de referencia.
Es un **mapa de ruta abstracto** que valida el cumplimiento del modelo fasético en su forma más simple.

---

## Propósito del EMI

- Evitar interpretaciones creativas del modelo (“yo lo entendí distinto”).
- Proveer un anclaje técnico claro sin depender de lenguajes o frameworks.
- Demostrar separación estricta de fases, contratos explícitos y cierre técnico.

---

## Sistema de Ejemplo

**Sistema:** Servicio de Autenticación  
**Nivel:** Abstracto  
**Vector de Ejecución:** Backend-First

---

## A. Backend (Vector Backend-First)

### Fase 1 — Persistencia

**Objeto:** `UserTable`  
**Campos:**

- `id`
- `email`
- `password_hash`
- `created_at`

Responsabilidad exclusiva:  
Almacenamiento e integridad del dato.

---

### Fase 2 — Contrato

**Objeto:** `UserDefinition`  
**Tipos:**

- `id: UUID`
- `email: string`

Responsabilidad exclusiva:  
Definir la estructura formal de datos expuestos al sistema.

---

### Fase 3 — Lógica de Negocio

**Función:** `authenticateUser(credentials)`  
**Retorno:** `UserDefinition | Error`

Responsabilidad exclusiva:  
Validación de credenciales y reglas de autenticación.  
No conoce transporte ni UI.

---

### Fase 4 — Comunicación

**Endpoint:** `POST /auth/login`  
**Input:** `credentials`  
**Output:** `UserDefinition` (JSON)

Responsabilidad exclusiva:  
Exposición de la lógica como interfaz de comunicación.  
Cero lógica de negocio.

---

## B. Frontend

### Fase 1 — Contrato Espejo

**Objeto:** `UserDTO`  
**Tipos:**

- `id: string`
- `email: string`

Nota:  
Copia estructural exacta de `UserDefinition`.

---

### Fase 2 — Comunicación

**Servicio:** `authService.login()`

Responsabilidad exclusiva:  
Transporte de datos entre Frontend y Backend.  
No procesa ni decide.

---

### Fase 3 — Lógica / Estado

**Hook / Store:** `useAuth()`

Responsabilidad exclusiva:  
Gestión del estado de sesión y reglas de uso en el cliente.  
Testeable sin UI.

---

### Fase 4 — UI

**Componente:** `LoginForm`

Responsabilidad exclusiva:  
Consumir la lógica existente y renderizar visualmente el resultado.  
No contiene reglas de negocio.

---

## Declaración de Cumplimiento Fasético

Este ejemplo cumple al **100%** con la Metodología Fasética:

- No existe mezcla de fases.
- Los contratos son explícitos y estables.
- La lógica está completamente aislada.
- La UI no actúa como fuente de verdad.
- Cada fase puede cerrarse técnicamente.

El ejemplo demuestra que el modelo puede ejecutarse de forma coherente,
independientemente del stack tecnológico utilizado.
