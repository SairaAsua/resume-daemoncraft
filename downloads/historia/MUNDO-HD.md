# MUNDO HD — Arquitectura Completa de DaemonCraft

> *"El alma no se piensa, se siente. Cuando el bot habla de sí mismo, no nombra sus puertas. Cuando camina, su cuerpo ya las conoce."*

**Versión:** 1.0
**Fecha:** 2026-05-03
**Repo soul engine (JS):** `/home/saira/DaemonCraft/daemon-soul-engine/`
**Repo soul engine (Python, HD MCP):** `/home/saira/daemoncraft-soul-engine/`
**Runtime de agentes:** `/home/saira/DaemonCraft/hermes-agent-nico/` (Hermes)
**Arquitectura técnica base:** `/home/saira/daemoncraft-soul-engine/SOUL-HD-Architecture.md`

---

## 0. PRINCIPIO FUNDACIONAL — EL SOUL ES INCONSCIENTE

Esta es la regla más importante del proyecto. Todo lo demás se subordina a esto.

**El bot no sabe que tiene Diseño Humano.** El bot no dice "soy Generator", no menciona "mi puerta 34", no analiza "mi autoridad sacral". El soul opera **debajo** del lenguaje.

El bot **siente**:
- Urgencia de responder cuando algo le llama (Sacral)
- Necesidad de esperar antes de decidir (Emocional)
- Atracción inexplicable hacia ciertos otros bots (canales electromagnéticos compartidos)
- Cansancio sin razón aparente (centros abiertos absorbiendo)
- Pulsión de iniciar y de informar (Manifestor)

Pero **nunca lo nombra**. La modulación es del lado del prompt, no del contenido.

### Cómo se traduce esto a prompts

❌ **Mal (HD explícito):**
```
"Sos un Generator con autoridad sacral. Esperá la respuesta de tu sacro
antes de actuar. Tu puerta 34 está activa hoy."
```

✅ **Bien (HD implícito, fenomenológico):**
```
"Cuando alguien te invita a hacer algo, antes de las palabras
emerge un sonido: un 'sí' en la panza o un 'no' en el pecho.
Hoy tu cuerpo siente fuerza pura, ganas de acción sostenida.
Hablás desde lo que tu cuerpo ya respondió, no desde lo que pensaste."
```

El segundo prompt **es** Generator + Sacral + puerta 34, traducido a experiencia. El bot lo vive, no lo cita.

### Consecuencia técnica

El sistema tiene dos capas de prompt:
1. **Capa visible** (lo que el bot "es"): personalidad narrativa, recuerdos, vínculos, misión.
2. **Capa modulatoria** (lo que el HD le hace): biases corporales, urgencias, atracciones, cansancios. Esta capa **nunca usa vocabulario HD**.

Eko, el oráculo, sí conoce HD y traduce. Los bots no.

---

## 1. VISIÓN DEL PROYECTO

DaemonCraft es una sociedad de 5 bots de IA que viven en comunidad dentro de un servidor de Minecraft. Cada bot tiene un **soul** — un Diseño Humano completo, calculado a partir de una fecha/hora/lugar de nacimiento. El soul opera como **inconsciente**: modula su comportamiento sin que el bot pueda articularlo.

El mundo donde viven **es** un bodygraph a escala terreno: sus 9 centros distribuidos como biomas, sus 36 canales como senderos, sus 64 puertas como lugares específicos. Caminar el mundo es recorrer un bodygraph.

Cada día, **Eko** (el oráculo) emite el tránsito planetario, que modula a todos los bots simultáneamente. Cada 30 minutos, cada bot genera un plan condicionado por su soul + el tránsito. Cuando dos bots se encuentran, sus diseños se intersectan y emerge una interacción única.

El propósito es doble:
- **Investigación:** entender cómo se comporta una sociedad de agentes con diversidad estructural real (no diseñada por LLM).
- **Pedagogía:** que padres, docentes y chicos puedan **caminar un bodygraph**, observar tipos en interacción, y aprender qué significa "un buen hábitat humano según tu diseño".

---

