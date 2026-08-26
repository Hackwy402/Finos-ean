# Guía de Laboratorio · Sesión 1

## Fundamentos de FinOps — Tu primer contacto con los costos en Azure

**Curso 88-EAN · FinOps y Optimización de Costos Cloud** · Duración: 1 hora
Plataforma: **Microsoft Azure** (cuenta *Azure for Students*)

> Meta de hoy: **ver** el gasto. No optimizamos todavía — primero hay que poder
> mirar. Al terminar sabrás moverte por el portal, estimar costos con la
> calculadora y ubicar un recurso en Cost Analysis.

---

## 0. Requisito: tu cuenta Azure for Students

Antes de empezar necesitas tu cuenta activa (te la habilita EAN con tu correo
académico):

1. Ve a **[azure.microsoft.com/free/students](https://azure.microsoft.com/es-es/free/students/)**.
2. Inicia sesión con el **correo académico** que te dio EAN y verifica tu identidad.
3. Recibes **USD $100 de crédito por 12 meses, sin tarjeta de crédito**.

> El crédito **no se gasta** con la calculadora ni por explorar el portal. Solo se
> consume si dejas recursos **encendidos**. Al final del lab los apagamos.

---

## Parte 1 · Activa y explora (20 min)

1. Entra a **[portal.azure.com](https://portal.azure.com)** con tu cuenta.
2. En la barra de búsqueda superior, escribe **«Subscriptions»** (Suscripciones) y
   ábrelo. Deberías ver tu suscripción *Azure for Students*. Anota:
   - El **nombre** y el **Subscription ID**.
   - El **crédito restante** (aparece como saldo/crédito gratuito).
3. Busca **«Resource groups»** (Grupos de recursos). Estará vacío — normal, aún no
   creaste nada. Recuerda la jerarquía de la teoría:
   `Billing account → Subscription → Resource group → Resource`.
4. Busca y abre **«Cost Management + Billing»** → en el menú, **«Cost analysis»**
   (Análisis de costos). Observa:
   - En una cuenta nueva el gráfico está casi vacío (aún no hay consumo, y la
     facturación **tarda ~8–24 h** en reflejarse). Es esperado.
   - Familiarízate con los controles: **rango de fechas**, **Group by** (Agrupar
     por: Service, Resource group, Location…) y **vista** (columnas, dona, línea).

> ✍️ **Anota en tu bitácora:** Subscription ID, crédito restante, y qué opciones de
> «Group by» ofrece Cost Analysis (las usarás toda la sesión y la S2).

---

## Parte 2 · Estima con la calculadora de precios (25 min)

La **Pricing Calculator** te deja estimar costos **sin desplegar nada** ni gastar
crédito. Es la herramienta para decidir *antes* de crear.

1. Abre **[azure.microsoft.com/pricing/calculator](https://azure.microsoft.com/es-es/pricing/calculator/)**.
2. Arma una pequeña arquitectura de ejemplo (un servicio web con datos). Agrega:
   - **Virtual Machines** → tamaño **B2s** (2 vCPU, 4 GB), Linux, región **East US**,
     **730 horas/mes** (encendida todo el mes).
   - **Storage Accounts** → **100 GB**, tier **Hot**, LRS.
   - **Bandwidth** (salida de datos) → **100 GB** de egress.
3. Ajusta la **moneda** (USD) y mira el **total mensual estimado**.
4. Ahora experimenta con las **palancas de costo** y anota el efecto:
   - Cambia la VM de **730 h** a **200 h/mes** (como si la apagaras de noche y fines
     de semana). ¿Cuánto baja?
   - Cambia el storage de **Hot** a **Cool**. ¿Cuánto baja?
   - Cambia la **región** de East US a otra (p. ej. Brazil South). ¿Sube o baja?

> ✍️ **Anota:** el total inicial y cuánto cambió con cada palanca (horas, tier,
> región). Estas son, en pequeño, las decisiones de optimización de la Sesión 4.

**Pregunta de reflexión:** ¿cuál de las tres palancas dio el mayor ahorro? ¿Por qué
tiene sentido para el negocio?

---

## Parte 3 · Ve tu gasto real (15 min)

Ahora creas un recurso **mínimo y barato** (una cuenta de almacenamiento vacía
cuesta centavos) para verlo aparecer en Cost Analysis.

1. En el portal, **Create a resource** → **Storage account**.
   - **Resource group:** crea uno nuevo llamado `rg-lab-finops`.
   - **Storage account name:** algo único, p. ej. `stlabfinops<tusiniciales>`.
   - **Region:** East US · **Redundancy:** LRS (la más barata).
   - **Review + create** → **Create**.
2. Cuando termine, ve a **Cost Management → Cost analysis** y agrupa por **Resource
   group**. Tu `rg-lab-finops` aparecerá aquí (recuerda: **puede tardar hasta 24 h**
   en mostrar costo por la latencia de facturación).
3. Mientras tanto, en tu recurso, abre **Tags** y ponle una etiqueta
   `ambiente = laboratorio`. (En la S2 usaremos las etiquetas para asignar costos.)

### ⚠️ Limpieza (importante — no gastes tu crédito)

Al terminar, **elimina el grupo de recursos** para que no quede nada cobrando:

- Ve a **Resource groups** → `rg-lab-finops` → **Delete resource group** (escribe su
  nombre para confirmar).

> Una cuenta de storage vacía cuesta casi nada, pero la disciplina FinOps empieza
> por ti: **apaga lo que no usas.**

---

## Checklist de la sesión

- [ ] Cuenta Azure for Students activa; anoté Subscription ID y crédito.
- [ ] Recorrí Cost Analysis y sé agrupar por servicio / grupo / etiqueta.
- [ ] Estimé una arquitectura en la calculadora y medí 3 palancas de ahorro.
- [ ] Creé un recurso, lo ubiqué en Cost Analysis y lo **eliminé** al terminar.

**Para la Sesión 2:** deja tu cuenta activa y trae anotado el resultado de la
calculadora. Trabajaremos **etiquetado y asignación de costos** (¿de quién es cada
peso?).
