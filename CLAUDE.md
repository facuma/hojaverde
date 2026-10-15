# HojaVerde — Contexto completo del proyecto (Ideathon NEA Tech 2026 + Stellar Track)

> Nombre de trabajo: **HojaVerde**. El equipo puede cambiarlo.
> Este archivo es el contexto maestro para Claude Code. Leelo entero antes de escribir código.

---

## 0. Instrucciones para Claude Code

- **Deadline duro:** viernes 16/10/2026 a las 19:00 (hora Argentina, UTC-3). Subir todo a las 18:30 como tarde. Commits posteriores a las 19:00 no cuentan para Stellar.
- **Prioridad:** primero una demo que funcione de punta a punta (sección 7, "Camino feliz de la demo"). Después, lo lindo. Nunca al revés.
- **Todo dato que no sea real se marca en la UI y en el README** con una etiqueta: `REAL`, `ESTIMADO` o `SIMULADO` (lo exige la guía de la ideathon).
- **Idioma de la UI:** español rioplatense, lenguaje simple. El usuario final es un productor rural y un comerciante de pueblo, no un banquero.
- **Mobile first:** el productor y el comercio usan celular.
- **No inventes integraciones oficiales** (SENASA, INYM, ARCA). Se simulan con datos seed y se dice que son simulados.
- **El contrato Soroban es requisito del track Stellar:** debe quedar desplegado en testnet, con su Contract ID y al menos un hash de transacción real en el README.
- Antes de cada bloque grande de trabajo, revisá la sección 9 (plan por hora) y decime qué vas a hacer.

---

## 1. El evento y las reglas que nos afectan

### 1.1 Ideathon NEA Productivo Digital (track principal)

- Escenario elegido: **Escenario 2 · Financiar lo que producimos**.
- Desafío oficial: transformar producción, contratos o derechos económicos del NEA en nuevas oportunidades de financiamiento y comercialización.
- Pregunta guía oficial: **¿Qué necesitaría comprobar un financiador antes de anticipar fondos?**
- Ejemplo que da la propia guía: una cooperativa yerbatera de Misiones que necesita capital antes de vender o cobrar.
- Pistas oficiales que la solución tiene que respetar explícitamente:
  1. Producción estimada, mercadería disponible y derecho de cobro **no son equivalentes**.
  2. Un token **no prueba por sí mismo** la existencia ni el valor de un activo.
  3. Hay que **identificar quién responde** si la cosecha o el contrato no se cumple.
- Blockchain/tokenización: no es obligatorio, "pero tiene un plus".
- No se exigen transacciones reales, integraciones oficiales ni certificaciones.

**Evaluación ideathon (100 pts):**

| Criterio | Puntos |
| --- | --- |
| Comprensión y resolución del problema | 25 |
| Innovación y diferenciación | 25 |
| Prototipo / demostración | 20 |
| Valor e impacto potencial | 20 |
| Factibilidad y validación | 10 |

**Entrega ideathon:** problema y destinatario con fuentes; solución y propuesta de valor; link a demo navegable; tecnologías y por qué; impacto, supuestos, limitaciones y siguiente paso; pitch deck PDF; declaración de uso de IA, componentes previos y datos simulados.

### 1.2 Stellar Track (track secundario, mismo proyecto)

- Equipo de 2 a 5 personas (para competir en ambos: 4 o 5).
- Requisitos mínimos:
  - Repo público en GitHub con código, README con instalación, despliegue y testing.
  - Al menos una herramienta del stack Stellar (usamos **Soroban + Stellar SDK + Freighter**, opcional Passkeys).
  - **Smart contract desplegado** en testnet, con **Contract ID** en README y entrega.
  - **Al menos una transacción real en testnet**, con hash o link a Stellar Expert en README y entrega, más las direcciones de las cuentas usadas.
  - Video demo + pitch de hasta 5 min (YouTube o Drive público). **Sin video no puntúa.**
  - Pitch deck PDF.
  - Evidencia de validación (entrevistas, encuestas, datos).
  - Declarar uso de IA y qué existía antes del evento.