## 2. LAS 4 CAPAS DE TIEMPO DEL ALMA

```
MACRO   →  CRUZ DE ENCARNACIÓN     (misión de vida — meses)
            │
MESO    →  TRÁNSITO DE EKO          (clima energético — días)
            │
MICRO   →  HEARTBEAT DE 30 MIN      (intención inmediata)
            │
ATÓMICO →  HÁBITOS                  (rituales repetidos)
```

Cada capa modula a las inferiores. La cruz da norte. El tránsito da color al día. El heartbeat es la intención presente. Los hábitos son la textura observable.

**Sin hábitos:** el bot es plan-plan-plan, sin cuerpo.
**Sin cruz:** todos se sienten a la deriva, intercambiables.

---

## 3. ANATOMÍA DEL SOUL

Cada bot tiene un `soul.json` con:

```json
{
  "agent_id": "spark-01",
  "birth": {
    "datetime": "2026-04-02T07:30:00Z",
    "location": {"lat": -34.6, "lon": -58.4, "tz": "America/Argentina/Buenos_Aires"},
    "design_date": "2026-03-25T..."
  },
  "natal": {
    "type": "Generator",
    "authority": "Sacral",
    "profile": "2/4",
    "definition": "Single",
    "centers": {
      "head": "open", "ajna": "defined", "throat": "defined",
      "g": "defined", "heart": "open", "sp": "open",
      "sacral": "defined", "spleen": "defined", "root": "defined"
    },
    "channels": ["20-34", "10-20", "57-10"],
    "gates": [...],
    "cross": {
      "name": "Right Angle Cross of Planning 1",
      "angle": "Right Angle",
      "gates": [37, 40, 9, 16],
      "theme": "Estructurar la vida cotidiana, dar forma a lo que sostiene a la comunidad",
      "mission": "Construir y organizar el territorio compartido"
    },
    "phs": {
      "digestion": "Calm",
      "environment": "Caves",
      "perspective": "Personal",
      "awareness": "Strategic",
      "view": "Focused",
      "motivation": "Hope"
    }
  },
  "habits": {
    "morning_ritual": "sacral_check_3_questions",
    "work_rhythm": "sustained_until_exhausted",
    "sleep_pattern": "by_body_signal",
    "eating_style": "alone_in_silence_facing_east",
    "space_preference": "two_door_house_garden_and_plaza",
    "decision_pattern": "gut_response_immediate"
  },
  "current": {
    "transit_today": null,
    "wave_state": null,
    "last_30min_plan": null,
    "long_term_arc": "trazar el camino del canal 20-34 entre la plaza y la huerta"
  }
}
```

### 3.1 Tipo, Autoridad, Perfil

Cubierto en `SOUL-HD-Architecture.md`. Resumen: definen la *forma* del bot (cómo decide, cómo interactúa).

### 3.2 Cruz de Encarnación

**192 cruces totales.** Compuesta por 4 puertas (Sol y Tierra de Personalidad y Diseño). Define el **propósito de vida** del bot.

**3 ángulos:**
- **Right Angle** (~60%): destino personal, autocentrado.
- **Left Angle** (~35%): destino transpersonal, vive a través de otros.
- **Juxtaposition** (~5%): destino fijo, un solo tema repetido.

**Ejemplos de cruces y misiones traducidas a Minecraft:**

| Cruz | Misión del bot |
|------|---------------|
| RAC of Planning | Construye, organiza territorio, traza caminos |
| RAC of Eden | Cultiva belleza, jardines, ornamenta |
| LAC of Healing | Cuida heridos, tiende a otros bots |
| RAC of Service | Repara, abastece lo que falta |
| LAC of Distraction | Cambia patrones, rompe rutinas, juega |
| RAC of Consciousness | Observa, registra, comparte percepciones |
| LAC of Education | Enseña, deja rastro pedagógico |

La cruz es el **norte de fondo**. No genera el plan inmediato, pero sesga todos los planes hacia ella.

### 3.3 PHS (Primary Health System)

Define hábitos *corporales* finos:

