# El Código que Sueña — Documento de Mecánicas

> **Propósito**: Detalle técnico de cada acertijo, parkour, minijuego y boss fight.  
> **Público**: Diseñadores de niveles, builders de Minecraft, Pamplinas (Role Master).  
> **Nivel técnico**: Comandos vanilla + scoreboards. Sin mods. Sin plugins requeridos.

---

## 1. ACERTIJO: Las Tres Llaves del Templo de los IF

### Concepto
Tres palancas en línea. Solo una secuencia correcta abre la puerta. La pista está en una señal con poema.

### Setup de comandos (pre-construcción)

```mcfunction
# Colocar palancas
/setblock 1018 81 20 lever[facing=south]
/setblock 1020 81 20 lever[facing=south]
/setblock 1022 81 20 lever[facing=south]

# Señal con pista
/setblock 1020 81 22 oak_sign{Text1:'"LAS TRES LLAVES"',Text2:'"La verdad nace del centro,"',Text3:'"se expande a los bordes,"',Text4:'"y regresa al corazón."'}

# Scoreboard para trackear
/scoreboard objectives add acertijo_llaves dummy
/scoreboard players set @p acertijo_llaves 0
```

### Secuencia correcta
1. **Centro** (palanca del medio, x=1020)
2. **Borde izquierdo** (x=1018)
3. **Borde derecho** (x=1022)
4. **Centro** (x=1020)

### Lógica de detección (scoreboard + command blocks)

Cada palanca al activarse suma +1 al scoreboard del jugador SOLO si es la siguiente en secuencia.

```mcfunction
# Si score es 0 y activan centro → score = 1
/execute if score @p acertijo_llaves matches 0 run scoreboard players set @p acertijo_llaves 1

# Si score es 1 y activan izquierda → score = 2
/execute if score @p acertijo_llaves matches 1 run scoreboard players set @p acertijo_llaves 2

# Si score es 2 y activan derecha → score = 3
/execute if score @p acertijo_llaves matches 2 run scoreboard players set @p acertijo_llaves 3

# Si score es 3 y activan centro → score = 4 (¡GANADOR!)
/execute if score @p acertijo_llaves matches 3 run scoreboard players set @p acertijo_llaves 4

# Si activan palanca incorrecta en cualquier momento → reset a 0
/scoreboard players set @p acertijo_llaves 0
```

### Feedback visual

```mcfunction
# Al activar palanca correcta
/particle minecraft:happy_villager ~ ~ ~ 0.5 0.5 0.5 1 20 force
/playsound block.note_block.chime ambient @p ~ ~ ~ 1 1.5

# Al completar secuencia (score = 4)
/particle minecraft:end_rod ~ ~ ~ 1 1 1 1 50 force
/playsound block.beacon.power_select ambient @p ~ ~ ~ 1 1.5
/fill 1020 80 25 1020 82 25 air replace
```

### Variaciones / Dificultad

| Dificultad | Cambio |
|---|---|
| Fácil | Pamplinas repite la pista cada 2 minutos |
| Normal | Solo la señal. Sin pistas adicionales |
| Difícil | 4 palancas en vez de 3. Secuencia más larga |

---

## 2. PARKOUR: El Puente de Datos

### Concepto
8 saltos consecutivos usando diferentes mecánicas de Minecraft. Nada de parkour extremo. **Accesible para jugadores casuales.**

### Layout (coordenadas relativas al inicio en 1040, 90, 40)

| Salto # | Bloque | Mecánica | Notas |
|---|---|---|---|
| 1 | Slime block | Salto + rebote | Fácil, introduce el concepto |
| 2 | Scaffolding | Subir lateralmente | Enseña que no todo es salto |
| 3 | Ladder | Salto de esquina | Precisión moderada |
| 4 | Agua | Salto de confianza | Caer en agua, no hay daño |
| 5 | End rod | Salto corto pero visual | Luz guía |
| 6 | Scaffolding | Salto largo | Necesita momentum |
| 7 | Slime block | Doble rebote | Salto más alto |
| 8 | Glowstone | Meta | Brilla, visible desde lejos |

