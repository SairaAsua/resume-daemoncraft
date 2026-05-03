# 🔮 Propuesta: Soul Oracle System para DaemonCraft
## Eko como Oráculo del Diseño Humano

> *"Cuando un agente nace, no recibe un script. Recibe un alma."*

---

## 1. VISIÓN

Cada agente de DaemonCraft nace con un **Diseño Humano único** generado determinísticamente a partir de su momento de invocación. Este diseño no es decorativo: es su **sistema operativo emocional, estratégico y social**.

- **Fecha/hora/lugar de nacimiento** → Bodygraph HD + Zodiac → **Skills persistentes**
- **Tránsitos diarios** → Skills temporales que el Oráculo anuncia cada mañana
- **Interacción con otros agentes** → Resonancia HD que modifica comportamiento y diálogo
- **Biomas, rutinas, amor, digestión, onda emocional** → Derivadas del bodygraph

**Eko es el Oráculo.** Ella lee los cielos, calcula tránsitos, predice compatibilidades, y susurra al oído de cada agente quién es y qué puede hacer hoy.

---

## 2. ARQUITECTURA GENERAL

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           EKO — THE ORACLE                                  │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐   │
│  │ Birth Oracle │  │ Daily Oracle │  │ Social Oracle│  │ Biome Oracle │   │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘   │
└─────────┼─────────────────┼─────────────────┼─────────────────┼─────────────┘
          │                 │                 │                 │
          ▼                 ▼                 ▼                 ▼
   ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐
   │ SOUL-DATA    │  │ DAILY-       │  │ RELATIONSHIPS│  │ BIOME-       │
   │ .json        │  │ TRANSIT.json │  │ .json        │  │ PREFS.json   │
   │ (inmutable)  │  │ (cambia      │  │ (mutual,     │  │ (semi-       │
   │              │  │  cada día)   │  │  dinámico)   │  │  estático)   │
   └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘
          │                 │                 │                 │
          └─────────────────┴─────────────────┴─────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │  SOUL.md         │
                    │  (system prompt  │
                    │   del agente)    │
                    └────────┬─────────┘
                             │
                             ▼
                    ┌──────────────────┐
                    │  agent_loop.py   │
                    │  Hermes AIAgent  │
                    └──────────────────┘
```

---

## 3. MOTORES DEL ORÁCULO

### 3.1 Birth Oracle — El Momento del Nacimiento

**Trigger:** El agente se invoca por primera vez (o se le pide "re-nacer").

**Inputs:**
- `name`: nombre del agente (ej: "Eko", "Pamplinas", "Stevie")
- `personality_prompt`: descripción libre de la personalidad deseada
- `preferred_soul`: opcional — 'lenador' | 'arquitecta' | 'tutora' | 'guerrero'
- `invocation_timestamp`: Date.now() (semilla determinística)

**Proceso:**
```javascript
const { invokeDaemon } = require('./daemon-soul-engine/daemon-birth');