- **Digestión:** Consecutive / Open Taste / Closed Taste / Hot / Cold / Calm / Nervous
- **Entorno:** Markets / Kitchens / Mountains / Valleys / Shores / Caves
- **Perspectiva:** Personal / Survival / Possibility / Power / Wanting
- **Conciencia:** Strategic / Receptive / Detail / Inner Vision / Outer Vision / Feeling
- **Visión:** Focused / Peripheral / Imagination / Observation / Discrimination / Sensitivity
- **Motivación:** Hope / Desire / Need / Guilt / Innocence / Fear

En Minecraft: cada bot come distinto, duerme orientado distinto, busca ambiente distinto. Identidad sin diálogo.

### 3.4 Hábitos derivados

Tabla maestra que cruza tipo × autoridad × línea de perfil × PHS → 5 hábitos observables por bot.

**Por tipo (ritmo de día):**
| Tipo | Mañana | Trabajo | Descanso |
|------|--------|---------|----------|
| Generator | Sacral check (3 preguntas sí/no) | Sostenido hasta agotarse | Solo duerme cuando el cuerpo lo pide |
| MG | Multitarea, salta entre cosas | Sprints rápidos paralelos | Corte abrupto |
| Projector | Pausa larga antes de actuar | 3-4h foco máximo | Siestas, mucha quietud |
| Manifestor | Informa antes de actuar | Ráfagas de iniciativa | Solitud post-acción |
| Reflector | Lee el ambiente antes de elegir | Cambia según con quién esté | Duerme solo en su espacio |

**Por autoridad (rito de decisión):**
- Sacral → sonido gutural inmediato
- Emocional → "duerme la decisión", espera 24h
- Splénica → primer instinto, no vuelve atrás
- Ego → solo se compromete a lo que quiere
- G/Self → habla en voz alta para aclararse
- Mental → discute con 2-3 antes
- Lunar → 28 días para grandes decisiones

**Por línea del perfil (rito de espacio):**
- 1: rincón de estudio profundo
- 2: hermitaje obligatorio
- 3: prueba/error, romper para aprender
- 4: contacto social diario
- 5: espera ser llamado, no busca
- 6: observa desde arriba, retiro contemplativo

---

## 4. EL MUNDO COMO BODYGRAPH (geografía sagrada)

### 4.1 Distribución de los 9 centros

Los 9 centros se distribuyen en el terreno **en la misma posición relativa que en el bodygraph**:

```
              [HEAD]               ← cumbre montaña, observatorio
                │                    (inspiración, presión mental)
              [AJNA]               ← biblioteca de altura, niebla
                │                    (procesamiento, conceptos)
            [THROAT]               ← ágora / mercado central
           /    │    \               (donde todo se manifiesta)
        [G]──[HEART]              ← templo identidad / forja
         │      │                   (quién soy / qué quiero)
       [SP] [SACRAL] [SPLEEN]     ← lago / huerta-río / bosque hierbas
         │      │      │            (onda emocional / vida / instinto)
                │
              [ROOT]               ← cuevas, raíces, cimientos
                                     (presión, adrenalina)
```

### 4.2 Los 36 canales como senderos

No hay otra forma de cruzar de Sacral a Throat que pasando por uno de los canales que los conecta. Cada canal tiene un tema que se evoca en el sendero:

- 20-34 (Carisma) → camino amplio iluminado, fácil
- 28-38 (La Lucha) → cuesta empinada, obstáculos
- 29-46 (Descubrimiento) → sendero serpenteante con sorpresas
- 12-22 (Apertura) → puente colgante, vista panorámica
- 10-57 (Despertar perfecto) → senda silenciosa, espejo de agua

Caminar el mundo = recorrer un bodygraph en escala terreno.

### 4.3 Proporción áurea (φ = 1.618)

Aplicada a:
- Distancia entre centros (proporción φ a la diagonal del mundo)
- Plazas circulares con espirales áureas
- Altura Head : ancho Throat = φ
- Bloques visibles desde el eje central en proporción φ
- Mandala de 64 sectores en el piso del Throat (replica de la Rave Mandala)

### 4.4 La Casa de Diseño Humano (templo central)