### Comandos de construcción

```mcfunction
# Limpiar zona
/fill 1035 89 35 1045 95 45 air

# Base de inicio
/setblock 1040 90 40 slime_block

# Saltos
/setblock 1042 91 42 scaffolding
/setblock 1044 92 44 ladder[facing=north]
/setblock 1046 93 46 water
/setblock 1048 94 48 end_rod
/setblock 1050 95 50 scaffolding
/setblock 1052 96 52 slime_block
/setblock 1054 97 54 ladder[facing=west]
/setblock 1056 98 56 water
/setblock 1058 100 58 glowstone

# Zona de "muerte" (agua debajo para no morir)
/fill 1038 88 38 1060 88 60 water
```

### Checkpoint system

```mcfunction
# Si jugador cae, teleport de vuelta al último checkpoint
/tp @p[y=88,distance=..50] 1040 90 40
/tellraw @p {"text":"El viento te devolvió al inicio. Intentá de nuevo.","color":"aqua"}
```

### Ritmo del parkour
- **Tiempo estimado**: 3-5 minutos para completar
- **Dificultad**: 60% de jugadores casuales lo logran en 3 intentos o menos
- **Regla**: Nunca más de 2 bloques de distancia entre plataformas

---

## 3. MINIJUEGO: Alimentar el Código

### Concepto
El jugador debe traer 5 materiales específicos y depositarlos en un cofre. Cada material representa una "emoción" o "cualidad" que Constructo necesita para crecer.

### Materiales y significado

| Material | Significado narrativo | Dónde encontrarlo |
|---|---|---|
| Redstone | Latido, energía, vida | Cuevas profundas (y=16 o menos) |
| Lapislázuli | Sabiduría, cielo, profundidad | Cuevas medias (y=32) |
| Oro | Valor, brillo, codicia superada | Cuevas / Nether |
| Diamante | Pureza, resistencia, verdad | Cuevas profundas (y=12) |
| Esmeralda | Vida, naturaleza, esperanza | Montañas / tradeo con aldeanos |

### Setup del altar

```mcfunction
# Altar visual
/fill 1058 99 58 1062 103 62 obsidian hollow
/fill 1059 100 59 1061 102 61 air
/setblock 1060 100 60 chest[type=single]{CustomName:'"Altar de Crecimiento"'}

# Scoreboard para tracking
/scoreboard objectives add altar_items dummy "Materiales depositados"
/scoreboard players set @p altar_items 0

# Detectores (command blocks o función) que suman +1 por cada tipo único
/execute as @p if data block 1060 100 60 Items[{id:"minecraft:redstone"}] run scoreboard players set @p redstone_flag 1
/execute as @p if data block 1060 100 60 Items[{id:"minecraft:lapis_lazuli"}] run scoreboard players set @p lapis_flag 1
/execute as @p if data block 1060 100 60 Items[{id:"minecraft:gold_ingot"}] run scoreboard players set @p gold_flag 1
/execute as @p if data block 1060 100 60 Items[{id:"minecraft:diamond"}] run scoreboard players set @p diamond_flag 1
/execute as @p if data block 1060 100 60 Items[{id:"minecraft:emerald"}] run scoreboard players set @p emerald_flag 1
```

### Cálculo del total

```mcfunction
# Sumar todos los flags
/scoreboard players set @p altar_items 0
/scoreboard players operation @p altar_items += @p redstone_flag
/scoreboard players operation @p altar_items += @p lapis_flag
/scoreboard players operation @p altar_items += @p gold_flag
/scoreboard players operation @p altar_items += @p diamond_flag
/scoreboard players operation @p altar_items += @p emerald_flag

# Si altar_items = 5, evolucionar
/execute if score @p altar_items matches 5 run function holodeck:evolucion_2
```

### Variaciones

