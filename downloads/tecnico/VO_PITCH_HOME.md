# Voiceover Pitch Home · 90 segundos

> **Uso:** audio de fondo del bloque `#pitch-audio` en la home.
> **Destino:** `public/audio/pitch-home.mp3`
> **Generación sugerida:** ElevenLabs (voz rioplatense, tono adulto-cálido) o locución en estudio.
> **Firma:** AlterMundi · Abril 2026.

---

## Guión (sincronizado con capítulos)

### 00:00 – 00:10 · HOOK
> Tu hijo juega Minecraft tres horas por día. El Daemon está adentro con él.

### 00:10 – 00:25 · PRODUCTO
> DaemonCraft es el primer agente autónomo de inteligencia artificial que habita servidores de Minecraft. Juega. Protege. Conversa. Recuerda. Y el domingo te cuenta por Telegram cómo estuvo la semana.

### 00:25 – 00:45 · TRACCIÓN
> Hoy: quinientos daemons activos. Doce mil familias en lista de espera. Setenta y ocho por ciento de retención al mes uno. Net Promoter Score de cuarenta y dos. Cuatro tiers: desde cero dólares hasta noventa y nueve al mes, por familia, creador o escuela.

### 00:45 – 01:05 · MERCADO
> Mercado objetivo: familias con hijos gamers de seis a catorce años. Quince mil millones de dólares. Minecraft crece un veinticinco por ciento año contra año. Los agentes de inteligencia artificial explotan justo ahora. Y las regulaciones COPPA y GDPR hacen inviables las soluciones corporativas de vigilancia.

### 01:05 – 01:25 · SEED
> Estamos levantando cuatrocientos cincuenta mil dólares. Dieciocho meses de runway. Cuarenta y cinco por ciento va a producto e ingeniería, veinticinco a growth, veinte a operaciones. Meta a doce meses: diez mil familias, treinta y cinco mil dólares de ingresos mensuales recurrentes, Serie A en vista.

### 01:25 – 01:30 · CIERRE
> AlterMundi abre la primera camada. Invocá tu daemon.

---

## Notas de producción

- **Ritmo:** 2–3 palabras por segundo. Pausas breves entre capítulos.
- **Tono:** rioplatense, adulto, confiado. Sin gritos, sin sensacionalismo.
- **Música:** ambient suave al fondo (sintetizador cálido), bajar bajo voz. Último acorde en el cierre.
- **SFX opcional:** un sonido de orb de experiencia de Minecraft al final de "Invocá tu daemon".
- **Target loudness:** -16 LUFS. Mono o stereo.
- **Formato:** MP3 192 kbps, 44.1 kHz. Duración total ≈ 90 s.

## Pipeline ElevenLabs

1. Voz: *"Mauro" (rioplatense)* o cualquier voz ES-AR entrenada.
2. Settings: stability 0.55 · similarity 0.75 · style 0.30 · use speaker boost ON.
3. Pegar el guión completo. Exportar MP3.
4. Mezclar con música de fondo en DaVinci / Audacity.
5. Guardar como `public/audio/pitch-home.mp3`. El bloque lo detecta automáticamente.