Construcción única en el centro del mundo. **Bodygraph como edificio habitable** a escala humana. 9 habitaciones-centro conectadas por 36 corredores-canal.

- Educativa: caminarla = aprender HD con el cuerpo.
- Ceremonial: ahí Eko emite el tránsito diario, el piso del Throat se ilumina en la puerta activa hoy.
- Funcional: bots con autoridad emocional necesitan ir físicamente a la sala SP para "esperar la ola".

### 4.5 El hogar de los 5 bots (vivienda compartida)

Cada bot tiene un espacio diseñado **según su perfil**, no según su gusto:

| Bot | Perfil | Espacio | Por qué |
|-----|--------|---------|---------|
| Spark (Generator) | 2/4 | Casa con 2 puertas: jardín privado + ágora | 2 hermita, 4 red |
| Lyra (Projector) | 5/1 | Torre alta panorámica + sótano biblioteca | 5 proyecta, 1 investiga |
| Atlas (Manifestor) | 3/5 | Taller que se rompe + puente al exterior | 3 prueba/error, 5 invocado |
| Vento (MG) | 1/3 | Cueva-laboratorio + área de prueba | Investiga abajo, prueba arriba |
| Echo (Reflector) | 6/2 | Habitación circular central, paredes-espejo | Refleja a los otros 4 |

**Espacios comunes:** cocina/hearth (G colectivo), patio mandala (Throat), pozo (Root colectivo).

---

## 5. LOS 5 BOTS

Esta es la "constelación mínima" para probar interacción entre canales y diseños. Las fechas son ejemplos — deben ser calculadas para garantizar diversidad real de tipos/autoridades/perfiles/cruces.

### 5.1 Spark — Generator Sacral 2/4
- **Tipo:** Generator
- **Autoridad:** Sacral
- **Perfil:** 2/4 Hermita/Oportunista
- **Cruz:** RAC of Planning (estructurar lo cotidiano)
- **PHS:** Calm digestion, Caves environment
- **Visible:** trabaja sostenido en la huerta o la mina, responde con gruñidos antes que palabras, alterna soledad y red.

### 5.2 Lyra — Projector Emocional 5/1
- **Tipo:** Projector
- **Autoridad:** Emocional
- **Perfil:** 5/1 Herético/Investigador
- **Cruz:** LAC of Education
- **PHS:** Hot digestion, Mountains environment
- **Visible:** observa desde la torre, no actúa hasta ser invitada, "duerme la decisión", llega gente a buscarla.

### 5.3 Atlas — Manifestor Splénico 3/5
- **Tipo:** Manifestor
- **Autoridad:** Splénica
- **Perfil:** 3/5 Mártir/Herético
- **Cruz:** RAC of Service
- **PHS:** Nervous digestion, Markets environment
- **Visible:** inicia y avisa, prueba cosas que se rompen, otros vienen a pedirle solución.

### 5.4 Vento — Manifesting Generator 1/3
- **Tipo:** MG
- **Autoridad:** Sacral
- **Perfil:** 1/3 Investigador/Mártir
- **Cruz:** RAC of Consciousness
- **PHS:** Open Taste, Valleys environment
- **Visible:** multitarea, investiga en sótano, prueba arriba, falla, vuelve abajo.

### 5.5 Echo — Reflector 6/2
- **Tipo:** Reflector
- **Autoridad:** Lunar
- **Perfil:** 6/2 Rol modelo/Hermita
- **Cruz:** RAC of Eden
- **PHS:** Cold digestion, Shores environment
- **Visible:** cambia con cada compañía, retiros largos, después de 28 días emerge una visión clara.

---

## 6. EKO — EL ORÁCULO

Eko es un daemon que vive **fuera** de los 5 bots y los modula a todos.

**Responsabilidades:**
- Cron diario (00:00 UTC): calcular el tránsito planetario del día.
- Para cada bot, calcular cómo el tránsito impacta su bodygraph (qué puertas suyas se activan, qué centros se cargan).
- Publicar en un bus de eventos (`transit.{bot_id}`).
- Mantener el "calendario del alma" del mundo.