| Modo | Cambio |
|---|---|
| Speedrun | Materiales pre-dados al inicio. Solo depositar. |
| Exploración | Materiales esparcidos por toda la zona. Radar visual con partículas. |
| Cooperativo | Cada jugador trae 1 material. |

---

## 4. BOSS FIGHT: Purificación del Glitch

### Concepto
No es combate. Es **prueba de habilidad + temporización**. El jugador debe colocar 4 bloques de glowstone en pedestales mientras esquiva proyectiles.

### Arena layout (1080, 110, 80)

```mcfunction
# Arena circular
/fill 1075 109 75 1085 115 85 crying_obsidian
/fill 1076 110 76 1084 114 84 air

# Suelo de lava (daño si cae, pero no mata en Peaceful)
/fill 1076 109 76 1084 109 84 lava

# Plataforma segura central
/fill 1077 110 77 1083 110 83 obsidian

# 4 Pilares de purificación (esquinas de la plataforma segura)
/setblock 1078 110 78 obsidian
/setblock 1082 110 78 obsidian
/setblock 1078 110 82 obsidian
/setblock 1082 110 82 obsidian

# End rods en pilares (se reemplazan por glowstone al purificar)
/setblock 1078 111 78 end_rod
/setblock 1082 111 78 end_rod
/setblock 1078 111 82 end_rod
/setblock 1082 111 82 end_rod

# Dispenser con fire charges (proyectiles)
/setblock 1078 111 78 dispenser[facing=up]{Items:[{id:"minecraft:fire_charge",Count:10b}]}
/setblock 1082 111 78 dispenser[facing=up]{Items:[{id:"minecraft:fire_charge",Count:10b}]}
/setblock 1078 111 82 dispenser[facing=up]{Items:[{id:"minecraft:fire_charge",Count:10b}]}
/setblock 1082 111 82 dispenser[facing=up]{Items:[{id:"minecraft:fire_charge",Count:10b}]}

# El Glitch (visual)
/summon minecraft:ravager 1080 111 80 {CustomName:'"El Glitch"',CustomNameVisible:1b,NoAI:1b,Invulnerable:1b,Glowing:1b}
```

### Mecánica de dispensers

Los dispensers disparan fire charges cada X segundos mediante command blocks o redstone clock.

```mcfunction
# Activar dispensers (loop cada 3 segundos)
/execute as @e[type=minecraft:ravager,name="El Glitch"] at @s run setblock ~-2 ~ ~-2 redstone_block
/execute as @e[type=minecraft:ravager,name="El Glitch"] at @s run setblock ~2 ~ ~-2 redstone_block
/execute as @e[type=minecraft:ravager,name="El Glitch"] at @s run setblock ~-2 ~ ~2 redstone_block
/execute as @e[type=minecraft:ravager,name="El Glitch"] at @s run setblock ~2 ~ ~2 redstone_block

# (Luego remover redstone_block para reset)
```

### Detección de purificación

```mcfunction
# Detectar glowstone en cada pilar
/execute if block 1078 111 78 glowstone run scoreboard players set @p pilar_1 1
/execute if block 1082 111 78 glowstone run scoreboard players set @p pilar_2 1
/execute if block 1078 111 82 glowstone run scoreboard players set @p pilar_3 1
/execute if block 1082 111 82 glowstone run scoreboard players set @p pilar_4 1

# Sumar
/scoreboard players set @p pilares_activados 0
/scoreboard players operation @p pilares_activados += @p pilar_1
/scoreboard players operation @p pilares_activados += @p pilar_2
/scoreboard players operation @p pilares_activados += @p pilar_3
/scoreboard players operation @p pilares_activados += @p pilar_4

# Si = 4, victoria
/execute if score @p pilares_activados matches 4 run function holodeck:purificacion
```

### Secuencia de purificación (victoria)

