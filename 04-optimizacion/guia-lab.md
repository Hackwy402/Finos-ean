# Guía de Laboratorio · Sesión 4

## Optimización — Encuentra el desperdicio y calcula el ahorro

**Curso 88-EAN · FinOps y Optimización de Costos Cloud** · Duración: 1 hora
Plataforma: **Microsoft Azure** (cuenta *Azure for Students*) + **Pricing Calculator**

> Hoy aplicas el playbook de optimización: **eliminar → ajustar → comprometer**.
> Buscas desperdicio en tu cuenta, simulas un rightsizing y calculas cuánto ahorra
> una reserva. El objetivo: pagar lo justo por el valor que necesitas.

---

## 0. Requisito

Tu cuenta **Azure for Students** activa. Entra a
**[portal.azure.com](https://portal.azure.com)**.

> ⚠️ La cuenta de estudiante **no permite comprar reservas/savings plans** reales
> (necesita permisos de facturación). Por eso las Partes 2 y 3 se hacen con la
> **calculadora de precios** — que es como se DECIDE en la vida real, antes de
> comprometer dinero.

---

## Parte 1 · Caza el desperdicio (20 min)

1. Abre **Azure Advisor** (búscalo en el portal) → pestaña **Cost** (Costo).
   - En una cuenta con pocos recursos habrá pocas recomendaciones; lee las que
     aparezcan y fíjate en el **ahorro estimado** de cada una.
2. Abre **Cost Management → Cost analysis** y agrupa por **Resource** (recurso).
   Pregúntate por cada uno: **¿esto genera valor o es desperdicio?**
3. Busca los sospechosos habituales (aunque sea de forma teórica en tu cuenta):
   - **Discos sin conectar** (unattached): busca "Disks" y mira la columna de VM
     asociada. Un disco sin VM = huérfano.
   - **IPs públicas sin asociar**.
   - **Recursos en grupos que creías borrados** (los de labs anteriores: ¡bórralos!).

> ✍️ **Anota:** ¿qué recomendaciones te dio Advisor y con qué ahorro? ¿Encontraste
> algún recurso que puedas eliminar hoy mismo?

---

## Parte 2 · Simula un rightsizing (20 min)

Con la **[calculadora de precios](https://azure.microsoft.com/pricing/calculator/)**:

1. Agrega una **Virtual Machine** "sobredimensionada": tamaño **D4s_v5**
   (4 vCPU, 16 GB), Linux, East US, 730 h/mes. Anota el costo mensual.
2. Ahora imagina que midieras su uso y la CPU está al **10%**. La bajas a
   **B2s** (2 vCPU, 4 GB). Cambia el tamaño y anota el nuevo costo.
3. Calcula: **ahorro mensual = costo_grande − costo_correcto**, y el **% de ahorro**.

> ✍️ **Anota:** el costo antes, después, el ahorro en $ y en %. Esto es rightsizing:
> el mismo trabajo, pagando por lo que de verdad se usa.

---

## Parte 3 · Calcula el ahorro de una reserva (20 min)

Para una VM **estable (24/7)**, comprometerse 1 o 3 años da un gran descuento.

1. En la calculadora, con una VM (p. ej. **B2s**, East US, 730 h):
   - Anota el precio **Pay as you go** (on-demand).
   - Cambia la opción de precio a **Reserved (1 año)** y luego **Reserved (3 años)**.
     (En la calculadora aparece como "Savings options" / "Reserved instances".)
2. Compara los tres precios y calcula el **% de ahorro** de cada reserva vs on-demand.
3. Reflexiona: ¿para qué tipo de carga tiene sentido cada opción?
   (24/7 fija → reserva; estable pero flexible → savings plan; variable/temporal →
   on-demand; ambiente de prueba → **apágalo**, no lo reserves.)

> ✍️ **Entregable de la sesión:** en tu bitácora, arma una mini-tabla con:
> recurso, precio on-demand, precio reservado 1 año, precio reservado 3 años, y el
> % de ahorro. Concluye qué recomendarías para una VM de producción 24/7.

---

## Checklist de la sesión

- [ ] Revisé Advisor (Cost) y entiendo sus recomendaciones con su ahorro estimado.
- [ ] Busqué desperdicio (discos/IPs/recursos ociosos) en mi cuenta.
- [ ] Calculé el ahorro de un rightsizing (VM grande → VM correcta).
- [ ] Comparé on-demand vs reserva 1/3 años y calculé el % de ahorro.
- [ ] Eliminé los recursos de labs anteriores que seguían encendidos.

**Para la Sesión 5:** trae identificado al menos un recurso optimizable. Cerraremos
con **gobierno** (Azure Policy), cultura FinOps, madurez y KPIs — para que el ahorro
sea sostenible y no se pierda con el tiempo.
