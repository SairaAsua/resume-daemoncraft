# Plan General — Videos animados sobre los audios de Nico

> Competencia Claude vs Gemini vs Kimi.
> Dos audios, dos videos. Estética simple, dibujos planos coherentes.

## Audios fuente

| Archivo | Duración | Tema |
|---|---|---|
| `voice_21-04-2026_14-43-33` | 61.7s | El bicho propone TDD para defenderse de inyecciones |
| `voice_21-04-2026_14-44-11` | 35.2s | El bicho leyó a Karpathy y se enchufó skills a sí mismo |

Los dos audios son una continuación: el video 2 explica el "antes" del video 1 (flashback). Por eso el plan los trata como **una pieza unificada** con la misma bible visual.

## Tesis estética

**"Dibujos planos hand-drawn con sensación stop motion digital."**

Una sola persona podría replicarlo con marcador y papel. Nada de gradientes complejos, sombreado realista, ni 3D. Se busca la coherencia por **economía de medios**, no por sofisticación.

### Tres reglas de oro
1. **Línea negra gruesa hand-drawn** sobre fondo crema. Trazo imperfecto, no vectorial limpio.
2. **Rellenos planos** en una paleta limitada de 7 colores. Sin gradientes, sin sombras realistas.
3. **Animación "on twos" + line boil**: 12fps, cada dibujo 2 frames, micro-variaciones de línea para sentir vida (técnica de boiling line clásica de animación 2D).

## Pipeline técnico

```
[Bible visual] → [Character sheets en nano-banana]
                     ↓
[Storyboard por escena] → [Keyframes en nano-banana usando refs]
                     ↓
[Veo image-to-video] → [Clips animados ~6-8s c/u]
                     ↓
[ffmpeg concat + audio sync] → [video final mp4]
```

**Por qué este orden:**
- Las character sheets aseguran que el bicho/Nico se vean igual en cada generación (pro tip de Veo: reutilizar mismas refs y mismas descripciones literales).
- nano-banana (Gemini 2.5 Flash Image) genera frames con la consistency de personajes.
- Veo anima preservando el estilo del input → animación "on twos" sale natural si lo pedimos en el prompt.

## Estructura de carpetas

```
audiosnico/
├── plan/           ← este plan, bible, storyboards
├── refs/           ← character sheets, paleta, ejemplos de estilo
├── frames/         ← keyframes generados (1 por escena)
├── videos/         ← clips de Veo por escena
└── final/          ← videos finales (audio1.mp4, audio2.mp4)
```

## Referencias estéticas (para guiar prompts)

- **Sketchplanations** (Jono Hey): doodles educativos planos, línea negra, fondos crema
- **Kurzgesagt simplificado**: paleta limitada, formas geométricas, conceptos abstractos
- **Don Hertzfeldt**: líneas mínimas, mucho hueco, animación on threes
- **Reza Hasni / "loose doodle"**: trazo imperfecto a propósito
- **Aardman digital cut-out** (Creature Comforts estilo plano): timing terroso

## Sources de la investigación

- [Stop motion FPS guide — HUE](https://huehd.com/stop-motion-animation-frame-rates-explained/)
- [Why FPS matters — Stop Motion Magazine](https://stopmotionmagazine.com/why-your-frame-rate-fps-matters-in-animation/)
- [Line boil tutorial — LinkedIn Learning](https://www.linkedin.com/learning/2d-animation-tips-and-tricks/boiling-a-line)
- [Line Boil — TV Tropes](https://tvtropes.org/pmwiki/pmwiki.php/Main/LineBoil)
- [Veo 3 prompting guide — Replicate](https://replicate.com/blog/using-and-prompting-veo-3)
- [Veo image-to-video — Replicate](https://replicate.com/blog/veo-3-image)
- [Multi-shot consistency Veo 3.1 — Skywork](https://skywork.ai/blog/multi-prompt-multi-shot-consistency-veo-3-1-best-practices/)
