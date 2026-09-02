# Guía de Laboratorio · Sesión 3

## Presupuestos y alertas — Que el sistema te avise antes de la factura

**Curso 88-EAN · FinOps y Optimización de Costos Cloud** · Duración: 1 hora
Plataforma: **Microsoft Azure** (cuenta *Azure for Students*)

> En la S1 viste el gasto y en la S2 lo asignaste por área. Hoy le pones un
> **límite** y **alertas**: creas un presupuesto con avisos escalonados y entiendes
> el **forecast**. El objetivo es enterarte ANTES, no a fin de mes.

---

## 0. Requisito

Tu cuenta **Azure for Students** activa. Entra a
**[portal.azure.com](https://portal.azure.com)** → busca **Cost Management + Billing**.

> Un presupuesto **no gasta crédito**: es solo una regla de aviso. Lo puedes dejar
> creado sin costo.

---

## Parte 1 · Crea un presupuesto (20 min)

1. En **Cost Management** → **Budgets** (Presupuestos) → **+ Add** (Agregar).
2. Configura:
   - **Name:** `budget-lab-mensual`
   - **Reset period:** **Monthly** (mensual)
   - **Creation/Expiration date:** deja las de por defecto.
   - **Amount (Monto):** un número bajo para que sea fácil de "alcanzar" en la demo,
     p. ej. **$5 USD** (o el que quieras vigilar).
   - **Scope / Filter (opcional):** si hiciste el lab de la S2, filtra por
     `Tag → centro-de-costo = pensiones` para presupuestar SOLO esa "área". Si no,
     déjalo a nivel de la suscripción.
3. **Next** para pasar a las alertas.

> ✍️ **Anota:** ¿a qué alcance le pusiste el presupuesto? ¿Por qué tiene sentido
> presupuestar por etiqueta y no solo el total?

---

## Parte 2 · Configura las alertas escalonadas (25 min)

En la pantalla de **Set alerts**:

1. Agrega **tres umbrales** (Alert conditions), tipo **Actual** (gasto real):
   - **50 %** del presupuesto
   - **80 %** del presupuesto
   - **100 %** del presupuesto
2. En **Alert recipients (email):** pon tu correo. (En un entorno real, cada umbral
   escalaría a una persona distinta: 50% al equipo, 80% al dueño, 100% al dueño +
   finanzas.)
3. **Create** (Crear).

Revisa lo que acabas de construir y responde en tu bitácora:
- ¿Qué diferencia hay entre una alerta de tipo **Actual** y una de tipo
  **Forecasted** (proyectada)? (Pista: una avisa por lo ya gastado; la otra, por lo
  que se PROYECTA gastar.)
- ¿Por qué es mejor tener 3 umbrales que una sola alerta al 100%?

> 💡 **Opcional (avanzado):** en vez de solo correo, un umbral puede disparar un
> **Action Group** (Teams, webhook, una automatización que apague recursos). Es el
> puente hacia el gobierno de la S5.

---

## Parte 3 · Lee el forecast (15 min)

1. Ve a **Cost Management → Cost analysis**.
2. En la vista, cambia el gráfico a una que muestre **Actual + Forecast** (o
   selecciona el rango "This month" — Azure dibuja la proyección punteada).
3. Observa:
   - La línea **real** (lo gastado hasta hoy).
   - La **proyección** (a cuánto cerrarías el mes al ritmo actual).
   - Si la proyección **cruza** tu presupuesto, es la señal de actuar.

> **Nota:** una cuenta nueva tiene poco historial, así que el forecast puede ser
> aproximado o casi plano. Lo importante hoy es **entender qué representa** y dónde
> leerlo, no el número exacto.

> ✍️ **Entregable de la sesión:** en tu bitácora, describe el presupuesto que
> creaste (alcance, monto, umbrales, destinatarios) y explica, con tus palabras,
> cómo este montaje evita una "factura sorpresa".

---

## Checklist de la sesión

- [ ] Creé un presupuesto mensual (con alcance total o por etiqueta).
- [ ] Configuré alertas escalonadas 50/80/100% con destinatario.
- [ ] Entiendo la diferencia entre alerta **Actual** y **Forecasted**.
- [ ] Ubiqué la **proyección** en Cost Analysis y sé interpretarla.

**Para la Sesión 4:** deja el presupuesto creado. Trabajaremos **optimización**:
rightsizing, apagar lo ocioso, eliminar desperdicio y comprar con descuento
(reservas y savings plans) — el CÓMO reducir el gasto que las alertas te señalan.