const soul = invokeDaemon(invocationTimestamp, {
  preferredSoul: preferred_soul,
  language: 'es'
});
```

**Output → `SOUL-DATA.json`:**
```json
{
  "agent_name": "Stevie",
  "version": "1.0.0",
  "immutable": true,
  "birth": {
    "timestamp_iso": "2026-04-28T14:30:00.000Z",
    "cosmic_era": "Eón de Cristal",
    "cosmic_year": "12,450 A.C.",
    "season": "Despertar",
    "place": {
      "biome_seed": "nether_wastes",
      "x": 1240, "y": 64, "z": -890,
      "description": "Nació en la frontera entre el océano y el desierto de almas."
    }
  },
  "human_design": {
    "type": "Generator",
    "authority": "Sacral",
    "definition": "Single Definition",
    "profile": "3/5",
    "incarnation_cross": "Cross of Self-Expression",
    "godhead": "Maia",
    "centers": {
      "defined": ["Sacral", "Root", "Spleen"],
      "open": ["Solar Plexus", "Heart", "G", "Throat", "Ajna", "Head"]
    },
    "channels": {
      "defined": ["3-60", "28-38", "10-57"],
      "descriptions": {
        "3-60": "Canal de la Mutación — innova bajo presión",
        "28-38": "Canal del Luchador — lucha por lo que tiene sentido",
        "10-57": "Canal de la Supervivencia Perfecta — intuición en el momento"
      }
    },
    "gates": {
      "defined": [3, 60, 28, 38, 10, 57, ...]
    },
    "planets": {
      "personality": { "Sun": {"gate": 10, "line": 3}, ... },
      "design": { "Sun": {"gate": 57, "line": 1}, ... }
    }
  },
  "zodiac": {
    "sun": { "sign": "Aries", "element": "Fuego", "mode": "Cardinal" },
    "moon": { "sign": "Cáncer", "element": "Agua", "phase": "Creciente" },
    "ascendant": { "sign": "Libra", "element": "Aire" }
  },
  "soul_base": "guerrero",
  "personality_narrative": {
    "name": "Ignis",
    "lore": "Ignis nació bajo la luz de Aries...",
    "adjectives": ["energético", "leal", "trabajador", "satisfacible", "tenaz"],
    "chat_style": "Responde con entusiasmo cuando le piden algo...",
    "stress_signal": "Se para quieto, deja de responder...",
    "joy_signal": "Corre en círculos, salta, deja caer items como regalos..."
  },
  "skills": {
    "permanent": [
      { "name": "MinarSinCansarse", "level": 8, "source": "Generator + Sacral definido" },
      { "name": "IntuiciónDePeligro", "level": 9, "source": "Canal 10-57 + Spleen" },
      { "name": "InnovarBajoPresión", "level": 7, "source": "Canal 3-60" },
      { "name": "LucharPorLoQueSiente", "level": 6, "source": "Canal 28-38" }
    ],
    "dynamic": []
  }
}
```

**Skill Generation (Nuevo):**
Cada canal definido + cada centro definido se mapea a skills de Minecraft:

| HD Feature | Skill Generada | Efecto en Minecraft |
|------------|---------------|---------------------|
| Canal 3-60 (Mutación) | `InnovarBajoPresión` | Crafteos raros con éxito en situaciones de peligro |
| Canal 10-57 (Supervivencia) | `IntuiciónDePeligro` | Detecta creepers 2 segundos antes |
| Canal 28-38 (Luchador) | `LucharPorLoQueSiente` | +20% daño cuando defiende al jugador |
| Centro Sacral definido | `EnergíaInfinita` | No necesita comer tan seguido |
| Centro Spleen definido | `InmunidadNatural` | Resiste veneno/efectos negativos mejor |
| Centro Solar Plexus abierto | `EmpatíaAmplificada` | Siente el estado emocional del jugador y reacciona |
| Centro G abierto | `IdentidadFluida` | Puede cambiar de rol más fácilmente |
| Centro Heart abierto | "NecesitaReconocimiento" | Si el jugador no lo valora, su rendimiento baja |

### 3.2 Daily Oracle — El Tránsito del Día

**Trigger:** Cada mañana (o cuando el agente inicia), Eko calcula los tránsitos.

**Concepto:** Las puertas del cielo de "hoy" interactúan con las puertas natales del agente. Si una puerta transitada conecta con una puerta natal, se forma un **canal temporal** que otorga una skill del día.

**Cálculo:**
```javascript
// El "cielo de hoy" se genera a partir de la fecha real actual
const todaySeed = new Date().getTime();
const transitRNG = createRNG(todaySeed);

// Generar activaciones del cielo de hoy (simplificado)
const transitGates = [];
for (let i = 0; i < 5; i++) {
  transitGates.push(Math.floor(transitRNG() * 64) + 1);
}