- Entrega en **Stellar APEX** (https://stellarapex.org). Cierre viernes 16/10 19:00.

**Evaluación Stellar (100 pts):**

| Criterio | Puntos |
| --- | --- |
| Validación con usuarios reales | 25 |
| Impacto (Argentina / LATAM) | 20 |
| Ejecución y calidad | 20 |
| Innovación | 20 |
| Integración con Stellar | 15 |

---

## 2. El problema

### 2.1 Historia corta (para el pitch)

Don Ramón tiene 15 hectáreas de yerba en el centro de Misiones. Entrega hoja verde al mismo secadero hace 12 años. En agosto necesita fertilizante y plata para pagar a los tareferos, pero cobra recién después de la cosecha. El banco le pide garantías y balances que no tiene. El comercio de insumos del pueblo le fía "al conocido", con riesgo alto y sin forma de cobrar si algo sale mal. Resultado: Ramón fertiliza menos, cosecha menos, y el ciclo se repite.

### 2.2 El insight (nuestro diferencial central)

**El productor del NEA no tiene historial crediticio, pero sí tiene historial productivo.** Cada entrega de hoja verde al secadero queda registrada. El estado del yerbal se ve por satélite. El clima de su zona es dato público. Nadie usa ese rastro para prestar.

Además, **existe un actor que siempre ve pasar la plata del productor: el secadero**, que le compra la hoja. Si la cuota se descuenta en el momento de la entrega, el riesgo de cobro cae muchísimo.

### 2.3 Datos de contexto (marcar origen en la UI y el pitch)

- Ejemplo oficial de la guía: cooperativa yerbatera de Misiones que necesita capital antes de vender. (REAL, fuente: guía NEA Productivo Digital)
- En agro, muchos costos se pagan antes de vender y cobrar. (REAL, guía oficial)
- En ganadería el crédito cubre ~5,6% de la inversión anual del sector, según Rosgan. (REAL, Bichos de Campo) — sirve como dato análogo del déficit de crédito en el campo.
- El canje de insumos por cosecha ya existe en el agro argentino. Nuestro aporte no es inventar el canje: es **puntuar con datos productivos verificables y automatizar el descuento en el punto de entrega**, para llegar al productor chico que hoy queda afuera.
- Precio de la hoja verde: desde la desregulación de fines de 2023 dejó de fijarlo el INYM y pasó a negociarse. **(VERIFICAR antes del pitch.)** En la demo usamos un precio de referencia SIMULADO configurable.
- Fuentes para citar: INYM (https://inym.org.ar/), INTA Cerro Azul sobre precios en la cadena yerbatera, INTA sobre adopción de tecnología en yerbateros, BCRA, CNV.

### 2.4 Destinatarios (claros, como pide la consigna)

| Actor | Qué gana |
| --- | --- |
| **Productor yerbatero chico/mediano** (usuario principal) | Accede a insumos a tiempo sin garantías; paga en kilos de hoja, no en pesos |
| **Comercio de insumos agrícolas** (cliente que paga) | Vende más y fía con riesgo medido y cobranza automática |
| **Secadero / cooperativa** | Productores que rinden más, fidelización, comisión por cobranza |
| **Financiador externo** (opcional, fase 2) | Cartera de créditos agro de corto plazo, con evidencia verificable |

---

## 3. La solución

**HojaVerde convierte el historial productivo del yerbatero en crédito para insumos, y cobra la cuota automáticamente cuando entrega la hoja verde al secadero.**

Respuesta directa a la pregunta guía — **lo que el financiador necesita comprobar, y cómo lo comprobamos:**

| El financiador necesita saber | Cómo lo verifica HojaVerde | Pista oficial que responde |
| --- | --- | --- |
| ¿Este productor produce de verdad? | Entregas históricas registradas por el secadero (lo que **ya ocurrió**, no lo estimado) | Pista 1 |
| ¿Va a producir esta campaña? | Salud del yerbal por satélite (NDVI) + clima de la zona | Pista 1 (estimación separada y etiquetada) |
| ¿Cómo cobro? | El secadero descuenta la cuota al recibir la hoja; el contrato reparte el pago | Pista 3 |
| ¿Quién responde si falla? | Orden explícito: productor → fondo de garantía de la cooperativa → financiador. Escrito en el contrato | Pista 3 |
| ¿El token prueba algo? | No. El token solo registra el derecho de cobro; la evidencia viene de las entregas y el satélite, y cada evidencia guarda su fuente | Pista 2 |

---

## 4. Casos de uso expandidos y diferenciales

Los marcados **[MVP]** se construyen para el viernes. Los **[PITCH]** se cuentan como hoja de ruta (con mockup si sobra tiempo).

### 4.1 Score productivo explicable [MVP] — diferencial principal

- Score 0–100 calculado con fórmula **transparente** (no caja negra), con pesos visibles.
- Claude (API) traduce el score a una explicación en lenguaje simple para el productor y para el comercio: "Te aprobamos $X porque entregaste todos los años desde 2014 y tu yerbal está más verde que el promedio de tu zona. Lo que más te baja: la caída de entregas en 2022."
- El productor ve **qué hacer para mejorar** su score.
- Diferencial vs UfarmX y scoring bancario: usamos registros productivos reales del NEA, no solo satélite, y el score se explica.

### 4.2 Crédito en insumos, no en efectivo [MVP]

- El crédito se usa en el comercio adherido. La plata va al comercio, no al productor.
- Reduce el desvío de fondos y le da al comercio un motivo para adherir: vende más.

### 4.3 Cobro en origen ("la cuota viaja con la hoja") [MVP] — diferencial principal

- Cuando el secadero registra una entrega, el contrato Soroban **divide el pago automáticamente**: cuota al acreedor, resto al productor.
- Nadie tiene que perseguir a nadie. Es la respuesta a "¿quién responde?".

### 4.4 Deuda en kilos de hoja verde [MVP]

- La cuota se expresa en **kg de hoja verde**, no en pesos. Se liquida al precio de referencia del día de la entrega.
- Protege al productor de la inflación y del descalce entre lo que debe y lo que cobra. Protege al acreedor porque cobra en el mismo activo que produce el deudor.

### 4.5 Cuota que entiende el clima ("pausa climática") [MVP] — momento wow de la demo

- Si hay **helada o sequía** en la zona del lote (umbral sobre datos de clima), el contrato **reprograma automáticamente** la cuota sin multa y sin trámite.
- En la demo: botón "Simular helada en Oberá" → la cuota se mueve a la próxima cosecha y se ve el evento on-chain.
- Datos de clima: Open-Meteo (API gratuita, sin key) para mostrar el clima REAL de la zona; el disparo del evento en la demo es SIMULADO.
- Diferencial: nadie en crédito agro chico ofrece esto. Encaja con la categoría "seguros que pagan con datos" del track Stellar.

### 4.6 Fondo de garantía de la cooperativa [MVP light / PITCH]

- La cooperativa aporta a un fondo común (en stablecoin de prueba) que cubre la primera pérdida si un socio no puede pagar.
- Convierte la confianza comunitaria que ya existe en una garantía medible. Orden de responsabilidad explícito.
- MVP: el contrato tiene un saldo de garantía y una función que lo usa ante default. PITCH: gobernanza del fondo.

### 4.7 Pasaporte productivo portable [PITCH]

- El productor es dueño de su historial verificado y lo puede mostrar a otro comercio, banco o comprador.
- Encaja con la categoría "identidad digital y credenciales" del track Stellar.

### 4.8 Productor por WhatsApp [PITCH, o MVP si sobra tiempo]

- El productor no instala nada: consulta su cupo, su cuota y su score por WhatsApp. Un agente con Claude responde.
- Si se hace, alcanza con una pantalla que simule el chat.

### 4.9 Inversores fuera de la región [PITCH]

- Un financiador externo fondea la cartera de créditos en USDC y cobra cuando los productores entregan.
- Mencionar el régimen de tokenización de la CNV (RG 1069/2025, sandbox) como camino regulatorio, **sin afirmar que está vigente hoy: verificar**.

### 4.10 El mismo modelo en otras cadenas del NEA [PITCH] — escalabilidad

El patrón es siempre: **productor sin historial crediticio + comprador que ve pasar su plata**.

| Cadena | Quién descuenta la cuota |
| --- | --- |
| Yerba mate (MVP) | Secadero / cooperativa |
| Ganadería de cría | Consignatario en el remate de terneros |
| Arroz | Molino arrocero |
| Tabaco | Acopiador |
| Té | Secadero de té |

---

## 5. Actores y flujo

```
Productor ──pide insumos──▶ Comercio ──consulta score──▶ HojaVerde
                                                            │
                         ◀──aprueba cupo + contrato─────────┘
Comercio entrega insumos al productor
                 │
   (meses después, cosecha)
                 ▼
Productor ──entrega hoja verde──▶ Secadero ──registra entrega──▶ Contrato Soroban
                                                                    │
                       ┌────────── divide el pago ──────────────────┤
                       ▼                                            ▼
              Cuota (kg × precio) al acreedor            Resto al productor

Evento climático (helada/sequía) ──oráculo/admin──▶ Contrato: pausa y reprograma la cuota
Default ──▶ Contrato usa el fondo de garantía de la cooperativa
```

---

## 6. Arquitectura y stack

| Capa | Tecnología | Por qué |
| --- | --- | --- |
| Frontend | Next.js (App Router) + TypeScript + Tailwind | Rápido, mobile first, deploy en Vercel |
| Backend | API Routes de Next.js | Sin servidor aparte; alcanza para la demo |
| Datos | SQLite + Prisma (o JSON seed si falta tiempo) | Datos SIMULADOS de productores, entregas y lotes |
| Mapa | Leaflet + OpenStreetMap | Mostrar el lote del productor |
| Satélite | NDVI precalculado y guardado en seed (SIMULADO); opcional Sentinel Hub / Google Earth Engine | En 24 h no da para pipeline satelital real |
| Clima | Open-Meteo API | Gratis, sin API key, dato REAL |
| IA | Claude API (`claude-sonnet-5-5`) | Explicación del score y agente WhatsApp |
| Smart contract | Soroban (Rust) | Requisito Stellar; lógica de reparto y pausa |
| Wallet | Freighter (o Passkeys si sobra tiempo) | Firma de transacciones en testnet |
| SDK | `@stellar/stellar-sdk` | Llamadas al contrato desde el front |
| Base del proyecto | Scaffold Stellar (https://scaffoldstellar.org) | Trae la integración armada |
| Token de prueba | Asset propio en testnet (ej. `USDCT`) vía Stellar Asset Contract | Evita depender de faucets de USDC |

Recursos: Stellar Docs (https://developers.stellar.org), Stellar Lab (https://lab.stellar.org), guía de IA para la hackathon (https://github.com/kaankacar/stellar-ai-guide-mx), guía Buen Día Builders (https://github.com/BuenDia-Builders/stellar-guide-vendimia-tech). **Leer la guía de IA antes de escribir el contrato.**

### 6.1 Estructura de repo sugerida

```
/contracts/hojaverde_credit/     # Soroban (Rust)
  src/lib.rs
  src/test.rs
/app/                            # Next.js
  (productor)/                   # vista productor
  (comercio)/                    # vista comercio
  (secadero)/                    # vista secadero
  api/score/route.ts
  api/explain/route.ts           # llama a Claude
  api/weather/route.ts           # Open-Meteo
/lib/score.ts                    # fórmula del score
/lib/stellar.ts                  # cliente del contrato
/prisma/schema.prisma
/prisma/seed.ts                  # datos SIMULADOS
README.md
CLAUDE.md
```

---

## 7. Camino feliz de la demo (lo único que TIENE que funcionar)

Duración objetivo: 3 minutos dentro del pitch de 5.

1. **Comercio** abre HojaVerde y busca a "Ramón Benítez" por CUIT (SIMULADO).
2. Ve el **score 78/100** con la explicación generada por Claude y el mapa del lote con NDVI.
3. Ve el **cupo aprobado**: hasta 30% del valor estimado de su próxima cosecha, expresado en kg de hoja verde.
4. Carga el pedido (fertilizante + herbicida) y **crea el crédito** → firma con Freighter → **transacción en testnet** (mostrar link a Stellar Expert).
5. Corte de tiempo: "Pasaron 6 meses, llegó la cosecha."
6. **Secadero** registra la entrega de 4.000 kg de Ramón → el contrato **divide el pago**: cuota al comercio, resto a Ramón → segunda transacción en testnet.
7. Momento wow: con otro productor, botón **"Simular helada en Oberá"** → la cuota se **reprograma sola** y se ve el evento en el contrato.
8. Cierre: pantalla del productor en el celular mostrando "Cuota pagada. Tu score subió a 82."

**Plan B sin internet:** video grabado del camino feliz + capturas en el deck.

---

## 8. Especificaciones

### 8.1 Modelo de datos (Prisma, todo SIMULADO salvo clima)

```prisma
model Productor {
  id            String   @id @default(cuid())
  nombre        String
  cuit          String   @unique   // SIMULADO
  localidad     String              // ej. Oberá, Apóstoles, Jardín América
  lat           Float
  lng           Float
  hectareas     Float
  anioInicio    Int
  cooperativa   String?
  walletAddress String?            // cuenta testnet
  entregas      Entrega[]
  lotes         Lote[]
  creditos      Credito[]
}

model Entrega {
  id          String   @id @default(cuid())
  productorId String
  secadero    String
  fecha       DateTime
  kg          Float
  productor   Productor @relation(fields: [productorId], references: [id])
}

model Lote {
  id          String   @id @default(cuid())
  productorId String
  poligono    Json      // GeoJSON
  ndviActual  Float     // SIMULADO
  ndviZona    Float     // promedio de la zona, SIMULADO
  productor   Productor @relation(fields: [productorId], references: [id])
}

model Credito {
  id             String   @id @default(cuid())
  productorId    String
  comercio       String
  montoInsumos   Float     // en USDCT
  cuotaKg        Float     // deuda expresada en kg de hoja verde
  estado         String    // ACTIVO | PAUSADO | PAGADO | DEFAULT
  contractCredId Int?      // id dentro del contrato Soroban
  txHashCreacion String?
  txHashPago     String?
  productor      Productor @relation(fields: [productorId], references: [id])
}
```

Seed: 6 productores con historias distintas (uno perfecto, uno con caída por sequía 2022, uno nuevo con poco historial, uno con yerbal en mal estado, etc.). 10 a 12 años de entregas para los antiguos. Localidades reales de Misiones y norte de Corrientes con coordenadas aproximadas.

### 8.2 Fórmula del score (`/lib/score.ts`)

Transparente y documentada. Cada componente devuelve 0–1 y se pondera:

| Componente | Peso | Cálculo sugerido |
| --- | --- | --- |
| Regularidad de entregas | 30 | % de años con entrega en los últimos 10 |
| Tendencia de volumen | 20 | Pendiente normalizada de kg/año, últimos 5 años |
| Salud del yerbal | 20 | `ndviActual / ndviZona`, recortado a [0, 1.2] y normalizado |
| Antigüedad con el secadero | 10 | min(años / 10, 1) |
| Pertenencia a cooperativa | 10 | 1 si es socio, 0 si no |
| Riesgo climático de la zona | 10 | 1 − probabilidad de helada/sequía (SIMULADO por zona) |

- **Cupo:** `cupoKg = score/100 × 0.30 × kgEsperadosProximaCosecha`, donde `kgEsperados` = promedio de los últimos 3 años ajustado por NDVI. Mostrar siempre que es ESTIMADO.
- Devolver también los 2 factores que más suben y los 2 que más bajan, para que Claude los explique.

### 8.3 Endpoint de explicación (`/api/explain`)

- Input: datos del productor + desglose del score.
- Prompt a Claude: explicar en 3 o 4 oraciones, lenguaje de campo, tuteo rioplatense, sin tecnicismos, incluir qué hacer para mejorar. Dos versiones: para el productor y para el comercio (más orientada a riesgo).
- Nunca inventar datos que no estén en el input.

### 8.4 Contrato Soroban `hojaverde_credit`

Estado por crédito:

```rust
struct Credit {
    productor: Address,
    acreedor: Address,      // comercio o financiador
    secadero: Address,      // único autorizado a liquidar entregas
    cuota_kg: i128,         // deuda en kg (× 1000 para decimales)
    pagado_kg: i128,
    vencimiento: u64,       // timestamp
    estado: Status,         // Activo | Pausado | Pagado | Default
}
```

Funciones:

| Función | Quién firma | Qué hace |
| --- | --- | --- |
| `init(admin, token, oracle)` | admin | Configura token de pago y cuenta oráculo de clima |
| `create_credit(productor, acreedor, secadero, cuota_kg, vencimiento) -> u32` | acreedor | Registra el derecho de cobro. Emite evento `credit_created` |
| `settle_delivery(credit_id, kg_entregados, precio_por_kg)` | secadero | El secadero transfiere el pago total de la entrega al contrato; el contrato envía al acreedor `min(pendiente, kg) × precio` y el resto al productor. Actualiza `pagado_kg`. Si completa, estado `Pagado`. Evento `delivery_settled` |
| `climate_pause(credit_id, nuevo_vencimiento, motivo)` | oracle | Reprograma sin multa. Estado `Pausado` → `Activo` con nueva fecha. Evento `climate_pause` |
| `fund_guarantee(monto)` | cooperativa | Deposita al fondo de garantía |
| `claim_guarantee(credit_id)` | acreedor | Si venció y está impago, cobra del fondo hasta el saldo pendiente. Estado `Default` |
| `get_credit(credit_id) -> Credit` | cualquiera | Lectura |

Reglas:

- Solo el `secadero` registrado puede llamar `settle_delivery` para ese crédito.
- Solo el `oracle` puede llamar `climate_pause`.
- Todos los montos con `i128` y escala fija; documentar la escala.
- Tests en `src/test.rs` para: creación, liquidación parcial, liquidación total, pausa climática, cobro de garantía, y llamadas no autorizadas que deben fallar.

**Honestidad técnica (para el pitch):** el contrato garantiza que el reparto se cumple tal como se pactó y deja todo auditable. **No garantiza** que la entrega física ocurrió: eso lo registra el secadero, que es un actor identificado y responsable. El token no prueba el activo; la evidencia sí.

### 8.5 Cuentas de testnet a crear y documentar en README

- `admin`, `oracle`, `comercio` (acreedor), `secadero`, `productor_ramon`, `productor_2`, `cooperativa`.
- Fondear con Friendbot. Crear y distribuir el asset `USDCT`.
- Registrar en README: Contract ID, direcciones públicas y hashes de: `create_credit`, `settle_delivery` y `climate_pause`.

---

## 9. Plan por hora (jueves 15 noche → viernes 16 19:00)

| Bloque | Qué | Quién (sugerido) |
| --- | --- | --- |
| Jue 20:00–22:00 | Scaffold Stellar + Next.js levantados; esqueleto del contrato compilando; schema + seed | Dev contrato / Dev front |
| Jue 22:00–01:00 | Contrato: `create_credit`, `settle_delivery` + tests. Front: vistas comercio y productor con datos seed, score funcionando | Dev contrato / Dev front |
| Vie 09:00–12:00 | Deploy del contrato a testnet; conectar front con Freighter; primera tx real | Ambos |
| Vie 12:00–14:00 | `climate_pause` + botón de helada; endpoint Claude de explicación; clima Open-Meteo | Dev contrato / Dev front |
| Vie 14:20–16:00 | Construcción acompañada: pulir camino feliz completo, vista secadero | Todos |
| Vie 16:00 | Taller de pitch (ir) | Todos |
| Vie 16:40–18:00 | README completo con hashes y Contract ID; grabar video; deck PDF | Pitch / Dev |
| Vie 18:20 | Revisión técnica | Todos |
| **Vie 18:30** | **Subir todo a Stellar APEX y al canal de la ideathon** | Líder |
| Vie 19:00 | Cierre. No más commits | — |

**En paralelo desde el jueves:** una persona hace 2–3 entrevistas cortas (sección 11). Valen 10 pts en la ideathon y 25 en Stellar.

---

## 10. Pitch (5 minutos)

1. **Ramón** (30 s): la historia de 2.1.
2. **El problema** (40 s): sin historial crediticio, con historial productivo. El comercio fía a ciegas.
3. **La solución** (40 s): score productivo explicable + crédito en insumos + la cuota viaja con la hoja.
4. **Demo** (2 min): camino feliz de la sección 7, con el momento de la helada.
5. **Por qué responde la consigna** (30 s): tabla de la sección 3, las tres pistas.
6. **Escala y modelo de negocio** (30 s): comisión por crédito al comercio + fee de cobranza al secadero; mismo modelo en ganadería, arroz, tabaco, té.
7. **Validación y próximo paso** (20 s): lo que dijeron los entrevistados; piloto con una cooperativa.

Diferenciales para repetir: **explicable, en kilos, cobro en origen, entiende el clima, garantía comunitaria.**

---

## 11. Validación (guion de entrevista, 5 min por persona)

A un productor yerbatero, un comercio de insumos o alguien de una cooperativa/secadero:

1. ¿Cómo financian hoy los insumos antes de la cosecha?
2. ¿Qué pasa cuando alguien no puede pagar?
3. ¿Le fiarías/aceptarías si la cuota se descuenta sola al entregar la hoja?
4. ¿Preferís deber en kilos o en pesos? ¿Por qué?
5. Si viene una helada, ¿qué pasa hoy con la deuda?

Registrar: nombre o rol (con permiso), fecha, respuestas clave. Va al README y al deck como evidencia.

---

## 12. Supuestos, limitaciones y riesgos (declarar en la entrega)

- **Datos:** entregas, CUIT, NDVI y riesgo climático por zona son SIMULADOS. Clima actual de Open-Meteo es REAL. Precio de referencia de hoja verde es SIMULADO.
- **Acceso a datos reales:** el historial de entregas lo tiene el secadero; el modelo supone que lo comparte con consentimiento del productor. No hay integración con INYM ni SENASA.
- **El contrato no verifica la entrega física:** depende de que el secadero la registre. El secadero es un actor identificado y con incentivo a cumplir.
- **Regulación:** el crédito comercial de un comercio a su cliente es habitual; un financiador externo o la tokenización de la cartera requieren encuadre CNV/BCRA. Verificar el estado del sandbox de tokenización de la CNV.
- **Oráculo climático:** en la demo es una cuenta admin; en producción sería un oráculo con datos meteorológicos verificables.
- **Uso de IA:** declarar que se usó Claude/Claude Code para desarrollo y que la app usa Claude API para las explicaciones.

## 13. Siguiente paso de validación

Piloto de 1 campaña con una cooperativa yerbatera de Misiones, 20 productores y 1 comercio de insumos, midiendo: tasa de aprobación, tasa de cobro en origen y kg adicionales cosechados por mejor fertilización.