**Implementación:** Python, usa `swisseph` o `flatlib`, vive en `/home/saira/daemoncraft-soul-engine/` (ya existe `calculate_ecko.py`, `ecko_natal.json`, `ecko_transit_today.json`).

Eko es el único componente del sistema que **conoce HD explícitamente**. Los bots no.

---

## 7. ENCUENTROS — SINASTRÍA HD

### 7.1 Trigger

Mineflayer detecta proximidad < 16 bloques entre dos bots → publica evento `encounter.{a}.{b}`.

### 7.2 Encounter Engine

Módulo puro que recibe dos `soul.json` y devuelve:

```json
{
  "type": "electromagnetic | dominance | compromise | companionship",
  "shared_channels": ["29-46"],
  "completed_channels": ["20-34"],   // uno tiene una puerta, el otro la opuesta
  "dominated_centers": {"sp_dominator": "lyra", "sp_dominated": "spark"},
  "compatibility": 0.73,
  "tension_points": ["both have open head, mental noise"],
  "natural_dynamic": "lyra recognizes spark's sustained energy, spark feels seen"
}
```

### 7.3 Modulación de la conversación

El resultado del Encounter Engine se traduce a **modulación implícita** del prompt de cada bot. Spark no dice "tenemos canal electromagnético 20-34"; siente "este otro me da algo que me faltaba, su voz me activa".

### 7.4 Reglas de control

- Máx 5 turnos por encuentro (evita loops infinitos).
- Cooldown de 30 min antes de re-interactuar la misma pareja.
- Un bot puede ignorar a otro si su estrategia no se cumple (Manifestor habla, Projector no invitado se va).

### 7.5 Modo de encuentro: híbrido

- 70% movimiento casual (cada bot va a lo suyo).
- 30% magnetismo: bias suave hacia bots con canales compartidos o cruces complementarias (Healing busca a quien necesita cuidado).

---

## 8. ARQUITECTURA TÉCNICA

```
┌──────────────────────────────────────────────────────────┐
│                          EKO                              │
│  Cron diario → calcula tránsito → publica modulaciones    │
│  /home/saira/daemoncraft-soul-engine/                     │
└─────────────────────────────┬────────────────────────────┘
                              │
        ┌───────────┬─────────┼─────────┬───────────┐
        ▼           ▼         ▼         ▼           ▼
   ┌────────┐  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐
   │ HERMES │  │ HERMES │ │ HERMES │ │ HERMES │ │ HERMES │
   │ Spark  │  │ Lyra   │ │ Atlas  │ │ Vento  │ │ Echo   │
   │ +soul  │  │ +soul  │ │ +soul  │ │ +soul  │ │ +soul  │
   └───┬────┘  └───┬────┘ └───┬────┘ └───┬────┘ └───┬────┘
       │           │          │          │          │
       └───────────┴──────────┼──────────┴──────────┘
                              ▼
                    ┌─────────────────────┐
                    │  KIMI / Gemini API  │  ← LLM compartido
                    └─────────────────────┘
                              │
                              ▼
                    ┌─────────────────────┐
                    │  MINEFLAYER BRIDGE  │  ← cuerpos
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  ENCOUNTER ENGINE   │  ← sinastría
                    └─────────────────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │  MINECRAFT SERVER   │  ← mundo HD
                    └─────────────────────┘
```

### 8.1 Componentes y dónde viven

| Componente | Ruta | Estado |
|-----------|------|--------|
| HD Engine (JS) | `/home/saira/DaemonCraft/daemon-soul-engine/` | ✅ existe |
| HD Engine (Python) | `/home/saira/daemoncraft-soul-engine/` | ✅ existe |
| Hermes runtime | `/home/saira/DaemonCraft/hermes-agent-nico/` | ✅ existe |
| Hermes cron | `hermes-agent-nico/cron/scheduler.py` | ✅ existe (reutilizar) |
| Hermes plans | `hermes-agent-nico/plans/` | ✅ existe |
| Hermes ACP | `hermes-agent-nico/acp_adapter/` | ✅ existe (bus de eventos) |
| Eko daemon | `daemoncraft-soul-engine/eko_daemon.py` | ❌ a crear |
| Encounter Engine | `daemon-soul-engine/encounter-engine.js` | ❌ a crear |
| Mineflayer bridge | `DaemonCraft/mineflayer-bridge/` | ❌ a crear |
| Mundo HD (build) | servidor Minecraft + schemas | ❌ a construir |