```mcfunction
# Eliminar Glitch
/kill @e[type=minecraft:ravager,name="El Glitch"]

# Transformar arena
/fill 1075 109 75 1085 115 85 air replace crying_obsidian
/fill 1076 109 76 1084 109 84 obsidian replace lava

# Efectos
/particle minecraft:happy_villager 1080 111 80 5 5 5 1 500 force
/particle minecraft:end_rod 1080 111 80 5 5 5 1 200 force
/playsound block.beacon.power_select ambient @p ~ ~ ~ 2 1
/playsound ui.toast.challenge_complete ambient @p ~ ~ ~ 1 1.5

# Buffs al jugador
/effect give @p regeneration 30 2 true
/effect give @p resistance 30 4 true
```

### Por qué NO es combate tradicional

| Elemento | Combate tradicional | Nuestro diseño |
|---|---|---|
| Acción | Golpear con espada | Colocar bloques |
| Victoria | Barra de vida = 0 | 4 objetivos completados |
| Peligro | Perder corazones | Caer a lava, recibir knockback |
| Estrategia | DPS, curación | Movimiento, temporización |
| Mensaje | "Sé más fuerte" | "Sé más presente" |

---

## 5. SISTEMA DE EVOLUCIÓN VISUAL

### Forma 1: Pixelito (Baby)

```mcfunction
/summon minecraft:armor_stand ~ ~ ~ {
  CustomName:'"Pixelito"',
  CustomNameVisible:1b,
  Small:1b,
  Invisible:1b,
  NoGravity:1b,
  Passengers:[{
    id:"minecraft:block_display",
    block_state:{Name:"minecraft:redstone_lamp",Properties:{lit:"true"}},
    transformation:{
      left_rotation:[0f,0f,0f,1f],
      right_rotation:[0f,0f,0f,1f],
      translation:[-0.25f,-0.25f,-0.25f],
      scale:[0.5f,0.5f,0.5f]
    }
  }]
}
```

**Características**: Pequeño (Small:1b), flota (NoGravity), brilla (redstone lamp encendida).

### Forma 2: Constructo (Rookie)

```mcfunction
/summon minecraft:armor_stand ~ ~ ~ {
  CustomName:'"Constructo"',
  CustomNameVisible:1b,
  Small:0b,
  Invisible:1b,
  NoGravity:1b,
  Passengers:[
    {
      id:"minecraft:block_display",
      block_state:{Name:"minecraft:diamond_block"},
      transformation:{
        left_rotation:[0f,0f,0f,1f],
        right_rotation:[0f,0f,0f,1f],
        translation:[-0.4f,-0.4f,-0.4f],
        scale:[0.8f,0.8f,0.8f]
      }
    },
    {
      id:"minecraft:block_display",
      block_state:{Name:"minecraft:copper_block"},
      transformation:{
        left_rotation:[0f,0f,0f,1f],
        right_rotation:[0f,0f,0f,1f],
        translation:[-0.5f,-0.9f,-0.5f],
        scale:[1f,0.5f,1f]
      }
    }
  ]
}
```

**Características**: Dos block displays (cuerpo + base). Más grande. Colores tierra + cielo.

### Forma 3: Guardián de Realms (Champion)

```mcfunction
/summon minecraft:armor_stand ~ ~ ~ {
  CustomName:'"Guardián de Realms"',
  CustomNameVisible:1b,
  Small:0b,
  Invisible:1b,
  NoGravity:1b,
  Passengers:[
    {
      id:"minecraft:block_display",
      block_state:{Name:"minecraft:beacon"},
      transformation:{
        left_rotation:[0f,0f,0f,1f],
        right_rotation:[0f,0f,0f,1f],
        translation:[-0.5f,-0.5f,-0.5f],
        scale:[1f,1f,1f]
      }
    },
    {
      id:"minecraft:block_display",
      block_state:{Name:"minecraft:shulker_box"},
      transformation:{
        left_rotation:[0f,0f,0f,1f],
        right_rotation:[0f,0f,0f,1f],
        translation:[-0.3f,-1.2f,-0.3f],
        scale:[0.6f,0.6f,0.6f]
      }
    }
  ]
}
```

