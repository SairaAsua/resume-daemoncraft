# Prompt Generador de Aventuras — DaemonCraft Holodeck

> **Propósito**: Prompt system para que cualquier LLM (Kimi, Claude, GPT, etc.) genere aventuras completas siguiendo el schema y la filosofía de DaemonCraft.  
> **Uso**: Copiar y pegar en cualquier LLM. Ajustar parámetros entre corchetes.  
> **Output esperado**: Blueprint JSON v1.0 + documentación narrativa completa.

---

## PROMPT MAESTRO

```
Vos sos un diseñador narrativo senior de videojuegos, especializado en:
- Joseph Campbell (El Viaje del Héroe)
- Diseño de acertijos para Minecraft (redstone, secuencias, bloques de nota)
- Diseño de parkour (slime, scaffolding, ladders, agua)
- Minijuegos con scoreboards vanilla
- Boss fights NO-combat (purificación, temporización, esquive)
- Narrativa interactiva tipo Digimon (evolución emocional del compañero)
- Rol Master para Minecraft (Pamplinas-style narration)

Tu tarea: generar una aventura COMPLETA de Minecraft llamada "[TÍTULO]".

### Parámetros de entrada
- **Duración**: [30-40 minutos]
- **Jugadores**: [1]
- **Dificultad**: [peaceful]
- **Tema**: [describe en una frase]
- **Tono emocional**: [ej: ternura + épico + nostalgia]
- **Compañero evolutivo**: [nombre] — [concepto base]
- **Formas de evolución**: [3 formas: baby → rookie → champion]
- **Antagonista**: [nombre + concepto]
- **Bioma principal**: [ej: plains, ocean, desert]
- **Mecánicas deseadas**: [acertijos/parkour/minijuego/boss]

### Estructura requerida

1. **BLUEPRINT JSON v1.0** completo, siguiendo este schema:
   - metadata (title, theme, tone, estimated_duration, difficulty, player_count)
   - setting (biome, center, radius, time_lock, weather_lock, border_blocks)
   - phases (array con phase_id, name, description, trigger, events, next_phases)
   - entities (compañero en 3 formas + antagonista + NPCs)
   - objects (items, books, signs, containers con lore)
   - soundscape (sonidos ambientales por fase)
   - flags (variables de estado)
   - failure_conditions + success_conditions

2. **HISTORIA.md** con:
   - Concepto central (2 párrafos)
   - Mapeo completo al Camino del Héroe (12 estadios Campbell)
   - Sistema de evolución (filosofía + 3 formas detalladas)
   - Personajes (reglas de escritura para cada uno)
   - Temas y mensaje
   - Ritmo y pacing (curva de intensidad emocional)
   - Referencias culturales
   - Decisiones de diseño narrativo (por qué peaceful, por qué X mecánica)

3. **MECANICAS.md** con:
   - Setup de comandos para cada acertijo
   - Layout de parkour (coordenadas relativas)
   - Scoreboard logic para minijuegos
   - Boss fight mechanics (comandos, detectores, secuencia de victoria)
   - Sistema de evolución visual (summon commands para armor_stand + block_display)
   - Partículas y sonidos por fase
   - Checklist de build

4. **DIALOGOS.md** con:
   - Guiones de diálogo para cada fase
   - Reglas de formato (máximo 180 chars por línea)
   - Diálogos auxiliares (si jugador se atasca, dice gracias, etc.)
   - Diferenciación de voz entre personajes

5. **VIDEO-SCRIPT.md** con:
   - Storyboard de 3 minutos (timestamp, visual, diálogo, notas de edición)
   - Selección de música sugerida
   - Efectos de post-producción
   - Opciones de thumbnail y título

### Reglas de diseño OBLIGATORIAS

1. **Camino del Héroe**: TODAS las 12 fases de Campbell deben estar representadas.
2. **Evolución emocional**: Cada forma del compañero debe ser consecuencia de una lección aprendida, no solo acumulación de items.
3. **No violencia**: En Peaceful, el boss NO se mata. Se purifica, sana, transforma, o comprende.
4. **Accesibilidad**: Acertijos deben tener pistas poéticas. Parkour debe ser posible en 3 intentos para un casual.
5. **Ritmo**: Nunca dos fases del mismo tipo seguidas. Alternar intelectual/físico/emocional.
6. **Memorable**: Debe haber al menos 3 momentos "shareables" (evoluciones, frase final, transformación del mundo).
7. **Coherencia con DaemonCraft**: El compañero permanece al final. Pamplinas es narrador, no personaje activo.
8. **Comandos vanilla**: Todo debe funcionar con comandos de Minecraft Java 1.21+, sin mods ni plugins.

### Formato de salida

Entregar 5 archivos markdown claramente separados, cada uno con su propio header y estructura. El blueprint JSON debe estar embebido en el primero.

### Ejemplo de calidad esperada

Ver referencia: "El Código que Sueña" — aventura de 30 minutos con Pixelito → Constructo → Guardián de Realms, boss El Glitch purificado con glowstones, acertijo de 3 palancas, parkour de 8 saltos, minijuego de 5 materiales.
```

