# Glosario Fasético

## Metodología Fasética de Ejecución Horizontal (MEFH)

El presente glosario define de manera **formal, normativa y no ambigua** los términos propios de la Metodología Fasética (MEFH).

Las definiciones aquí expuestas tienen **prioridad semántica** sobre cualquier interpretación externa.  
Cualquier reinterpretación fuera de este marco se considera una **desviación del modelo**.

---

## Anti-Evolución

**Definición:**  
Práctica explícitamente prohibida que introduce cambios saltando fases, contratos o procesos de validación.

**Incluye:**  
Hotfixes informales, parches directos en UI o lógica fuera de micro-ciclos.

**Efecto:**  
La anti-evolución degrada el sistema irreversiblemente, incluso si el cambio “funciona” en lo inmediato.

---

## Anti-Patrón Fasético

**Definición:**  
Desviación sistemática del modelo que compromete la integridad estructural del sistema.

**Naturaleza:**  
Los anti-patrones no son errores aislados, sino prácticas que anulan los beneficios del enfoque fasético  
(ej. mezcla de fases, contratos implícitos, avance por presión temporal).

---

## Caja 0

**Definición:**  
Caja especial y opcional, exclusiva del Vector Frontend-First. Representa el contrato visual y funcional esperado del sistema, validado con el cliente antes de la implementación de lógica real.

**Restricción:**  
La Caja 0 es fuente de verdad visual, pero **nunca** fuente de verdad de negocio, reglas o persistencia.

**Características:**

- Contiene UI estática o mockups funcionales.
- No incluye lógica real ni conexiones productivas.
- Sirve como referencia obligatoria para la integración final del Frontend.

---

## Caja Fasética

**Definición:**  
Unidad lógica de responsabilidad dentro del Modelo de Ejecución por Fases Horizontales.

Una Caja no representa complejidad interna ni tamaño de implementación, sino una **frontera semántica y técnica claramente delimitada**.

**Propiedades Clave:**

- Posee una responsabilidad única.
- Expone contratos claros hacia otras cajas.
- Su implementación interna es irrelevante para las fases adyacentes.
- No permite dependencias implícitas ni fugas de lógica.

---

## Cierre Técnico

**Definición:**  
Estado en el cual una fase o micro-ciclo cumple todas las condiciones de validación y queda congelado hasta una reapertura formal.

**Norma:**  
El cierre técnico es absoluto; no admite excepciones por conveniencia.

---

## Contrato

**Definición:**  
Definición formal y explícita de las estructuras de datos, tipos y expectativas de intercambio entre fases o sistemas.

**Norma:**  
Un contrato es ley dentro del modelo.  
No puede inferirse, improvisarse ni ajustarse informalmente sin reapertura de fase.

---

## Contrato Espejo

**Definición:**  
Réplica exacta de un contrato definido en una fase, implementada en la fase consumidora.

**Propósito:**  
Garantizar sincronía estructural entre productor y consumidor, eliminando interpretaciones implícitas.

**Norma:**  
Cualquier divergencia entre contrato y contrato espejo constituye un error crítico.

---

## Fase Horizontal

**Definición:**  
Etapa estructural del modelo que agrupa Cajas con la misma responsabilidad funcional a lo largo de todo el sistema.

**Característica:**  
Las fases son horizontales porque atraviesan el proyecto completo y no representan momentos temporales, sino capas de responsabilidad técnica.

El avance entre fases está condicionado exclusivamente a **validación técnica**, no a cronogramas.

---

## Gatekeeping (Cierre de Fase)

**Definición:**  
Acto formal de validación que autoriza el paso de una fase a la siguiente.

Sin Gatekeeping explícito, no existe avance legítimo.

**Requisitos de Cierre:**

- Validación de frontera (no mezcla de responsabilidades).
- Integridad mínima funcional.
- Ausencia de dependencias ocultas.

---

## Ley de No Mezclar Responsabilidades

**Definición:**  
Regla suprema de la Metodología Fasética.

Establece que ninguna fase puede contener lógica, decisiones o conocimiento que pertenezcan a otra fase, más allá de su contrato inmediato.

**Consecuencia:**  
La violación de esta ley invalida la implementación como Fasética.

---

## Micro-Ciclo Fasético

**Definición:**  
Re-ejecución controlada de una o más fases horizontales sobre un sistema existente, sin afectar las fases no impactadas.

**Propósito:**  
Permitir evolución sin degradación estructural.  
Constituye el único mecanismo válido de cambio dentro del modelo.

---

## Revisión Estructural Mayor

**Definición:**  
Tipo de evolución que invalida decisiones base del sistema  
(modelo de datos, dominio o arquitectura fundamental).

**Norma:**  
No se permite su implementación como parche.  
Debe tratarse como un nuevo ciclo mayor del proyecto.

---

## Sincronía de Espejo

**Definición:**  
Principio que establece que todo contrato debe existir en versiones equivalentes y sincronizadas en ambos extremos del sistema (Backend y Frontend).

La sincronía no es conceptual; es **estructural y verificable en código**.

---

## Vector de Ejecución

**Definición:**  
Orden estratégico de construcción del sistema que determina el punto de partida y la dirección del desarrollo.

**Vectores Válidos:**

- **Frontend-First:** El diseño visual (Caja 0) actúa como plano maestro funcional.
- **Backend-First:** La estructura de datos y la lógica actúan como cimiento primario.

**Nota:**  
El vector no altera las fases existentes, solo su orden de activación.
