# ESPECIFICACIÓN TÉCNICA

## Metodología Fasética de Ejecución Horizontal (MEFH)

**Versión:** 3.0  
**Estado:** Estable  
**Clasificación:** Metodología de Arquitectura y Ejecución de Software  
**Autor:** Andriy Pastrana

---

## 1. Propósito de la Especificación

Este documento define formalmente las **reglas técnicas**, **principios operativos** y **criterios de validez** de la Metodología Fasética de Ejecución Horizontal (MEFH).

Su objetivo es permitir:

- Implementaciones consistentes del modelo
- Auditoría técnica de proyectos que afirman ser “Faséticos”
- Discusión estructurada sin ambigüedad semántica
- Evolución controlada de la metodología

Este documento **no es una guía de gestión**, ni un manual de productividad.

---

## 2. Definición Formal

La Metodología Fasética de Ejecución Horizontal (MEFH) es un modelo de construcción de software basado en:

- Separación estricta de responsabilidades
- Fases horizontales inmutables
- Contratos explícitos como ley estructural
- Validación técnica como único criterio de avance

El progreso se mide por **certeza técnica validada**, no por tiempo, tareas ni entregables visuales.

---

## 3. Principios Innegociables

Una implementación solo puede considerarse MEFH si cumple **todos** los principios siguientes:

### 3.1 Inmutabilidad de Fase

Una fase cerrada no puede ser modificada sin un proceso formal de reapertura.

### 3.2 No Mezclar Responsabilidades

Ninguna fase puede contener lógica, decisiones o dependencias que pertenezcan a otra fase.

### 3.3 Contratos como Ley

Los contratos definen la frontera absoluta entre fases.  
No son sugerencias ni adaptables “por conveniencia”.

### 3.4 Certeza sobre Velocidad

El avance se bloquea ante inconsistencias estructurales, incluso bajo presión temporal.

---

## 4. Fases Horizontales Definidas

### 4.1 Ciclo Backend

1. **Persistencia**  
   Arquitectura de datos, integridad, relaciones y reglas de almacenamiento.

2. **Contratos**  
   Definiciones formales y tipadas que representan los datos del sistema.

3. **Lógica de Negocio**  
   Reglas, validaciones y orquestación.  
   Totalmente agnóstica a UI y transporte.

4. **Comunicación**  
   Exposición de la lógica mediante mecanismos de transporte.  
   Prohibida cualquier lógica de negocio.

---

### 4.2 Ciclo Frontend

1. **Contratos Espejo**  
   Réplica exacta de los contratos del Backend o de la Caja 0.

2. **Conexión**  
   Transporte de datos sin procesamiento visual.

3. **Lógica / Estado**  
   Procesamiento local, reglas de presentación y estado de aplicación.

4. **Integración o Construcción UI**  
   Representación visual del comportamiento definido previamente.

---

## 5. Vectores de Ejecución Permitidos

### 5.1 Vector Frontend-First

- Existe una **Caja 0 (UI/UX)** previa
- La UI es fuente de verdad **visual y funcional esperada**
- No es fuente de verdad de negocio ni datos

Uso recomendado:

- Productos UX-driven
- Software a medida
- Exploración funcional controlada

---

### 5.2 Vector Backend-First

- La estructura de datos gobierna el sistema
- La UI se construye como consecuencia
- Máxima prioridad a integridad y coherencia

Uso recomendado:

- Sistemas críticos
- Fintech
- Plataformas de alta seguridad

---

## 6. Gatekeeping (Cierre de Fase)

El cierre de una fase requiere validación explícita:

- No existe lógica fuera de su fase
- El contrato es completo y estable
- La fase puede probarse de forma aislada

Sin validación, **no hay avance**.

---

## 7. Evolución y Micro-Ciclos

MEFH permite evolución mediante **micro-ciclos faséticos**.

### 7.1 Regla de Impacto

Todo cambio debe clasificarse según las fases que impacta antes de implementarse.

### 7.2 Tipos de Evolución

- **Tipo A:** Evolución Local
- **Tipo B:** Evolución Encadenada
- **Tipo C:** Revisión Estructural Mayor

Si un cambio no puede clasificarse, **no puede ejecutarse**.

---

## 8. Anti-Patrones Críticos

Cualquier implementación que incurra en los siguientes patrones **deja de ser Fasética**:

- Mezcla de fases
- Contratos implícitos
- Avance por presión temporal
- UI como autoridad lógica
- Falsos cierres de fase

---

## 9. Criterio de Validez MEFH

Un sistema puede declararse MEFH únicamente si:

- Todas las fases están identificadas
- Los contratos son explícitos
- Las fronteras son auditables
- El sistema puede evolucionar sin degradación estructural

---

## 10. Alcance de la Especificación

Esta especificación:

✔ Define reglas técnicas  
✔ Permite auditoría estructural  
✔ Es independiente de frameworks

No define:
✘ Herramientas  
✘ Lenguajes  
✘ Metodologías de gestión

---

## 11. Estado del Documento

Este documento representa la **versión estable actual** de MEFH.  
La metodología puede evolucionar, pero **sin romper compatibilidad conceptual** con versiones previas.
