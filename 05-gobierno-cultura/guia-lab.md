# Guía de Laboratorio · Sesión 5 (cierre)

## Gobierno y cultura — Que el ahorro sea sostenible

**Curso 88-EAN · FinOps y Optimización de Costos Cloud** · Duración: 1 hora
Plataforma: **Microsoft Azure** (cuenta *Azure for Students*)

> Cierre del curso. Ya sabes ver, asignar, controlar y optimizar. Hoy lo haces
> **sostenible**: creas una política que previene el desperdicio, defines tus KPIs y
> ubicas a tu organización en el modelo de madurez.

---

## 0. Requisito

Tu cuenta **Azure for Students** activa. Entra a
**[portal.azure.com](https://portal.azure.com)** → busca **Policy**.

> Las políticas **no cuestan**. En Students puedes asignarlas a nivel de tu
> suscripción. Si el efecto **Deny** diera un problema de permisos, usa **Audit**
> (reporta sin bloquear) — el aprendizaje es el mismo.

---

## Parte 1 · Crea una política de etiquetado (25 min)

Vas a exigir que todo recurso tenga la etiqueta `centro-de-costo`.

1. En **Policy** → **Assignments** → **Assign policy**.
2. Configura:
   - **Scope (alcance):** tu suscripción *Azure for Students*.
   - **Policy definition:** busca y elige **"Require a tag on resources"**
     (Requerir una etiqueta en los recursos).
   - **Parámetro Tag Name:** `centro-de-costo`.
   - (La definición estándar usa el efecto **Deny**. Si no tienes permiso para Deny,
     elige una definición de tipo **Audit**, p. ej. *"Audit resources missing tag"*.)
3. **Review + create** → **Assign**.

**Compruébalo:**
4. Intenta crear un recurso **SIN** la etiqueta `centro-de-costo` (p. ej. una Storage
   account, sin agregar tags).
   - Con **Deny:** Azure **bloquea** la creación (verás un error de política).
   - Con **Audit:** te deja crear, pero el recurso aparece **"Non-compliant"**
     (no conforme) en **Policy → Compliance**.
5. Ahora créalo **CON** la etiqueta `centro-de-costo = pensiones`. Debe funcionar.

> ✍️ **Anota:** ¿qué efecto usaste (Deny/Audit)? ¿qué pasó al crear sin etiqueta?
> ¿Por qué una política es mejor que "recordarle a la gente que etiquete"?

---

## Parte 2 · Define tus KPIs (20 min)

Elige **3 KPIs** que tu organización debería seguir y, para cada uno, di de dónde
saldría el dato. Ejemplos (elige o propón los tuyos):

| KPI | De dónde sale el dato |
|---|---|
| % del presupuesto usado (por área) | Cost Management → Budgets |
| % de recursos etiquetados | Policy → Compliance |
| $ de desperdicio eliminado / mes | Advisor + Cost Analysis |
| Costo por trámite (unit economics) | Costo del área ÷ nº de trámites (dato del negocio) |
| % de cobertura de reservas | Cost Management → Reservations |

> ✍️ **Entregable:** tabla con tus 3 KPIs, su fórmula/fuente, y **por qué** cada uno
> le importa a la dirección de tu organización.

---

## Parte 3 · Plan de madurez (15 min)

1. Ubica a tu organización en el modelo **gatear → caminar → correr**:
   - ¿Tiene visibilidad del gasto cloud? ¿etiqueta? ¿presupuesta? ¿optimiza?
     ¿tiene políticas?
2. Define **3 acciones concretas** para avanzar al siguiente nivel (las más
   valiosas y realistas para tu contexto).

> ✍️ **Entregable final:** una frase de compromiso — «En los próximos 3 meses, mi
> organización va a ____, ____ y ____ para madurar su práctica FinOps».

---

## Checklist de la sesión

- [ ] Asigné una política de etiqueta obligatoria (Deny o Audit).
- [ ] Comprobé qué pasa al crear un recurso sin la etiqueta.
- [ ] Definí 3 KPIs con su fuente de datos.
- [ ] Ubiqué a mi organización en el modelo de madurez y definí 3 acciones.

---

## 🎓 Cierre del curso

Recorriste el ciclo completo de FinOps:
**Informar (S1–S2) → Optimizar (S3–S4) → Operar (S5)**. Ahora tienes el marco, las
herramientas (Azure y AWS) y la práctica para llevar la responsabilidad financiera a
la nube de tu organización. **FinOps no es gastar menos: es maximizar el valor de
cada peso.** ¡Gracias y éxitos!