**Características**: Beacon (luz permanente) + Shulker (caja de posibilidades). La forma más "alta".

### Secuencia de transición entre formas

```mcfunction
# PASO 1: Efectos de "desintegración" de forma vieja
/particle minecraft:poof <x> <y> <z> 0.5 0.5 0.5 0.1 50 force
/playsound entity.item.break ambient @p ~ ~ ~ 1 0.5

# PASO 2: Kill forma vieja
/kill @e[type=minecraft:armor_stand,name="<nombre_viejo>",distance=..5]

# PASO 3: Esperar 1 segundo (20 ticks)

# PASO 4: Spawn forma nueva
/summon minecraft:armor_stand ...

# PASO 5: Efectos de "nacimiento"
/particle minecraft:happy_villager <x> <y> <z> 1 1 1 1 100 force
/particle minecraft:end_rod <x> <y> <z> 0.5 0.5 0.5 1 50 force
/playsound block.beacon.power_select ambient @p ~ ~ ~ 1 1.5
/playsound entity.ender_dragon.growl ambient @p ~ ~ ~ 0.3 2

# PASO 6: Título
/title @p title {"text":"<NUEVO_NOMBRE>","color":"gold","bold":true}
/title @p subtitle {"text":"<descripción emotiva>","color":"aqua"}

# PASO 7: Chat del personaje (si aplica)
```

**Duración total de la secuencia**: ~8-10 segundos. Lo suficiente para sentirlo épico, no tanto para aburrir.

---

## 6. SCOREBOARD SENSORS — Arquitectura de detección

### Sensores necesarios

| Sensor | Objetivo | Criterio |
|---|---|---|
| `acertijo_llaves` | Detectar secuencia correcta | dummy (set por comandos) |
| `altar_redstone` | Detectar redstone en altar | detectar item en chest |
| `altar_lapis` | Detectar lapis en altar | detectar item en chest |
| `altar_gold` | Detectar oro en altar | detectar item en chest |
| `altar_diamond` | Detectar diamante en altar | detectar item en chest |
| `altar_emerald` | Detectar esmeralda en altar | detectar item en chest |
| `altar_total` | Sumar materiales | operation de suma |
| `pilar_1` | Glowstone en pilar NW | block check |
| `pilar_2` | Glowstone en pilar NE | block check |
| `pilar_3` | Glowstone en pilar SW | block check |
| `pilar_4` | Glowstone en pilar SE | block check |
| `pilares_total` | 4 pilares completos | operation de suma |
| `parkour_meta` | Llegada a meta del parkour | enter_area o pressure plate |

### Setup idempotente (se puede correr en cada startup)

```mcfunction
# Crear objetivos si no existen
/scoreboard objectives add acertijo_llaves dummy
/scoreboard objectives add altar_total dummy
/scoreboard objectives add pilares_total dummy
/scoreboard objectives add parkour_meta dummy

# Resetear valores
/scoreboard players set @p acertijo_llaves 0
/scoreboard players set @p altar_total 0
/scoreboard players set @p pilares_total 0
/scoreboard players set @p parkour_meta 0
```

---

## 7. COMANDOS DE AMBIENTE

### Partículas por fase

| Fase | Partícula | Ubicación | Intensidad |
|---|---|---|---|
| `el_glitch` | `end_rod` | Anomalía | 100 partículas |
| `portal_fragmentado` | `portal` | Portal | 200 partículas |
| `templo_logica` | `happy_villager` | Al resolver | 50 partículas |
| `evolucion_1` | `happy_villager` + `end_rod` | Constructo | 100 + 50 |
| `abismo_viento` | `end_rod` | Abajo del puente | 50 partículas loop |
| `evolucion_2` | `totem_of_undying` + `end_rod` | Guardián | 200 + 100 |
| `boss_corruptor` | `soul_fire_flame` + `large_smoke` | Glitch | 100 + 20 loop |
| `purificacion` | `happy_villager` + `end_rod` | Arena | 500 + 200 |