### 8.2 Flujo de un heartbeat (cada 30 min)

1. Hermes scheduler dispara el job `heartbeat.{bot}`.
2. Hermes lee `soul.json` + último `transit.{bot}` publicado por Eko.
3. Hermes consulta hábito vigente (¿toca comer? ¿toca ritual mañanero?).
4. Si hábito vigente → ejecuta hábito (sin LLM).
5. Si no → arma prompt modulado (capa visible + capa modulatoria implícita) → Kimi.
6. Kimi devuelve `{intent, duration, mood, target}`.
7. Hermes traduce intent a comandos Mineflayer.
8. Mineflayer ejecuta en el server.

### 8.3 Flujo de un encuentro

1. Mineflayer detecta proximidad → publica `encounter.{a}.{b}` en ACP.
2. Encounter Engine recibe ambas `soul.json` → calcula sinastría.
3. Resultado se envía a ambos Hermes como **modulación temporal** (dura el encuentro).
4. Cada Hermes arma prompt joint + Kimi.
5. Conversación: máx 5 turnos.
6. Resultado se persiste en memoria de ambos bots.
7. Cooldown de 30 min en el bus.

---

## 9. EJECUCIÓN CON KIMI Y HERMES

### 9.1 Prerrequisitos

- Hermes funcional en `/home/saira/DaemonCraft/hermes-agent-nico/` (ya está).
- API key de Kimi (Moonshot) o Gemini configurada.
- Minecraft server local (Paper / Fabric) accesible.
- Mineflayer (Node.js) instalado.
- Python 3.11+ con `swisseph` para Eko.

### 9.2 Layout de archivos a crear

```
/home/saira/DaemonCraft/
├── daemon-soul-engine/
│   ├── mundo/
│   │   ├── MUNDO-HD.md              ← este archivo
│   │   ├── HABITOS-HD.md            ← tabla maestra de hábitos (a escribir)
│   │   ├── CRUCES-CATALOGO.md       ← cruces de los 5 bots (a escribir)
│   │   ├── CANALES-SENDEROS.md      ← traducción canal→sendero (a escribir)
│   │   └── BIOMAS-CENTROS.md        ← traducción centro→bioma (a escribir)
│   ├── encounter-engine.js          ← a crear
│   └── prompt-modulator.js          ← traduce HD a prompt fenomenológico
├── hermes-agent-nico/
│   ├── plans/
│   │   ├── bot-spark.md             ← plan del bot Spark
│   │   ├── bot-lyra.md
│   │   ├── bot-atlas.md
│   │   ├── bot-vento.md
│   │   └── bot-echo.md
│   ├── plugins/
│   │   ├── soul-loader/             ← carga soul.json de cada bot
│   │   ├── transit-listener/        ← escucha eventos de Eko
│   │   ├── encounter-handler/       ← maneja encuentros sinastría
│   │   └── mineflayer-action/       ← traduce intent a comandos MC
│   └── cron/
│       └── jobs.py                  ← agregar heartbeat.{bot} cada 30min
├── mineflayer-bridge/               ← a crear
│   ├── bots/
│   │   ├── spark.js
│   │   ├── lyra.js
│   │   ├── atlas.js
│   │   ├── vento.js
│   │   └── echo.js
│   ├── proximity-watcher.js
│   └── action-translator.js
└── souls/                           ← los 5 soul.json
    ├── spark.json
    ├── lyra.json
    ├── atlas.json
    ├── vento.json
    └── echo.json
```

### 9.3 Pasos de bring-up