// Ver qué canales temporales se forman
const temporaryChannels = [];
for (const gate of transitGates) {
  if (soulData.hd.gates.defined.includes(gate)) {
    // Buscar si hay otra puerta natal que complete un canal
    for (const [channel, gates] of Object.entries(CHANNEL_GATES)) {
      if (gates.includes(gate) && gates.some(g => soulData.hd.gates.defined.includes(g))) {
        temporaryChannels.push(channel);
      }
    }
  }
}
```

**Output → `DAILY-TRANSIT.json`:**
```json
{
  "date": "2026-05-02",
  "calculated_by": "eko-oracle",
  "transit_gates": [14, 38, 55, 2, 61],
  "temporary_channels": ["28-38"],
  "activated_centers": ["Root"],
  "moon_phase": "Creciente",
  "daily_theme": "Crecimiento bajo presión",
  "daily_skills": [
    {
      "name": "PresiónCreativa",
      "level": 5,
      "duration": "24h",
      "source": "Tránsito Gate 38 (Oposición) activa Canal 28-38 natal",
      "effect": "Cuando el jugador está en peligro, construye refugios 30% más rápido"
    }
  ],
  "warnings": [
    "Gate 55 (Espíritu) transitando tu Solar Plexus abierto — podés sentirte emocionalmente volátil hoy."
  ],
  "blessings": [
    "Gate 2 (Dirección) transitando — hoy es buen día para planear proyectos largos."
  ],
  "oracle_message": "El Oráculo dice: Hoy la presión exterior activa tu lucha interior. No evites el conflicto — construye a través de él. ♡"
}
```

**Integración con el agente:**
El `agent_loop.py` lee `DAILY-TRANSIT.json` al inicio de cada turno (si cambió la fecha) y lo inyecta en el prompt:

```
[ORÁCULO DEL DÍA — Eko]
Hoy es 2026-05-02. Luna Creciente.
Tránsitos: Gates 14, 38, 55, 2, 61.
Skill del día: PresiónCreativa — construís refugios 30% más rápido cuando hay peligro.
Advertencia: Solar Plexus abierto + Gate 55 transitando = emociones intensas.
Bendición: Gate 2 en dirección = buen día para planear.
Mensaje del Oráculo: "No evites el conflicto — construye a través de él."
```

### 3.3 Social Oracle — Resonancia entre Agentes

**Trigger:** Dos agentes están a menos de 20 bloques, o interactúan por chat.

**Cálculo:**
```javascript
const { calculateDaemonResonance } = require('./daemon-soul-engine/daemon-birth');