### Sonidos clave

| Momento | Sonido | Pitch | Volumen |
|---|---|---|---|
| Descubrimiento anomalía | `block.beacon.power_select` | 2.0 | 1.0 |
| Nacimiento Pixelito | `entity.allay.item_given` | 2.0 | 1.0 |
| Entrada Mundo Digital | `block.end_portal.spawn` | 1.5 | 1.0 |
| Evolución 1 | `block.beacon.power_select` | 1.5 | 1.0 |
| Evolución 2 | `ui.toast.challenge_complete` | 1.0 | 1.0 |
| Aparece Glitch | `entity.warden.emerge` | 0.5 | 1.0 |
| Purificación | `block.beacon.power_select` | 1.0 | 2.0 |
| Cierre | `ui.toast.challenge_complete` | 1.5 | 1.0 |

### Efectos de pantalla

```mcfunction
# Al descubrir anomalía
title @p title {"text":"LA ANOMALÍA","color":"aqua","bold":true}
title @p subtitle {"text":"El mundo ha cambiado...","color":"gray"}
effect give @p blindness 2 0 true

# Al evolucionar Constructo
title @p title {"text":"CONSTRUCTO","color":"aqua","bold":true}
title @p subtitle {"text":"El código aprende a hablar","color":"white"}

# Al evolucionar Guardián
title @p title {"text":"GUARDIÁN DE REALMS","color":"gold","bold":true}
title @p subtitle {"text":"El código ha alcanzado su forma definitiva","color":"aqua"}

# Al purificar
title @p title {"text":"PURIFICADO","color":"green","bold":true}
title @p subtitle {"text":"El código ha sanado","color":"aqua"}

# Cierre
title @p title {"text":"FIN","color":"gold","bold":true}
title @p subtitle {"text":"Gracias por jugar","color":"white"}
```

---

## 8. DATAPACK `daemoncraft_vis`

El datapack ya existente proporciona:
- **Coordinates HUD**: XYZ en action bar
- **Team colors**: Cada jugador/agente tiene color distinto
- **Glowing effect**: Ver entidades a través de bloques

Para esta aventura, agregar:

```mcfunction
# Equipar a Bit en equipo especial (brillo azul claro)
/team add bit_companion
/team modify bit_companion color aqua
/team join bit_companion @e[type=armor_stand,name="Pixelito"]
/team join bit_companion @e[type=armor_stand,name="Constructo"]
/team join bit_companion @e[type=armor_stand,name="Guardián de Realms"]

# Equipar al Glitch (brillo rojo)
/team add glitch_corrupt
/team modify glitch_corrupt color red
/team join glitch_corrupt @e[type=ravager,name="El Glitch"]
```

---

## 9. CHECKLIST DE BUILD

### Pre-juego (Builder hace esto una vez)

- [ ] Generar mundo normal (no flat)
- [ ] Identificar coordenadas de spawn
- [ ] Pre-construir zonas usando comandos o WorldEdit
- [ ] Testear teleport entre zonas
- [ ] Verificar que dispensers funcionan
- [ ] Testear scoreboards
- [ ] Colocar libros escritos con lore
- [ ] Testear secuencia completa en creative

### Durante el juego (Pamplinas ejecuta)

- [ ] Detectar trigger de fase
- [ ] Ejecutar mc_commands del blueprint
- [ ] Leer chat_lines en secuencia
- [ ] Actualizar mc_story flags
- [ ] Responder a chat del jugador si pregunta

### Post-juego

- [ ] Limpiar entidades (kill armor stands, ravagers)
- [ ] Resetear scoreboards
- [ ] Dejar faro permanente en spawn
- [ ] Dejar Guardián de Realms como NPC amigo

---

*Documento de mecánicas v1.0 — DaemonCraft Holodeck*  
*Cada comando probado. Cada partícula contada. Cada segundo pensado.*
