# Sesión 3 · Presupuestos, alertas, anomalías y forecasting

Tercera sesión (inicia la fase **Optimizar**): del gasto asignado a **controlarlo
antes de que ocurra**. Presupuestos con alertas escalonadas, detección de anomalías
y forecast. El objetivo: enterarte ANTES, no a fin de mes.

## Objetivos

- Crear **presupuestos (budgets)** por total, grupo de recursos o etiqueta.
- Configurar **alertas escalonadas** (50/80/100%) y escalar al destinatario correcto.
- Entender la **detección de anomalías** (gasto fuera del patrón) frente al budget.
- Leer el **forecast** (proyección de cierre de mes) para anticipar.

## Contenido

```
03-presupuestos-alertas/
├── guia-lab.md                 # laboratorio (participantes)
├── diapositivas/               # deck de teoría (PPTX + PDF, 15 láminas) + guía PDF
└── chuleta-docente.md          # (no se publica) facilitación + respuestas
```

## Laboratorio

Ver [`guia-lab.md`](guia-lab.md). Tres partes (1 hora): crear un presupuesto mensual
(con alcance por etiqueta), configurar alertas escalonadas con destinatario, y leer
la proyección en Cost Analysis. Un presupuesto no consume crédito.

## Multi-nube y herramientas

Equivalencias Azure ↔ AWS (Azure Budgets ↔ AWS Budgets, anomaly alerts ↔ AWS Cost
Anomaly Detection, Azure Monitor ↔ CloudWatch) con iconos oficiales, un esquema
anotado de la pantalla de Budgets, y diagramas de umbrales, anomalía y forecast.

Idea clave: un budget **avisa**, no frena. El control proactivo convierte el gasto
de reactivo (retrovisor) en anticipado (el camino). Sigue la S4 (optimización).
