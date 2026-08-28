# Guía de Laboratorio · Sesión 2

## Etiquetado y asignación de costos — Ponle nombre y apellido a cada peso

**Curso 88-EAN · FinOps y Optimización de Costos Cloud** · Duración: 1 hora
Plataforma: **Microsoft Azure** (cuenta *Azure for Students*)

> En la S1 viste el gasto total. Hoy lo repartes: creas dos "áreas", etiquetas sus
> recursos y agrupas el costo por etiqueta para responder **¿de quién es cada peso?**

---

## 0. Requisito

Tu cuenta **Azure for Students** activa (de la S1). Entra a
**[portal.azure.com](https://portal.azure.com)**. Ten a la mano las etiquetas del
curso (todo en minúscula, sin tildes):

| Clave | Valores de ejemplo |
|---|---|
| `ambiente` | `produccion` / `pruebas` |
| `centro-de-costo` | `pensiones` / `ti` |
| `proyecto` | `portal-afiliados` |

---

## Parte 1 · Organiza y crea dos "áreas" (20 min)

Vas a simular dos áreas usando dos **grupos de recursos**.

1. **Create a resource** → **Resource group** → nombre `rg-pensiones` · región East US
   → **Create**. Repite con `rg-ti`.
2. En cada grupo, crea un recurso barato:
   - En `rg-pensiones`: una **Storage account** (`stpensiones<iniciales>`, LRS).
   - En `rg-ti`: otra **Storage account** (`stti<iniciales>`, LRS).

> Usamos storage porque cuesta centavos. Lo importante hoy no es el monto, sino
> **etiquetar y agrupar**.

---

## Parte 2 · Etiqueta cada recurso (25 min)

1. Entra a la Storage account de `rg-pensiones` → menú **Tags** (Etiquetas).
2. Agrega estos pares (clave / valor) y **Guardar**:
   - `ambiente` = `produccion`
   - `centro-de-costo` = `pensiones`
   - `proyecto` = `portal-afiliados`
3. Repite en la Storage account de `rg-ti`, pero con
   `centro-de-costo` = `ti` (las demás igual).
4. **Deja un recurso SIN etiquetar a propósito** (o crea un tercero): lo usarás para
   ver el costo "(sin etiqueta)".

> ✍️ Regla de oro del lab: **las mismas claves en todos los recursos**, escritas
> igual. `centro-de-costo` ≠ `Centro-de-Costo` ≠ `costcenter`.

**Tip (opcional):** también puedes etiquetar el **grupo de recursos** completo; pero
ojo — en Azure las etiquetas **no se heredan** automáticamente al recurso. Por eso
se etiqueta el recurso (o se fuerza con una política, S5).

---

## Parte 3 · Reparte el gasto y repórtalo (15 min)

1. Ve a **Cost Management → Cost analysis**.
2. En **Group by**, elige **Tag** → `centro-de-costo`.
3. Observa el desglose: `pensiones`, `ti` y **`(sin etiqueta)`**.
   - Recuerda la **latencia de 8–24 h**: si aún no hay costo, practica el AGRUPAR y
     filtrar; lo esencial es que el recurso quede etiquetado.
4. Cambia el Group by a `ambiente` y luego a `proyecto`. Fíjate cómo la MISMA
   herramienta responde preguntas distintas según la etiqueta.

> ✍️ **Entregable de la sesión:** en tu bitácora, responde:
> - ¿Cuánto (o qué porcentaje) quedó en `(sin etiqueta)`? ¿Por qué es un problema?
> - Si tuvieras que hacer *showback*, ¿qué le dirías al área de Pensiones?

### ⚠️ Limpieza

Elimina los grupos de recursos `rg-pensiones` y `rg-ti` (**Delete resource group**)
para no consumir crédito.

---

## Checklist de la sesión

- [ ] Creé dos grupos de recursos (dos "áreas") con un recurso cada uno.
- [ ] Etiqueté con `ambiente`, `centro-de-costo`, `proyecto` (mismas claves).
- [ ] Dejé un recurso sin etiqueta para ver el costo "(sin etiqueta)".
- [ ] Agrupé Cost Analysis por etiqueta y sé leer el reparto por área.
- [ ] Eliminé los recursos al terminar.

**Para la Sesión 3:** deja tus recursos etiquetados. Trabajaremos **presupuestos y
alertas por área** — que te avisan antes de que la factura sorprenda.