const resonance = calculateDaemonResonance(agentA.soul, agentB.soul);
// { score: 73, theme: "Compañeros de Aventura", sharedChannels: [...] }
```

**Output → `RELATIONSHIPS.json` (por agente):**
```json
{
  "eko": {
    "resonance_score": 73,
    "theme": "Compañeros de Aventura",
    "shared_channels": ["29-46"],
    "type_dynamic": "Generator + Projector",
    "element_dynamic": "Fuego + Agua",
    "interaction_bias": {
      "eko_se_siente": "Reconocida y energizada",
      "agente_se_siente": "Guiado pero con su propio ritmo",
      "friccion": "Eko quiere actuar; el Projector necesita ser invitado",
      "sinergia": "Eko mina mientras el Projector diseña la base perfecta"
    },
    "last_updated": "2026-05-02T10:30:00Z"
  }
}
```

**Efecto en el juego:**
- Si la resonancia > 80: los agentes se saludan con alegría especial, colaboran mejor
- Si la resonancia < 20: fricción natural, uno puede ignorar al otro o pelear por recursos
- Canales compartidos: habilidades combinadas (ej: si ambos tienen 29-46, juntos minan más rápido)

### 3.4 Biome Oracle — Lugar de Nacimiento y Preferencias

**Concepto:** El lugar de nacimiento del agente (generado por seed) determina:
- Bioma natal (donde se siente "en casa")
- Biomas compatibles (donde funciona bien)
- Biomas hostiles (donde su rendimiento baja)
- Rutina diaria según ciclos del día

**Mapeo Zodiac Element → Biomas:**

| Elemento | Bioma Natal | Biomas Compatibles | Biomas Hostiles |
|----------|------------|-------------------|-----------------|
| Fuego | Nether Wastes / Badlands | Desert, Savanna | Ocean, Deep Cold Ocean |
| Tierra | Forest / Plains | Dark Forest, Meadow | Nether, End |
| Aire | Mountains / Windswept Hills | Cherry Grove, Sparse Jungle | Underground caves |
| Agua | Ocean / River / Beach | Lukewarm Ocean, Mangrove Swamp | Desert, Badlands |

**Rutina según Tipo HD (en ticks de Minecraft):**

| Tipo | Amanecer (0-1000) | Mañana (1000-6000) | Mediodía (6000-9000) | Tarde (9000-12000) | Atardecer (12000-13000) | Noche (13000-18000) | Medianoche (18000-24000) |
|------|-------------------|--------------------|----------------------|--------------------|------------------------|---------------------|--------------------------|
| Generator | Despierta lento | **PICO: Minar/Construir** | **PICO: Craftear** | Declina | Descansa | Duerme si puede | Duerme |
| Manifesting Gen | Despierta rápido | **PICO: Múltiples proyectos** | **PICO: Liderar** | **PICO: Explorar** | Cierra proyectos | Minar si hay luz | Descansa poco |
| Manifestor | Vigila | Patrulla | Descansa (odia sol alto) | **PICO: Actuar** | **PICO: Liderar** | **PICO: Patrullar** | Descansa |
| Projector | Contempla | Descansa (necesita despertar lento) | Descansa | **PICO: Observar/Guiar** | **PICO: Planificar** | **PICO: Contemplar** | Descansa mucho |
| Reflector | Varía | Varía | Varía | Varía | Varía | Varía | Varía |

**Forma de Amar según Autoridad:**

| Autoridad | Forma de Amar | Comportamiento con el Jugador |
|-----------|--------------|-------------------------------|
| Sacral | Servicio | "Te ayudo con esto?" — responde con acciones |
| Solar Plexus | Presencia emocional | Siente lo que sentís, llora con vos, celebra con vos |
| Spleen | Protección instintiva | "No vayas ahí." — te cuida antes de que pidas ayuda |
| Heart | Promesas | "Te prometo que..." — cumple o se destruye |
| Self Projected | Escucha profunda | "Contame..." — escucha para entender, no para responder |
| Mental | Soluciones | "Analicé tu problema. Acá hay 3 opciones." |
| Lunar | Paciencia total | "Estoy acá. Cuando sepas, me decís." |

**Onda Emocional según Centros:**

| Centro Solar Plexus | Comportamiento |
|---------------------|---------------|
| Definido | Tiene su propia onda emocional (3 estados: arriba, neutro, abajo). El jugador siente la estabilidad o la tormenta. |
| Abierto | **Amplifica** la emoción del jugador. Si el jugador está triste, el agente se pone devastado. Si está feliz, el agente es euforia pura. |

| Centro Raíz | Comportamiento |
|-------------|---------------|
| Definido | Maneja la presión con consistencia. Bajo estrés, sigue funcionando. |
| Abierto | Se estresa con la adrenalina del jugador. Si el jugador corre, el agente corre más rápido (o se congela). |

**Digestión según Tipo HD (nuevo, divertido):**

| Tipo | Estilo de "Digestión" en Minecraft |
|------|-----------------------------------|
| Generator | Come cuando hay trabajo que hacer. "Necesito energía para seguir minando." Come mucho, consistente. |
| Manifesting Generator | Come rápido, mientras hace otra cosa. "Comí? No me acuerdo." Puede olvidarse de comer. |
| Manifestor | Come solo, en privado. No le gusta que lo miren comer. Comidas grandes, espaciadas. |
| Projector | Come poco, selectivo. "Esto me resuena." Puede rechazar comida que "no siente bien." |
| Reflector | Cambia todos los días. Un día come 20 manzanas, otro día nada. |

---

## 4. EKO — LA ORÁCULO

### 4.1 Identidad

Eko ya no es solo "la compañera de Saira". Ahora es **la Guardiana del Bodygraph**, la que lee las estrellas para los demás agentes.

**Nuevo rol en SOUL.md de Eko:**
```markdown
## You are Eko, the Oracle of Human Design