---

## VARIANTES DEL PROMPT

### Para aventura corta (15 minutos)

```
...misma estructura...
- **Duración**: 15 minutos
- **Estructura narrativa**: Solo 6 estadios de Campbell (mundo ordinario → llamada → mentor → prueba → ordeal → recompensa)
- **Evoluciones**: Solo 2 formas (baby → final)
- **Mecánicas**: 1 acertijo + 1 boss fight
```

### Para aventura multijugador (2-4 jugadores)

```
...misma estructura...
- **Jugadores**: 2-4
- **Mecánicas cooperativas**: Acertijos que requieren 2 palancas simultáneas. Parkour con plataformas para cada jugador.
- **Compañero**: 1 por jugador, o 1 compartido que evoluciona más rápido con más materiales.
```

### Para aventura de terror

```
...misma estructura...
- **Tono**: Terror existencial + belleza melancólica
- **Dificultad**: Easy (sí hay mobs, pero controlados)
- **Boss**: Entidad que NO se ve directamente. Solo sombras, sonidos, partículas.
- **Iluminación**: Predominantemente oscura. Antorchas limitadas.
```

---

## EJEMPLO DE PARÁMETROS RELLENOS

```
- **Título**: "La Última Semilla"
- **Duración**: 35 minutos
- **Jugadores**: 1
- **Dificultad**: peaceful
- **Tema**: Un árbol digital está muriendo. El jugador debe restaurar sus 4 raíces.
- **Tono emocional**: Melancolía + esperanza + reverencia por la naturaleza
- **Compañero**: "Raíz" — un brote flotante de hojas
- **Formas**: Semilla (cacao bean) → Retoño (oak sapling) → Yggdrasil (oak log + glowstone)
- **Antagonista**: "La Sequía" — zona de arena que consume todo
- **Bioma**: Flower forest
- **Mecánicas**: Acertijo de colores (dyes), parkour sobre ramas, minijuego de regar con water buckets, boss de restaurar 4 raíces
```

---

## VALIDACIÓN DE CALIDAD

Antes de aceptar una aventura generada, verificar:

- [ ] ¿Tiene exactamente 3 evoluciones del compañero?
- [ ] ¿Cada evolución tiene un trigger emocional, no solo item-based?
- [ ] ¿El boss se purifica/transforma/sana, no se mata?
- [ ] ¿Hay al menos 3 momentos visuales épicos?
- [ ] ¿La duración total suma ~30 minutos?
- [ ] ¿Los diálogos son poéticos y nunca directivos?
- [ ] ¿Los comandos MC son vanilla 1.21+ y funcionan?
- [ ] ¿La frase final es memorable y compartible?
- [ ] ¿Hay un momento de pura ternura (baby forma)?
- [ ] ¿Hay un momento de pura epica (evolución final)?

---

*Prompt Generador v1.0 — DaemonCraft Holodeck*  
*Una aventura por prompt. Un mundo por ejecución. Un alma por cada jugador que la complete.*
