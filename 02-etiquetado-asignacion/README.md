# Sesión 2 · Etiquetado, organización y asignación de costos

Segunda sesión (fase **Informar**): del gasto total a saber **de quién es cada
peso**. Organizas los recursos (jerarquía), los **etiquetas** (tags) y repartes el
costo por área/proyecto con **showback**.

## Objetivos

- Organizar recursos con la jerarquía de Azure (grupos de gestión → suscripción →
  grupo de recursos → recurso).
- Diseñar una **estrategia de etiquetado** (pocas etiquetas, obligatorias, consistentes).
- Agrupar el costo por etiqueta en **Cost Analysis** y hacer **showback**.
- Distinguir **showback vs chargeback** y entender el costo huérfano/compartido.

## Contenido

```
02-etiquetado-asignacion/
├── guia-lab.md                 # laboratorio (participantes)
├── diapositivas/               # deck de teoría (PPTX + PDF, 18 láminas) + guía PDF
└── chuleta-docente.md          # (no se publica) facilitación + respuestas
```

## Laboratorio

Ver [`guia-lab.md`](guia-lab.md). Tres partes (1 hora): creas dos "áreas" (grupos de
recursos), etiquetas sus recursos con las claves del curso (`ambiente`,
`centro-de-costo`, `proyecto`), dejas uno sin etiqueta a propósito, y en Cost
Analysis agrupas por etiqueta para repartir el gasto (viendo el costo "(sin etiqueta)").

## Multi-nube y herramientas

Incluye las equivalencias Azure ↔ AWS (Tags ↔ Cost Allocation Tags, Management
Groups ↔ Organizations, Azure Policy ↔ Tag/Service Control Policies) con iconos
oficiales, y esquemas anotados de Cost Analysis (Group by Tag) y de la pantalla de
Tags.

Esta sesión cierra la fase **Informar** del FinOps Framework. Sigue la S3
(presupuestos y alertas por área).
