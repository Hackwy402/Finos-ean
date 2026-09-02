# Ejercicio práctico · Forecasting en Excel

## Proyecta el costo de tus máquinas virtuales

**Curso 88-EAN · FinOps · Sesión 3** · Duración: 20–25 min · Herramienta: **Excel**
(o Google Sheets / LibreOffice Calc)

> Este ejercicio **no necesita cuenta de Azure**. Trabajas con un export real de
> costos (formato AWS Cost Explorer) y haces la proyección tú mismo, para entender
> qué hace por dentro el "forecast" que viste en la herramienta.

---

## 0. El archivo

Abre **`datos/costos-maquinas-virtuales.csv`** en Excel. Es el historial de costo
mensual de las máquinas virtuales de un área, de **sep-2025 a ago-2026** (12 meses):

| Columna | Qué es |
|---|---|
| `Service` | La fecha del mes (o "Service total", que es la suma de cada columna) |
| `EC2-Instances($)` | Costo de las instancias/VMs (el grueso del gasto) |
| `EC2-Other($)` | Discos, transferencia de datos… (costos asociados a las VMs) |
| `Lambda($)` | Funciones serverless (un costo menor) |
| `Total costs($)` | La suma del mes |

> Es el mismo tipo de archivo que exportas desde **Cost Explorer (AWS)** o
> **Cost Analysis → Export (Azure)**. Saber leerlo es parte del trabajo FinOps.

---

## 1. Prepara los datos (5 min)

1. **Borra la fila `Service total`** (fila 2): es un resumen, no un mes. La usaremos
   solo para verificar al final.
2. Deberías quedar con **12 filas de meses** y sus costos.
3. Convierte la primera columna a **fecha** si Excel no lo hizo (Formato → Fecha).

---

## 2. Grafica la tendencia (5 min)

1. Selecciona la columna de **fecha** y la de **`Total costs($)`**.
2. Inserta un **gráfico de líneas**.
3. Observa: el gasto **sube** de ~$980 a ~$2.590 en el año. Esa tendencia es lo que
   vas a proyectar.

---

## 3. Proyecta los próximos 4 meses (10 min)

Agrega en la tabla las filas de **sep, oct, nov y dic de 2026** (sin valor de costo
todavía). Vas a estimarlas de dos formas:

**Opción A — con función (recomendada):**
Usa **`=PRONOSTICO.LINEAL(fecha_nueva; rango_totales_conocidos; rango_fechas_conocidas)`**
(en inglés `FORECAST.LINEAR`, o `TREND`). Por ejemplo, si los totales están en
`E3:E14` y las fechas en `A3:A14`, para septiembre-2026 en `A15`:

```
=PRONOSTICO.LINEAL(A15; E3:E14; A3:A14)
```

Copia la fórmula para los 4 meses. Excel ajusta una recta a tu historial y la
extiende.

**Opción B — a ojo / con línea de tendencia:**
En el gráfico, clic derecho sobre la línea → **Agregar línea de tendencia** →
**Lineal** → marca **"Presentar ecuación"** y **"Extender 4 periodos"**. Verás la
recta proyectada y su fórmula `y = mx + b`.

---

## 4. Compáralo con un presupuesto (5 min)

Supón que el área tiene un **presupuesto mensual de $2.800**.

1. Agrega una columna "Presupuesto" con el valor `2800` en todas las filas.
2. Grafica **Total** + **Proyección** + **Presupuesto** juntos.
3. Responde en tu bitácora:
   - ¿En qué mes tu **proyección** cruza (o se acerca a) el presupuesto de $2.800?
   - Si eso pasara, ¿qué harías HOY con lo aprendido en la sesión (alerta,
     rightsizing, apagar ambientes)?

> Esto es exactamente lo que hace el **forecast** de Cost Analysis / Cost Explorer:
> ajusta tu tendencia y te avisa si vas a superar el límite — para actuar antes.

---

## Entregable

Guarda tu Excel con: el gráfico de la tendencia, los 4 meses proyectados, y una
frase respondiendo cuándo cruzarías el presupuesto y qué acción tomarías. Súbelo o
entrégalo según indique el docente.

> **Dato:** la proyección lineal es la más simple. En la realidad hay estacionalidad
> (fin de año, cierres) y las herramientas usan modelos más finos — pero la idea es
> la misma: **usar el pasado para anticipar el futuro y decidir a tiempo.**
