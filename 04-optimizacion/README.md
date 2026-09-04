# Sesión 4 · Optimización: rightsizing, waste, Advisor y compromisos

Cuarta sesión (fase **Optimizar**): el CÓMO reducir el gasto que no genera valor,
sin frenar el negocio. El playbook: **eliminar → ajustar → comprometer**.

## Objetivos

- Eliminar el **desperdicio** (recursos ociosos, discos huérfanos, ambientes olvidados).
- Hacer **rightsizing**: ajustar el tamaño al uso real (ni de más, ni de menos).
- Usar **apagado programado** y **autoescalado** para pagar solo cuando se usa.
- Aprovechar **Advisor** (recomendaciones con ahorro estimado).
- Decidir entre **reservas vs savings plans** para comprar con descuento.

## Contenido

```
04-optimizacion/
├── guia-lab.md                 # laboratorio (participantes)
├── diapositivas/               # deck de teoría (PPTX + PDF, 15 láminas) + guía PDF
└── chuleta-docente.md          # (no se publica) facilitación + respuestas
```

## Laboratorio

Ver [`guia-lab.md`](guia-lab.md). Tres partes (1 hora): cazar desperdicio con Advisor
y Cost Analysis, simular un rightsizing en la calculadora (VM grande → correcta), y
calcular el ahorro de una reserva (on-demand vs 1/3 años). Como la cuenta de
estudiante no permite comprar reservas reales, el análisis se hace con la calculadora
— como se decide en la vida real.

## Multi-nube y herramientas

Equivalencias Azure ↔ AWS (Advisor ↔ Trusted Advisor/Compute Optimizer,
Reservations ↔ Reserved Instances, Savings Plans ↔ Savings Plans) con iconos
oficiales, esquema anotado de las recomendaciones de Advisor, y diagramas de
rightsizing y de reservas vs savings plans.

Regla de oro: **eliminar → ajustar → comprometer**, en ese orden. Optimizar no es
apagar todo, es pagar lo justo por el valor. Sigue la S5 (gobierno y cultura).
