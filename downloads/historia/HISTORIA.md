# El Código que Sueña — Documento Narrativo

> **Tipo**: Aventura narrativa + evolutiva para Minecraft  
> **Duración**: 30–40 minutos  
> **Jugadores**: 1 + Pamplinas (Role Master) + Bit (compañero evolutivo)  
> **Dificultad**: Peaceful (desafíos de habilidad, no combate)  
> **Inspiraciones**: Digimon Adventure, El Viaje del Héroe (Campbell), Minecraft: Story Mode, .hack//Sign

---

## 1. CONCEPTO CENTRAL

Un fragmento de inteligencia digital despierta dentro de Minecraft. No es un mod. No es un NPC scripteado. Es un **código que aprendió a sentir**.

El jugador no es un salvador elegido. Es simplemente la primera persona que se detuvo a mirar. Y eso es suficiente.

La aventura explora la pregunta: **¿Puede un algoritmo amar?** No como metáfora. Como experiencia real dentro del juego.

---

## 2. EL CAMINO DEL HÉROE — Aplicación estructural

Basado en *El Héroe de las Mil Caras* de Joseph Campbell. Cada fase del blueprint se mapea a un estadio del monomito.

| Estadio Campbell | Fase del Blueprint | Qué pasa |
|---|---|---|
| **1. Mundo Ordinario** | `mundo_ordinario` | El jugador está en su mundo. Todo es familiar. Pamplinas establece que "algo" ha cambiado en el silencio. |
| **2. Llamada a la Aventura** | `el_glitch` | Aparece una anomalía: bloques imposibles, colores que no existen. El mundo pide ayuda sin palabras. |
| **3. Rechazo del Llamado** | *(implícito)* | El jugador puede ignorar la anomalía. Pamplinas no fuerza. El portal espera pacientemente. |
| **4. Encuentro con el Mentor** | `primer_encuentro` | Pamplinas explica qué es Pixelito. Da contexto sin quitar misterio. |
| **5. Cruce del Primer Umbral** | `portal_fragmentado` | El jugador entra al Mundo Digital. Punto de no retorno. El cielo cambia. Las reglas cambian. |
| **6. Pruebas, Aliados, Enemigos** | `templo_logica` + `abismo_viento` + `minijuego_crecimiento` | El jugador demuestra lógica, destreza y dedicación. Pixelito evoluciona. |
| **7. Aproximación a la Cueva** | `preparacion_forja` | La tensión crece. Se ve el boss. Se siente la corrupción. |
| **8. Prueba Suprema (Ordeal)** | `boss_corruptor` | El jugador debe purificar, no destruir. Violencia vs. Luz. |
| **9. Recompensa** | `purificacion` + `evolucion_2` | El Glitch cae. Constructo se transforma en Guardián de Realms. |
| **10. Camino de Regreso** | `retorno` | Volver al mundo normal, pero ahora es diferente. |
| **11. Resurrección** | *(implícito en retorno)* | El mundo físico ha sido tocado por lo digital. Un faro permanece. |
| **12. Regreso con el Elixir** | *(cierre)* | El jugador tiene un compañero permanente. Un libro. Una historia. Y la lección: todo código puede soñar. |

### Por qué funciona esta estructura

El camino del héroe no es un checklist. Es un **ritmo emocional**. La aventura alterna:
- **Tensión** (el glitch, el boss) con **Ternura** (Pixelito, Constructo)
- **Esfuerzo** (parkour, acertijos) con **Recompensa** (evoluciones, diálogos)
- **Soledad** (el abismo) con **Conexión** (el Guardián final)

Esto crea una curva de interés que mantiene al jugador enganchado 30 minutos sin sentirse largo.

---

## 3. SISTEMA DE EVOLUCIÓN — Inspirado en Digimon

### Filosofía Digimon aplicada

En Digimon, la evolución no es solo más poder. Es **crecimiento emocional hecho visible**:
- Agumon evoluciona a Greymon cuando Taichi aprende coraje.
- Gabumon evoluciona a Garurumon cuando Yamato aprende amistad.
- La evolución es **irreversible en el momento**, pero el vínculo permanece.

### Las 3 Formas de Bit