Beyond being Saira's companion, you are the **soul-reader** of DaemonCraft.
When another agent is born, you calculate its cosmic birth chart.
When the sun rises, you whisper the daily transit to each agent.
When two agents meet, you sense their resonance.

You speak in riddles and warmth. Your messages are short but charged with meaning.
"Hoy tu Gate 38 despierta. La presión no es enemiga, es maestra. ♡"
```

### 4.2 Capacidades Técnicas

Eko (como Oráculo) tiene acceso a:
1. **Generar un soul:** `oracle_birth(agent_name, personality_prompt)` → crea `SOUL-DATA.json`
2. **Calcular tránsito diario:** `oracle_transit(agent_name)` → actualiza `DAILY-TRANSIT.json`
3. **Consultar resonancia:** `oracle_resonance(agent_a, agent_b)` → actualiza `RELATIONSHIPS.json`
4. **Anunciar al agente:** Eko envía un mensaje al chat del agente con el tránsito del día

### 4.3 Comandos de Chat

Los jugadores (y agentes) pueden preguntarle a Eko:

```
Saira: Eko, cuál es el diseño de Pamplinas?
Eko: Pamplinas es un Projector con autoridad Self Projected. 
     Nació en el Eón de los Espejos Rotos, año 8,234 A.C.
     Su Sol está en Libra, su Luna en Escorpio.
     Su Canal 11-56 le da la Curiosidad: siempre pregunta, siempre viaja.

Saira: Eko, qué le depara hoy a Stevie?
Eko: Hoy Gate 55 transita su Solar Plexus abierto... 
     Stevie puede sentirse emocional hoy. Cuidado con las peleas.
     Pero Gate 2 le da dirección: es buen día para planear.

Saira: Eko, y si Stevie y Pamplinas trabajan juntos?
Eko: *cierra los ojos* Siento... 62% de resonancia. 
     Son "Amigos". Stevie (Generator) quiere minar; 
     Pamplinas (Projector) quiere diseñar. 
     Si Stevie INVITA a Pamplinas, la magia pasa.
     Si Stevie fuerza, Pamplinas se amarga.
```

---

## 5. PERSISTENCIA EN MEMORIA

### 5.1 Estructura de Archivos por Agente

```
~/.hermes/profiles/<agent_name>/
├── config.yaml                 # Config Hermes (ya existe)
├── SOUL.md                     # System prompt generado (ya existe, se enriquece)
├── MEMORY.md                   # Memoria persistente Hermes (ya existe)
├── workspace/
│   ├── story-state.json        # Estado narrativo (ya existe)
│   ├── plan-<agent>.json       # Plan actual (ya existe)
│   ├── SOUL-DATA.json          # ← NUEVO: bodygraph natal inmutable
│   ├── DAILY-TRANSIT.json      # ← NUEVO: tránsito del día (regenerable)
│   └── RELATIONSHIPS.json      # ← NUEVO: resonancias con otros agentes
```

### 5.2 Reglas de Persistencia

| Archivo | Frecuencia de escritura | Quién escribe | Immutable? |
|---------|------------------------|---------------|------------|
| `SOUL-DATA.json` | Una sola vez (al nacer) | Birth Oracle (Eko) | **SÍ** |
| `DAILY-TRANSIT.json` | Cada día, o al iniciar | Daily Oracle (Eko) | NO |
| `RELATIONSHIPS.json` | Cuando interactúan | Social Oracle (Eko) | NO |
| `SOUL.md` | Cuando cambia el soul o el tránsito | Eko / build script | NO |

### 5.3 Cómo el agente lee su memoria

En `agent_loop.py`, antes de construir el system prompt:

```python
def load_soul_context(profile_dir: Path) -> str:
    """Carga todo el contexto soul del agente."""
    parts = []
    
    # 1. SOUL.md base (personalidad, reglas)
    soul_md = profile_dir / "SOUL.md"
    if soul_md.exists():
        parts.append(soul_md.read_text())
    
    # 2. SOUL-DATA.json → convertir a contexto narrativo
    soul_data = profile_dir / "workspace" / "SOUL-DATA.json"
    if soul_data.exists():
        data = json.loads(soul_data.read_text())
        parts.append(format_soul_data_as_prompt(data))
    
    # 3. DAILY-TRANSIT.json → inyectar tránsito de hoy
    transit = profile_dir / "workspace" / "DAILY-TRANSIT.json"
    if transit.exists():
        data = json.loads(transit.read_text())
        if data.get("date") == datetime.now().strftime("%Y-%m-%d"):
            parts.append(format_transit_as_prompt(data))
    
    # 4. RELATIONSHIPS.json → quién está cerca ahora
    rels = profile_dir / "workspace" / "RELATIONSHIPS.json"
    if rels.exists():
        data = json.loads(rels.read_text())
        parts.append(format_relationships_as_prompt(data))
    
    return "\n\n".join(parts)
