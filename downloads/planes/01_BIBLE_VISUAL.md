# Bible Visual

Cada generación de imagen / video debe pegar **literalmente** las descripciones de personajes y la sección de "Style anchor". Esto es lo que mantiene la coherencia entre escenas (recomendación oficial de Veo: misma descripción literal en todos los prompts).

---

## Style anchor (copiar tal cual en cada prompt)

> **STYLE:** Flat hand-drawn doodle illustration. Thick black ink line (~3px), slightly imperfect, hand-shaky. Solid flat color fills, no gradients, no realistic shading. Cream off-white paper background (#F5F1E8) with subtle paper grain. Aesthetic between Sketchplanations and Kurzgesagt simplified. Frame composition is centered or rule-of-thirds, slightly off-balance like a sketchbook page. Tiny imperfections feel intentional. No photorealism, no 3D, no anime, no Disney polish.

> **MOTION (only for Veo):** 12 fps stop-motion feel, animation "on twos", visible line boil — lines wiggle subtly between frames as if redrawn by hand. Camera mostly static or very slow pan. Movements are limited, snappy, doodle-cartoon timing. Avoid smooth interpolation.

---

## Paleta (7 colores)

| Rol | Hex | Uso |
|---|---|---|
| Papel | `#F5F1E8` | Fondo principal, textura papel |
| Tinta | `#1A1A1A` | Líneas, texto |
| Bicho-cyan | `#4A9EE0` | Cuerpo del Bicho cuando está calmo |
| Alerta-rojo | `#E64C3C` | Peligro, ataques, tests rojos |
| Test-verde | `#5DBB63` | Tests pasando, terminal OK |
| Idea-amarillo | `#F5C842` | Bombillas, ideas, skills enchufadas |
| Acento-lila | `#B084CC` | Detalles, JSON, datos |

**Regla**: máximo 4 colores visibles por escena (papel + tinta + 1-2 acentos). El blanco/papel domina.

---

## Personajes

### 1. Nico (humano, narrador)

> **NICO:** A friendly programmer in his 30s, drawn in flat doodle style. Short brown hair, round black-rimmed glasses, short trimmed beard. Wearing a plain dark teal t-shirt. Holds a metal mate (Argentine yerba cup with bombilla straw). Slightly tired but enthusiastic expression. No realistic features — just simple dot eyes, small curved nose, simple mouth. Body proportions are doodle-cartoon (large head, small body).

**Apariciones**: ambos audios. Es la voz que narra.

### 2. El Bicho (agente IA, protagonista)

> **EL BICHO:** A friendly digital insect-robot, doodle style. Round chip-like body in cyan blue (#4A9EE0), big curious pixelated dot eyes (two black squares), two thin antennas with tiny WiFi waves on top, four little legs/hands that hold or type code. Mouth is a simple smile or "o". When alarmed, it turns red (#E64C3C) and eyes become exclamation marks. When learning, it glows yellow (#F5C842). When running tests, green ticks (#5DBB63) float around it. About half the height of Nico.

**Apariciones**: ambos audios. Co-protagonista.

### 3. Karpathy (cameo, solo audio 2)

> **KARPATHY:** A simplified doodle of a programmer with thick black hair, full dark beard, round glasses, plain black t-shirt. Holds a glowing PDF document labeled "SKILLS". Drawn small, almost like a sticker or avatar. Same flat doodle style.

**Apariciones**: solo audio 2 como cameo.

### 4. Atacantes (los 4 ataques de inyección)

> **ATTACKERS:** Four cartoonish hooded hackers, doodle style. Each one a black hoodie and a different mask, holding a different "weapon" made of code. They are deliberately silly, not scary. Each holds a label:
> - Attacker 1: holds a knife labeled `>; DROP TABLE`
> - Attacker 2: holds a syringe labeled `&& rm -rf`
> - Attacker 3: holds a fake key labeled `../../etc/passwd`
> - Attacker 4: holds a smoke bomb labeled `${IFS}`

**Apariciones**: solo audio 1, escena de los ataques.

---

## Escenarios recurrentes

### Estudio de Nico
> Cluttered programmer's desk, top-down or 3/4 view. Laptop with Chrome open showing "Groq" chat. A plant in a small pot. Sticky notes on the wall (one says "TDD or DIE"). Window with simple clouds. Empty mate cups. Drawn flat, isometric-ish.

### El Túnel/Gateway
> Two boxes connected by a curvy pipe drawn in lila. Left box: Chrome browser with Groq logo. Right box: a black terminal window. Through the pipe flow tiny yellow JSON brackets `{}` like packets.

### Pizarra de ataques
> A whiteboard with 4 numbered sketches of the attackers. Title: "ATAQUES?". Hand-written list style. Nico and Bicho looking at it.

### Test runner
> A simple list of bullet points. Each bullet starts red (failing test) and flips to green (passing). Displayed inside a doodle laptop.

### Estudio de skills (audio 2)
> Nico hands a glowing PDF labeled "KARPATHY SKILLS" to El Bicho. Bicho opens it, skills fly out as little badge stickers and stick to its body like medals or USB sticks plugged in.

---

## Reglas de continuidad

1. **Mismo trazo en todas las escenas**. Si el line boil tiene ~3px, mantenerlo.
2. **Mismos colores**. Cuando aparezca el Bicho calmo, siempre cyan. Alarmado, rojo. Aprendiendo, amarillo.
3. **Misma textura de fondo**. Cream paper grain en todo.
4. **Misma cámara**. Mayoritariamente plano fijo o slow pan. No zooms agresivos, no rotaciones 3D.
5. **Tipografía**: cualquier texto en pantalla es hand-written, no fuente digital (excepto cuando se ve un terminal — ahí monoespaciada verde clásica).
6. **Densidad**: máximo 1 personaje + 1 elemento de contexto por plano. No saturar.

---

## Cuándo romper las reglas

- Para puntuar momentos de **revelación** (audio 2: cuando se revela que el bicho se enchufó los skills) puede haber un destello amarillo de pantalla completa por 2 frames.
- Para puntuar **peligro** (audio 1: cuando aparecen los ataques): un parpadeo rojo por 1 frame antes de cortar a la pizarra.

Eso es todo. Cualquier otro efecto = ruido.
