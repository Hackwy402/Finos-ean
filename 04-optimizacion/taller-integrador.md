# Taller integrador · Sesión 4

## Del dato a la decisión — Una propuesta de optimización FinOps

**Curso 88-EAN · FinOps y Optimización de Costos Cloud** · Duración: 45–60 min
Modalidad: en equipos de 2–3 · Herramientas: **Calculadora de precios de Azure**,
**Excel** (dataset de la S3) y el **FinOps Framework** (finops.org/framework)

> Este taller **integra todo el curso** (S1 a S4). No aprendes algo nuevo: APLICAS
> lo visto a un caso realista y produces el entregable que haría un analista FinOps
> de verdad: una **propuesta de optimización** con números y respaldo en el marco.

---

## El escenario

Eres el/la analista FinOps del área de **Pensiones** de una entidad. Tu líder te
pide reducir el costo cloud del área, que viene subiendo. Tienes:

1. El **historial de costos** del área: `datos/costos-maquinas-virtuales.csv`
   (el mismo del ejercicio de forecasting de la S3).
2. El **inventario de recursos** actual: `datos/inventario-recursos-pensiones.csv`
   (8 recursos que suman **$2.590/mes**, el gasto de agosto).
3. Un **presupuesto mensual** del área de **$2.800**.

Tu misión: entregar una **propuesta de optimización de 1 página** que recorra el
ciclo FinOps **Informar → Cuantificar → Optimizar → Operar**, usando las tres
herramientas. Usa la plantilla [`88-EAN_S04_Plantilla-Propuesta.md`](88-EAN_S04_Plantilla-Propuesta.md).

---

## Parte A · INFORMAR — ¿qué está pasando? (10 min)

*(Framework: dominio **Understand Usage & Cost** — Reporting & Analytics, Allocation)*

1. Abre `costos-maquinas-virtuales.csv` en Excel. Responde:
   - ¿Qué **componente** manda el costo (EC2-Instances / EC2-Other / Lambda)?
   - ¿La tendencia sube, baja o es plana?
2. Abre `inventario-recursos-pensiones.csv`. Identifica los **sospechosos**:
   - ¿Cuáles VMs tienen la **CPU muy baja** (sobredimensionadas)?
   - ¿Hay **discos huérfanos**? ¿Un ambiente de **pruebas** encendido 24/7?

> Anota: el costo del área es **$2.590/mes** y todo está etiquetado
> `centro-de-costo = pensiones` (gracias a la S2, sabes que es SUYO).

---

## Parte B · CUANTIFICAR — ¿hacia dónde va? (10 min)

*(Framework: dominio **Quantify Business Value** — Forecasting, Budgeting)*

1. Con el Excel, **proyecta** el gasto de los próximos meses (usa
   `PRONOSTICO.LINEAL`/`TREND`, como en el ejercicio de la S3).
2. Compara la proyección con el **presupuesto de $2.800**:
   - ¿En qué mes la proyección **cruza** el presupuesto?
3. Escribe el **problema en una frase**: «Si no hacemos nada, el área superará su
   presupuesto en ____ ».

---

## Parte C · OPTIMIZAR — ¿qué hacemos? (20 min)

*(Framework: dominio **Optimize Usage & Cost** — Usage Optimization, Rate Optimization)*

Aplica el playbook de la S4 (**eliminar → ajustar → comprometer**) al inventario.
Usa la **[Calculadora de precios](https://azure.microsoft.com/es-es/pricing/calculator/)**
para estimar los costos "después". Llena la tabla de la plantilla con, para cada
recurso: acción propuesta, costo antes, costo después, ahorro.

Guíate por estas decisiones (justifícalas con lo visto):
- **Discos huérfanos** → *eliminar* (no aportan valor). Ahorro = su costo completo.
- **VMs sobredimensionadas** (CPU 12–15%) → *rightsizing* a un tamaño menor. Estima
  el nuevo costo en la calculadora.
- **VM de pruebas 24/7** → *apagado programado* fuera de horario laboral (solo L–V
  8–18). Estima el ahorro por horas (~220 h/mes de 730).
- **VMs de producción estables** → tras el rightsizing, evalúa una **reserva 1 año**
  (compara on-demand vs reservado en la calculadora).
- **Storage y Function** en uso → *mantener*.

Calcula **dos escenarios**:
- **A · Quick wins** (sin compromiso): solo eliminar + rightsizing + apagado.
- **B · Con compromiso**: A + reservar las VMs de producción.

> ¿Cuál recomiendas y por qué? (Pista: A es inmediato y sin riesgo; B ahorra más
> pero exige comprometerse 1 año — decisión de negocio.)

---

## Parte D · OPERAR — ¿cómo lo sostenemos? (10 min)

*(Framework: dominio **Manage the FinOps Practice** — Governance, Policy & Risk; KPIs)*

Optimizar una vez no basta: el gasto vuelve a crecer sin gobierno. Propón:
1. **Dos reglas/políticas** para que el desperdicio no vuelva. Ejemplos:
   - «Todo recurso debe tener etiqueta `centro-de-costo` y `ambiente` (obligatorio)».
   - «Los ambientes de `pruebas` se apagan automáticamente fuera de horario».
   - «Ninguna VM con CPU < 20% por 30 días sin revisión de rightsizing».
2. **Un KPI** para seguir el ahorro en el tiempo (ej.: *costo por trámite*, o
   *% del presupuesto usado*, o *$ de desperdicio detectado/mes*).

---

## Entregable

Completa **`88-EAN_S04_Plantilla-Propuesta.md`** (1 página) con:
1. **Diagnóstico** (Informar): costo actual y qué lo domina.
2. **Riesgo** (Cuantificar): la proyección vs el presupuesto.
3. **Plan** (Optimizar): la tabla de acciones con ahorro, y los 2 escenarios.
4. **Sostenibilidad** (Operar): 2 políticas + 1 KPI.
5. **Mapa al FinOps Framework**: a qué fase y capability corresponde cada parte.

Súbelo o preséntalo en 3 minutos por equipo, según indique el docente.

> **Por qué este taller importa:** un analista FinOps no solo "sabe de nube" — toma
> datos, cuantifica el riesgo, propone acciones con números y las sostiene con
> gobierno, hablando el lenguaje del FinOps Framework. Eso es lo que acabas de hacer.
