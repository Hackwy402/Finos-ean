# Propuesta de optimización de costos cloud

> Plantilla del taller integrador · Sesión 4 · 88-EAN. Reemplaza el texto en
> _cursiva_. Objetivo: 1 página, con números y respaldo en el FinOps Framework.

| | |
|---|---|
| **Equipo / Analista** | _nombres_ |
| **Área** | Pensiones (`centro-de-costo = pensiones`) |
| **Fecha** | _AAAA-MM-DD_ |
| **Costo actual** | $2.590 / mes · **Presupuesto:** $2.800 / mes |

---

## 1. Diagnóstico — Informar
*(FinOps Framework · Fase Inform · Understand Usage & Cost)*

_En 2–3 líneas: ¿cuánto gasta el área y qué componente/recurso domina el costo?
Ej.: «El 85% del costo son las máquinas virtuales; dos de producción están
sobredimensionadas (CPU 12–15%) y hay 3 discos huérfanos.»_

## 2. Riesgo — Cuantificar
*(Fase Inform/Optimize · Quantify Business Value: Forecasting, Budgeting)*

_La proyección (del Excel): «Al ritmo actual, el área cerrará ____ y superará el
presupuesto de $2.800 en el mes de ____ .»_

## 3. Plan de optimización — Optimizar
*(Fase Optimize · Optimize Usage & Cost: Usage & Rate Optimization)*

| Recurso | Acción | Costo antes | Costo después | Ahorro/mes |
|---|---|---|---|---|
| _disco-huerfano ×3_ | _eliminar_ | _$180_ | _$0_ | _$180_ |
| _srv-app-01_ | _rightsizing D4→D2_ | _$920_ | _$___ | _$___ |
| _srv-app-02_ | _rightsizing D4→D2_ | _$920_ | _$___ | _$___ |
| _srv-pruebas-01_ | _apagado fuera de horario_ | _$365_ | _$___ | _$___ |
| _srv-app-01/02_ | _reserva 1 año (escenario B)_ | _$___ | _$___ | _$___ |
| _st-datos / function_ | _mantener_ | _$205_ | _$205_ | _$0_ |

**Escenario A · Quick wins (sin compromiso):** total ≈ $_____ / mes (ahorro __%).
**Escenario B · Con compromiso (+ reserva):** total ≈ $_____ / mes (ahorro __%).

**Recomendación:** _¿A o B? ¿por qué? (inmediatez y riesgo vs ahorro y compromiso)_

## 4. Sostenibilidad — Operar
*(Fase Operate · Manage the FinOps Practice: Governance, Policy & Risk; KPIs)*

- **Política 1:** _ej. etiquetas obligatorias (centro-de-costo, ambiente)_
- **Política 2:** _ej. apagado automático de ambientes de pruebas fuera de horario_
- **KPI a seguir:** _ej. % del presupuesto usado / costo por trámite / $ desperdicio/mes_

## 5. Mapa al FinOps Framework

| Parte de la propuesta | Fase | Capability |
|---|---|---|
| Diagnóstico | Inform | Reporting & Analytics · Allocation |
| Riesgo / proyección | Inform | Forecasting · Budgeting |
| Plan de optimización | Optimize | Usage Optimization · Rate Optimization |
| Sostenibilidad | Operate | Governance, Policy & Risk · KPIs & Benchmarking |

---
_Una frase de cierre para el líder: «Con el Escenario ___ el área queda en $____ /mes,
por debajo del presupuesto, sin afectar el servicio.»_