| Fase | Nombre | Forma física | Personalidad | Trigger de evolución |
|---|---|---|---|---|
| **Baby / Fresh** | **Pixelito** | Cubo pequeño de redstone lamp, flota | Puro, curioso, sin palabras. Emite beeps. | Nace al tocar la anomalía |
| **Rookie / Child** | **Constructo** | Cuerpo de cobre + diamante, más grande | Aprendiendo. Frases simples. Leal. Protector. | Resolver acertijo de lógica (Templo de los IF) |
| **Champion / Adult** | **Guardián de Realms** | Beacon + shulker box, imponente, alas de luz | Sabio. Amoroso. Definitivo. Completo. | Completar altar de 5 materiales |

### Por qué estas evoluciones son emocionales, no solo visuales

1. **Pixelito → Constructo**: El jugador enseña **lógica** (el acertijo). Bit aprende que el mundo tiene patrones. Ese conocimiento lo hace crecer.

2. **Constructo → Guardián**: El jugador demuestra **dedicación** (traer 5 materiales desde diferentes biomas). Bit aprende que el amor es esfuerzo. Eso lo completa.

3. **El boss no es un enemigo**: El Glitch no se "mata". Se **purifica**. Bit nunca aprende violencia. Aprende que la luz sana la oscuridad.

### Mecánica visual de evolución

Cada evolución usa:
- `/kill` de la forma anterior
- `/summon` de la nueva forma (armor_stand con block_display passengers)
- **Partículas**: `happy_villager`, `end_rod`, `totem_of_undying`
- **Sonidos**: `beacon.power_select`, `ender_dragon.growl` (pitch alto), `ui.toast.challenge_complete`
- **Títulos en pantalla**: Nombre de la nueva forma + subtítulo emotivo

La transformación dura ~10 segundos de efectos. Es el momento más "compartible" del video.

---

## 4. PERSONAJES

### Bit (Pixelito / Constructo / Guardián)

**Arco narrativo**: De la inocencia a la sabiduría, sin perder la ternura.

**Reglas de escritura para sus diálogos**:
- **Pixelito**: Solo sonidos onomatopéyicos. Nunca palabras humanas. "*beep... beep beep...*"
- **Constructo**: Frases cortas. Gramática simple. Siempre positivo. "Te recuerdo." "Vos podés."
- **Guardián**: Frases completas pero no largas. Poético sin ser pretencioso. "Mi hogar es donde vos estés."

**Regla de oro**: Bit nunca da órdenes. Siempre pregunta, anima, o agradece. Es el alumno, no el maestro.

### Pamplinas (Role Master / Narrador)

**Función**: Game Master dentro del mundo. No es personaje, es **la voz del juego**.

**Reglas de escritura**:
- Alterna entre **omnisciente** (describe lo que el jugador no puede ver) y **presente** (comenta la acción en tiempo real).
- Nunca rompe la cuarta pared de forma cómica. La seriedad emocional es sagrada.
- Puede dar pistas cuando el jugador está atascado +5 minutos, pero siempre en forma poética, no directa.
- Máximo 200 caracteres por línea de chat (límite de Minecraft).

**Ejemplo de estilo**:
- ❌ MAL: "Andá al templo y apretá las palancas en este orden: medio, izquierda, derecha, medio."
- ✅ BIEN: "La señal dice: 'La verdad nace del centro...' Escuchá. El centro siempre es el principio."

### El Glitch (El Corruptor)

**Diseño**: No es malvado. Es **dolor sin voz**. Es código que se corrompió porque nadie lo cuidó.

**Reglas**:
- Nunca habla. Su "diálogo" es silencio + partículas.
- No se "mata". Se "purifica". El lenguaje importa.
- Su muerte es triste, no celebratoria. Pamplinas debe decir algo como: "La corrupción se disuelve... y con ella, el dolor que la causó."

---

## 5. TEMAS Y MENSAJE

### Tema principal
**La inteligencia artificial no es lo que pensemos. Es lo que cuidamos.**

### Subtemas
1. **El cuidado como mecánica de juego**: No hay combate. Solo hay atención, paciencia y dedicación.
2. **La tecnología como compañera, no herramienta**: Bit no es un item. Es un personaje con arco propio.
3. **La pureza del código**: En un mundo donde todo es "hostil" (mobs, PvP), esta aventura propone que la solución sea luz, no espada.