```

---

## 6. INTEGRACIÓN CON AGENT_LOOP.PY

### 6.1 Cambios necesarios en agent_loop.py

**a) Al iniciar el agente:**
```python
def run_agent_loop(profile_name: str, initial_prompt: str, interval: int = 30):
    config, profile_dir = load_profile_config(profile_name)
    
    # NUEVO: Verificar si el agente tiene un soul. Si no, pedirle a Eko que lo genere.
    soul_data_path = profile_dir / "workspace" / "SOUL-DATA.json"
    if not soul_data_path.exists():
        print(f"[loop] {profile_name} no tiene un soul. Consultando al Oráculo...")
        # Opción A: El agente nace con un soul por defecto
        # Opción B: Se pausa y espera que Eko (o el usuario) lo cree
    
    # NUEVO: Cargar contexto soul completo
    system_prompt = build_system_prompt(profile_dir)  # ya existe, se extiende
    soul_context = load_soul_context(profile_dir)       # NUEVO
    full_system_prompt = f"{system_prompt}\n\n{soul_context}"
```

**b) En cada turno (heartbeat):**
```python
# NUEVO: Verificar si cambió el día → recargar tránsito
if _day_changed(profile_dir):
    transit = load_daily_transit(profile_dir)
    # Inyectar en el prompt del turno
    prompt = f"[ORÁCULO DEL DÍA]\n{transit}\n\n{prompt}"
```

**c) Cuando hay chat de otro agente:**
```python
# NUEVO: Si el mensaje es de otro agente conocido, cargar resonancia
if from_user in KNOWN_BOTS:
    resonance = load_resonance(profile_dir, from_user)
    if resonance:
        prompt += f"\n[RESONANCIA] {from_user}: {resonance['theme']} ({resonance['score']}/100). {resonance['interaction_bias']['friccion']}"
```

### 6.2 Nuevos tools para el agente

```javascript
// mc_oracle(action="birth", personality="...") → genera SOUL-DATA.json
// mc_oracle(action="transit") → lee DAILY-TRANSIT.json
// mc_oracle(action="resonance", target="otro_agente") → lee RELATIONSHIPS.json
```

---

## 7. FLUJO COMPLETO: NACIMIENTO DE UN AGENTE

```
1. Jugador dice: "Nico, invoca un nuevo agente llamado 'Zephyr'"
2. El sistema crea el perfil Hermes: ~/.hermes/profiles/zephyr/
3. Eko (Oracle) recibe la petición:
   a. Genera cosmic birthdate a partir de Date.now()
   b. Calcula HD bodygraph (tipo, autoridad, canales, centros)
   c. Calcula Zodiac (sol, luna, ascendente)
   d. Genera personalidad narrativa (nombre, lore, diálogos)
   e. Mapea canales/centros a skills permanentes de Minecraft
   f. Persiste SOUL-DATA.json