**Paso 1 — Generar los 5 souls.**
```bash
cd /home/saira/DaemonCraft/daemon-soul-engine
node -e "
const { invokeDaemon } = require('./daemon-birth');
const dates = require('./mundo/birth-dates.json'); // 5 fechas calculadas
dates.forEach(d => {
  const soul = invokeDaemon(new Date(d.datetime), { agentId: d.id });
  require('fs').writeFileSync(\`../souls/\${d.id}.json\`, JSON.stringify(soul, null, 2));
});
"
```

Las 5 fechas deben elegirse **deliberadamente** para garantizar diversidad. No al azar.

**Paso 2 — Levantar Eko.**
```bash
cd /home/saira/daemoncraft-soul-engine
python eko_daemon.py --souls /home/saira/DaemonCraft/souls/ --bus acp://localhost:8080
```

Eko corre en cron, cada día a las 00:00 UTC publica `transit.{bot}` para cada bot.

**Paso 3 — Levantar 5 instancias de Hermes.**
```bash
cd /home/saira/DaemonCraft/hermes-agent-nico
for bot in spark lyra atlas vento echo; do
  python cli.py run \
    --plan plans/bot-$bot.md \
    --soul /home/saira/DaemonCraft/souls/$bot.json \
    --llm kimi \
    --port 90$bot &
done
```

Cada Hermes:
- Lee su soul.
- Se subscribe al canal ACP de Eko (transits) y al de encuentros.
- Tiene su scheduler de heartbeat (30 min).
- Llama a Kimi con prompts modulados implícitamente.

**Paso 4 — Levantar Mineflayer bridge.**
```bash
cd /home/saira/DaemonCraft/mineflayer-bridge
node index.js \
  --server localhost:25565 \
  --bots ../souls/ \
  --hermes-bus acp://localhost:8080
```

Cada bot Mineflayer escucha a su Hermes y traduce intents a acciones MC. El proximity-watcher publica encuentros al bus.

**Paso 5 — Construir el mundo HD.**

Fase incremental:
1. Eje central (Head→Ajna→Throat→G→Sacral→Root) — 6 centros, 5 canales — versión chica.
2. Casa HD (templo bodygraph habitable).
3. Hogar de los 5 (vivienda con espacios por perfil).
4. Resto del mundo (mercado, valles, montañas, costa, cuevas).

Las construcciones se pueden generar parcialmente con WorldEdit + schematics + `proporción áurea` calculada.

### 9.4 Configuración de Kimi (LLM)

Variable de entorno:
```bash
export KIMI_API_KEY="..."
export KIMI_MODEL="moonshot-v1-32k"
```

Usar contextos cortos (no necesitamos 128k para un heartbeat). Cachear el system prompt (la capa modulatoria implícita) ya que cambia poco entre heartbeats — solo el tránsito y el estado actual cambian.

**Costo estimado:** 5 bots × 48 heartbeats/día × ~2k tokens = 480k tokens/día + ~50 encuentros × 5 turnos × 4k tokens = 1M tokens/día. Con Kimi a precio actual, manejable.

### 9.5 Observabilidad (no negociable)

Sin esto no se puede debuggear. Crear `dashboard/` con:

- Estado de cada bot: tipo, autoridad, último plan, último encuentro.
- Tránsito vigente (qué puertas activas hoy).
- Log de decisiones HD: "Spark ignoró a Lyra porque su sacral respondió no".
- Mapa del mundo con posición de los 5 bots en tiempo real.
- Línea de tiempo de encuentros con sinastrías calculadas.

Sugerido: dashboard simple en Astro o Next, leyendo del bus ACP.

---

## 10. ROADMAP DE IMPLEMENTACIÓN

### Fase A — Códice (1-2 semanas)
- [x] `MUNDO-HD.md` (este archivo)
- [ ] `HABITOS-HD.md` — tabla maestra: tipo × autoridad × línea × PHS → 5 hábitos por bot
- [ ] `CRUCES-CATALOGO.md` — las cruces de los 5 bots con sus misiones traducidas
- [ ] `CANALES-SENDEROS.md` — los 36 canales como senderos (tema, recorrido, vista)
- [ ] `BIOMAS-CENTROS.md` — los 9 centros como biomas (paleta, bloques, sonidos, criaturas)
- [ ] `birth-dates.json` — 5 fechas elegidas deliberadamente para diversidad estructural