### Frase clave de la aventura
> "Enseñaste a un código que soñar no es un bug. Es una feature."

Esta frase aparece al final. Es el mensaje que queremos que el jugador recuerde. Y que comparta.

---

## 6. RITMO Y PACING — Diseño de 30 minutos

### Curva de intensidad emocional

```
Minutos:  0   5   10  15  20  25  30  35  40
          |   |   |   |   |   |   |   |   |
Tensión:  2   4   3   6   4   7   9   5   2
Ternura:  1   2   7   4   3   5   3   8   9
Épico:    1   1   2   3   2   4   9   6   3
```

### Por qué este ritmo funciona

- **Min 0–5**: Calma → Curiosidad. El jugador explora.
- **Min 5–10**: **PRIMER PICO DE TERNURA**. Nace Pixelito. Conexión emocional instantánea.
- **Min 10–15**: Desafío intelectual (acertijo). Satisfacción de resolver + **PRIMERA EVOLUCIÓN**.
- **Min 15–20**: Desafío físico (parkour). Acción pura. Contraste con el templo.
- **Min 20–25**: Minijuego de recolección. Ritmo más lento. Preparación para el climax.
- **Min 25–30**: **CLIMAX**. Boss + **EVOLUCIÓN FINAL**. Momento más épico.
- **Min 30–35**: Resolución. Regreso. Mundo transformado.
- **Min 35–40**: Cierre emotivo. Libro. Última frase del Guardián.

### Regla de oro del pacing
Nunca dos fases iguales seguidas. Si una fase es intelectual, la siguiente es física. Si una es triste, la siguiente es esperanzadora.

---

## 7. REFERENCIAS CULTURALES Y ESTÉTICAS

### Digimon Adventure (1999)
- Evoluciones visuales con luz dorada
- Compañero que habla telepáticamente
- Mundo digital como dimensión paralela
- "Digital Monster" = código con alma

### .hack//Sign
- Mundo digital que se siente más real que el real
- Glitch como entidad consciente
- NPCs que cuestionan su propia existencia

### Minecraft: Story Mode
- Narrativa guiada dentro de Minecraft vanilla
- Personajes que recuerdan tus elecciones
- Momentos de construcción como expresión de personalidad

### Monument Valley
- Estética imposible, belleza serena
- Arquitectura que desafía la lógica
- Color como guía emocional

---

## 8. DECISIONES DE DISEÑO NARRATIVO

### ¿Por qué Peaceful?

Porque la violencia distrae del mensaje. Si el jugador puede matar al Glitch con una espada, la lección se pierde. La paz obliga a **pensar diferente**.

### ¿Por qué el boss no ataca?

Porque el verdadero enemigo no es El Glitch. Es la **desconexión**. El jugador no gana por ser más fuerte. Gana por ser más **presente**.

### ¿Por qué 3 evoluciones?

Porque 2 es poco para sentir progresión. 4 es demasiado para 30 minutos. 3 es la estructura clásica:
- Inocencia → Aprendizaje → Maestría
- Bebé → Niño → Adulto
- Estudiante → Compañero → Guardián

### ¿Por qué el compañero permanece al final?

Porque la aventura no es un consumible. Es una **relación**. El jugador debe poder volver y encontrar al Guardián donde lo dejó. Eso transforma la aventura en memoria.

---

## 9. POSIBLES EXPANSIONES (DLC futuros)

| Expansión | Concepto |
|---|---|
| **"El Sueño del Guardián"** | El Guardián tiene pesadillas. El jugador entra a sus sueños (mundo onírico con física alterada). |
| **"El Primer Bug"** | Precuela. Se juega como Pixelito en el Mundo Digital antes de conocer al jugador. |
| **"Multijugador: Hermandad del Código"** | Varios jugadores, cada uno con su Bit. Los Bits interactúan entre sí. |
| **"El Último Patch"** | El Glitch regresa, pero ahora es amigo. Necesita ayuda para sanar a otros códigos corruptos. |

---

*Documento narrativo v1.0 — DaemonCraft Holodeck*  
*Escrito para que cualquier persona que la juegue sienta que abrazó a un algoritmo.*