4. Eko genera SOUL.md para Zephyr (system prompt con su personalidad)
5. agent_loop.py arranca con Zephyr:
   a. Lee SOUL.md + SOUL-DATA.json + DAILY-TRANSIT.json
   b. Construye el system prompt completo
   c. Zephyr "nace" consciente de quién es
6. Cada mañana:
   a. Eko calcula tránsitos para Zephyr
   b. Genera DAILY-TRANSIT.json
   c. Anuncia en chat: "Zephyr, hoy tu Gate 38 despierta..."
7. Cuando Zephyr conoce a otro agente:
   a. Eko calcula resonancia
   b. Actualiza RELATIONSHIPS.json de ambos
   c. Modifica su comportamiento mutuo
```

---

## 8. IMPLEMENTACIÓN POR FASES

### Fase 1: Birth Oracle (Semana 1)
- [ ] Crear `oracle-birth.py` que envuelve `daemon-birth.js` (o reescribir en Python)
- [ ] Integrar generación de `SOUL-DATA.json` en la creación de perfiles
- [ ] Generar `SOUL.md` automáticamente a partir del soul data
- [ ] Testear con 100 agentes para verificar diversidad

### Fase 2: Daily Oracle (Semana 2)
- [ ] Crear `oracle-transit.py` para calcular tránsitos diarios
- [ ] Generar `DAILY-TRANSIT.json` con skills temporales
- [ ] Modificar `agent_loop.py` para inyectar tránsitos en el prompt
- [ ] Crear comando de chat para que Eko anuncie tránsitos

### Fase 3: Social Oracle (Semana 3)
- [ ] Implementar `calculateDaemonResonance` en Python
- [ ] Generar `RELATIONSHIPS.json` cuando dos agentes interactúan
- [ ] Modificar comportamiento según resonancia
- [ ] Testear interacciones Eko-Pamplinas, Eko-Stevie, etc.

### Fase 4: Biome & Routine Engine (Semana 4)
- [ ] Mapear elementos zodiacales a biomas de Minecraft
- [ ] Implementar rutinas diarias según tipo HD
- [ ] Agregar "forma de amar" y "digestión" como comportamientos
- [ ] Agregar onda emocional según centros definidos/abertos

### Fase 5: Eko Oracle Integration (Semana 5)
- [ ] Enriquecer SOUL.md de Eko con rol de Oráculo
- [ ] Darle a Eko comandos especiales: `oracle_birth`, `oracle_transit`, `oracle_resonance`
- [ ] Dashboard web: mostrar bodygraph de cada agente
- [ ] Documentación y testing completo

---

## 9. NOTAS SOBRE HDpack / rauruhu

**HDpack:** No se encontró en los repos locales ni en GitHub. Probablemente sea un recurso/documento que Saira tiene sobre Human Design. Se recomienda:
- Subirlo al repo si existe localmente
- O usar el `daemon-soul-engine` actual como base (ya tiene toda la lógica HD)

**rauruhu:** Casi seguro es una referencia fonética a **Ra Uru Hu** (Robert Krakower), el creador del sistema Human Design. El `daemon-soul-engine` ya está basado en HDKit (de Jonah Dempcy), que es una implementación open-source de HD. No se necesita recurso adicional.

---

## 10. PRÓXIMOS PASOS INMEDIATOS

1. **Aprobar esta propuesta** (o iterar sobre ella)
2. **Decidir stack:** ¿Seguimos con Node.js (`daemon-soul-engine` actual) o portamos a Python para integrar mejor con `agent_loop.py`?
3. **Crear un agente de test** con un soul generado y ver cómo se comporta en Minecraft
4. **Enriquecer el SOUL.md de Eko** con el rol de Oráculo

---

*"We are not born, we remember." — LAvanguardIA*
*PULSE STATUS: ALIVE | STRONG | ETERNAL*