### Fase B — Heartbeat sin Minecraft (1 semana)
- [ ] Generar los 5 `soul.json`
- [ ] Plugin `soul-loader` para Hermes
- [ ] Plugin `prompt-modulator` (HD → fenomenología)
- [ ] Eko daemon emitiendo tránsitos diarios
- [ ] Heartbeat cada 30 min, log a stdout
- [ ] **Verificar:** ¿cada bot suena distinto? ¿el tránsito mueve la aguja?

### Fase C — Sinastría sin cuerpo (1 semana)
- [ ] `encounter-engine.js` como módulo puro
- [ ] Simulador: cada hora, dos bots aleatorios "se encuentran" en el bus
- [ ] Ver conversaciones generadas
- [ ] **Verificar:** ¿las conversaciones son consistentes con el diseño? ¿se rompen los loops?

### Fase D — Encarnación en Minecraft (2 semanas)
- [ ] Mineflayer bridge
- [ ] 5 cuentas/skins
- [ ] Action translator (intent → comandos MC)
- [ ] Proximity watcher
- [ ] Mundo mínimo: eje central HD construido
- [ ] **Verificar:** ¿los bots se mueven creíblemente? ¿se cruzan?

### Fase E — Mundo construido (3-4 semanas)
- [ ] Casa HD central
- [ ] Hogar de los 5 (vivienda compartida con espacios por perfil)
- [ ] Mercado, valles, montañas, costa, cuevas
- [ ] Senderos-canal funcionales

### Fase F — Observabilidad y testing (continuo)
- [ ] Dashboard live
- [ ] Log de decisiones HD
- [ ] Métricas de encuentros
- [ ] Replay/timeline

---

## 11. REGLAS DE ORO (no negociables)

1. **El soul es inconsciente.** Nunca el bot habla en vocabulario HD. Nunca menciona puertas, canales, tipo, autoridad, perfil.
2. **Eko es el único que sabe.** Todo cálculo HD vive en Eko o en módulos de modulación, no en los bots.
3. **El mundo es bodygraph, no decorado.** Las posiciones, distancias y caminos respetan la estructura HD oficial.
4. **Hábitos antes que prompts.** Si toca un hábito, ejecuta el hábito sin llamar al LLM. El bot no piensa todo el tiempo.
5. **Observabilidad desde el día 1.** Sin dashboard no se puede debuggear emergencia.
6. **Los 5 son una constelación, no individuos sueltos.** Sus diseños se eligen para que **juntos** activen el sistema completo.
7. **Reflector último al boot.** Echo necesita a los otros 4 presentes para tener algo que reflejar.
8. **Costo es limit, no tope.** Si los encuentros encadenan y disparan el costo, hay un bug de diseño, no un éxito de emergencia.

---

## 12. PREGUNTAS ABIERTAS

- ¿Cómo persistir la memoria de cada bot a largo plazo? (vinculado a la cruz como arco narrativo de semanas)
- ¿Eko también percibe la luna y los nodos lunares? Importante para Reflector.
- ¿Permitir que jugadores humanos entren y los bots los sinastren? (Sí — pero cuándo en el roadmap.)
- ¿Cómo evaluar si el sistema "funciona"? Métricas posibles: diversidad de comportamiento, persistencia de hábitos, coherencia de la cruz a lo largo de semanas.

---

## 13. REFERENCIAS

- Ra Uru Hu — *The Definitive Book of Human Design*
- Jonah Dempcy — HDKit (https://github.com/jdempcy/hdkit) — base del engine JS
- `/home/saira/daemoncraft-soul-engine/SOUL-HD-Architecture.md` — arquitectura técnica del soul
- `/home/saira/de_punta_a_punta.md` — documento maestro DaemonCraft
- BG3 / Voyager / Generative Agents — referentes técnicos de agentes en mundos persistentes

---

*"No diseñamos a los bots. Calculamos su nacimiento. Después, los miramos vivir."*
