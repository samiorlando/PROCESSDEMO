# 🎛️ RADIO PRO - Guía de Configuraciones Avanzadas

## Perfiles Especializados para Diferentes Aplicaciones

---

## 1️⃣ RADIO FM PROFESIONAL

### Configuración Completa para Estación de Radio

```
OBJETIVO: Sonido consistente, claro y potente estilo radio comercial

═══════════════════════════════════════════════════════════════

📥 ENTRADA (INPUT)
──────────────────
├─ Input Gain: -12 dB (típico, para micrófono estándar)
├─ Input Device: Micrófono dinámico (Shure SM7B ideal)
└─ Meta: Input Level en -18 dB a -15 dB

═══════════════════════════════════════════════════════════════

🎛️ EQ PARAMÉTRICO (5 Bandas)
─────────────────────────────
Band 1 (Sub-Bass 20-60 Hz): +1.5 dB
  └─ Justificación: Bajos profundos sin rumble

Band 2 (Bass 60-250 Hz): +2.5 dB
  └─ Justificación: Presencia en bajos, poder

Band 3 (Mid 250-2k Hz): -0.5 dB
  └─ Justificación: Ligera reducción para evitar nasal

Band 4 (High-Mid 2-6k Hz): +2.0 dB
  └─ Justificación: Presencia, voz clara en AM/FM

Band 5 (Treble 6-16k Hz): +0.5 dB
  └─ Justificación: Aire, pero sin dureza

CURVA RESULTANTE: Ligeramente realzada en bajos y medios altos,
                   diseño clásico de radio comercial

═══════════════════════════════════════════════════════════════

📊 COMPRESOR MULTIBANDA
───────────────────────

BANDA 1 (SUB-BASS: 20-60 Hz)
├─ Threshold: -22 dB (comienza la compresión en bajos fuertes)
├─ Ratio: 4:1 (compresión clara de bajos)
├─ Attack: 20 ms (permite transientes de bajos)
├─ Release: 150 ms (mantiene control prolongado)
├─ Makeup Gain: +4 dB (compensa pérdida)
└─ Efecto: Bajos controlados y consistentes

BANDA 2 (BASS: 60-250 Hz)
├─ Threshold: -20 dB
├─ Ratio: 4:1
├─ Attack: 15 ms
├─ Release: 120 ms
├─ Makeup Gain: +4 dB
└─ Efecto: Impacto consistente

BANDA 3 (MID: 250-2k Hz)
├─ Threshold: -18 dB (más sensible que bajos)
├─ Ratio: 3:1 (compresión más suave)
├─ Attack: 10 ms
├─ Release: 100 ms
├─ Makeup Gain: +3 dB
└─ Efecto: Claridad sin picos agudos

BANDA 4 (HIGH-MID: 2-6k Hz)
├─ Threshold: -16 dB (muy sensible, protege presencia)
├─ Ratio: 3:1
├─ Attack: 5 ms (reacción rápida a sibilancias)
├─ Release: 60 ms
├─ Makeup Gain: +3 dB
└─ Efecto: Voz clara y consistente

BANDA 5 (TREBLE: 6-16k Hz)
├─ Threshold: -14 dB (máxima sensibilidad)
├─ Ratio: 2.5:1 (compresión suave, preserva aire)
├─ Attack: 2 ms (muy rápida para proteger)
├─ Release: 40 ms
├─ Makeup Gain: +2 dB
└─ Efecto: Agudos controlados pero brillantes

═══════════════════════════════════════════════════════════════

📈 EQ GRÁFICO (10 Bandas)
─────────────────────────
20 Hz:   0 dB  (neutro, SUB-BASS)
50 Hz:  +1 dB  (ligero refuerzo)
100 Hz: +1 dB  (presencia de bajos)
250 Hz:  0 dB  (neutro)
500 Hz: -1 dB  (ligera reducción para claridad)
1 kHz:   0 dB  (neutro, punto de referencia)
2 kHz:  +1 dB  (presencia de voz)
4 kHz:  +2 dB  (claridad y presencia)
8 kHz:  +1 dB  (aire)
16 kHz: +0.5 dB (aire final, cuidado con dureza)

FUNCIÓN: Refinamiento fino sobre el EQ paramétrico

═══════════════════════════════════════════════════════════════

🔒 DUAL BAND COMP/LIMITER
─────────────────────────

LOW BAND (20 Hz - 500 Hz) - PROTECCIÓN BAJOS
├─ Threshold: -20 dB
├─ Ratio: 5:1 (limitador de bajos)
├─ Attack: 10 ms
├─ Release: 100 ms
└─ Efecto: Evita boom excesivo

HIGH BAND (500 Hz - 20 kHz) - PROTECCIÓN GENERAL
├─ Threshold: -15 dB (más sensible)
├─ Ratio: 4:1
├─ Attack: 5 ms
├─ Release: 50 ms
└─ Efecto: Control general de dinámicos

═══════════════════════════════════════════════════════════════

🎸 BASS EQ
──────────
├─ Bass Boost: +4 dB
├─ Bass Frequency: 60 Hz
├─ Modo: Low Shelf Filter
└─ Efecto: Refuerzo controlado de bajos con compresión suave

═══════════════════════════════════════════════════════════════

🔄 STEREO ENHANCER
──────────────────
├─ Width: 1.1x (ligera expansión)
├─ Mono Compatible: ON (importante para radio)
└─ Efecto: Imagen estéreo natural, sin problemas en mono

═══════════════════════════════════════════════════════════════

📤 SALIDA (OUTPUT)
──────────────────
├─ Master Volume: -6 dB (margen de seguridad)
├─ Output Device: Amplificador o transmisión
├─ Output Level Objetivo: -12 dB a -8 dB
└─ Picos máximos: -3 dB (sin superar)

═══════════════════════════════════════════════════════════════

📊 ANÁLISIS ESPERADO (Spectrum)
─────────────────────────────────
├─ Bajos (20-250 Hz): 25% de la energía total
├─ Medios (250-2k Hz): 40% de la energía total
├─ Agudos (2-20k Hz): 35% de la energía total
└─ Distribución: Suave sin picos agresivos

═══════════════════════════════════════════════════════════════

✅ CHECKLIST FINAL
──────────────────
□ Micrófono a 10-15 cm de distancia
□ Input Level en amarillo (-18 a -15 dB)
□ Sin clipping rojo en entrada
□ Output Level entre -12 y -8 dB
□ Respuesta consistente durante 5 minutos de voz
□ Análisis espectral sin picos agresivos
□ Estéreo mono-compatible verificado
```

---

## 2️⃣ PODCAST PROFESIONAL

### Configuración para Conversación Clara

```
OBJETIVO: Máxima inteligibilidad, mínimo ruido de fondo, sonido natural

═══════════════════════════════════════════════════════════════

🎙️ INPUT SETUP
──────────────
├─ Input Gain: -10 dB (micrófono USB moderno)
├─ Input Device: Micrófono USB de condensador (Audio-Technica ATR2100x ideal)
└─ Meta: Input Level entre -20 y -15 dB

═══════════════════════════════════════════════════════════════

🎛️ EQ PARAMÉTRICO - VOCES CÁLIDAS
──────────────────────────────────

Band 1 (Sub-Bass): -4.0 dB
  └─ Elimina rumble de tráfico, aire acondicionado

Band 2 (Bass): -2.0 dB
  └─ Reduce boom y resonancia de micrófono

Band 3 (Mid): +3.5 dB
  └─ CRÍTICO para inteligibilidad de voz, riqueza tonal

Band 4 (High-Mid): +2.0 dB
  └─ Presencia, articulación, definición

Band 5 (Treble): -1.5 dB
  └─ Evita sibilancia (la "s" demasiado notoria)

RESULTADO: Voz clara, cálida, sin dureza

═══════════════════════════════════════════════════════════════

🎚️ COMPRESOR MULTIBANDA - SUAVE Y NATURAL
────────────────────────────────────────────

BANDA 1-2 (SUB-BASS/BASS): BYPASS o valores mínimos
├─ Threshold: -25 dB (muy alto, no afecta)
├─ Ratio: 1.5:1 (casi transparente)
└─ Justificación: No queremos comprimir bajos

BANDA 3 (MID): CONTROL LIGERO
├─ Threshold: -15 dB
├─ Ratio: 2:1 (compresión muy suave)
├─ Attack: 10 ms
├─ Release: 150 ms
├─ Makeup Gain: +2 dB
└─ Efecto: Estabiliza la voz sin cambiar carácter

BANDA 4 (HIGH-MID): CONTROL PRESENCIA
├─ Threshold: -14 dB
├─ Ratio: 2:1
├─ Attack: 5 ms
├─ Release: 80 ms
├─ Makeup Gain: +2 dB
└─ Efecto: Mantiene consistencia de presencia

BANDA 5 (TREBLE): MUY SUAVE
├─ Threshold: -12 dB
├─ Ratio: 1.5:1
├─ Attack: 2 ms
├─ Release: 50 ms
└─ Efecto: Protege solo de picos extremos

═══════════════════════════════════════════════════════════════

📈 EQ GRÁFICO - REFINAMIENTO FINO
──────────────────────────────────

20 Hz:   -4 dB  (elimina rumble bajo)
50 Hz:   -3 dB  (reduce ruido ambiental)
100 Hz:  -2 dB  (reduce boominess)
250 Hz:   0 dB  (neutro)
500 Hz:   0 dB  (neutro)
1 kHz:    0 dB  (referencia)
2 kHz:   +2 dB  (articulación, voz)
4 kHz:   +3 dB  (presencia)
8 kHz:   +1 dB  (aire, cuidado sibilancia)
16 kHz:   0 dB  (evita dureza)

═══════════════════════════════════════════════════════════════

🔒 DUAL BAND LIMITER - SEGURIDAD SUAVE
───────────────────────────────────────

LOW BAND: MINIMAL
├─ Threshold: -15 dB
├─ Ratio: 2:1
└─ Solo para prevenir boom

HIGH BAND: PROTECCIÓN ACTIVA
├─ Threshold: -12 dB (sensible)
├─ Ratio: 3:1
├─ Attack: 2 ms
├─ Release: 50 ms
└─ Efecto: Protege contra picos de sibilancia

═══════════════════════════════════════════════════════════════

🎸 BASS EQ
──────────
├─ Bass Boost: 0 dB (desactivado)
├─ Razón: Queremos bajos mínimos para podcasts
└─ Focus: Inteligibilidad sobre bajos

═══════════════════════════════════════════════════════════════

🔄 STEREO ENHANCER
──────────────────
├─ Width: 1.0x (neutro)
├─ Mono Compatible: ON (muchos escuchan en mono)
└─ Razón: Conversación, no necesita expansión

═══════════════════════════════════════════════════════════════

📤 OUTPUT
─────────
├─ Master Volume: -9 dB (margen de seguridad para edición)
├─ Output Level: -15 dB a -10 dB
└─ Picos: -4 dB máximo

═══════════════════════════════════════════════════════════════

🛑 NORMAS DE AUDIO PARA PODCASTS
─────────────────────────────────
├─ LUFS: -16 a -14 LUFS (estándar Spotify)
├─ Picos: -3 dB FS máximo
├─ Rango dinámico: 4-6 dB (controlado pero natural)
└─ Ruido de fondo: < -40 dB
```

---

## 3️⃣ MÚSICA EN VIVO (STREAMING)

### Configuración para Retransmisión de Conciertos

```
OBJETIVO: Sonido potente, dinámico, profesional sin distorsión

═══════════════════════════════════════════════════════════════

🎵 INPUT
────────
├─ Input Gain: -6 dB (micrófono dinámico para voz + instrumento)
├─ Input Device: Interfaz de audio multi-entrada
└─ Meta: Input Level entre -18 y -12 dB

═══════════════════════════════════════════════════════════════

🎛️ EQ PARAMÉTRICO - SONIDO MUSICAL
────────────────────────────────────

Band 1 (Sub-Bass): +2.0 dB
  └─ Impacto de bajos sin rumble

Band 2 (Bass): +2.5 dB
  └─ Punch y presencia

Band 3 (Mid): +0.5 dB
  └─ Cuerpo sin nasal

Band 4 (High-Mid): +1.5 dB
  └─ Presencia sin dureza

Band 5 (Treble): +1.5 dB
  └─ Aire y brillantez

RESULTADO: Curva "smiley" clásica de música pop/rock

═══════════════════════════════════════════════════════════════

🎚️ COMPRESOR MULTIBANDA - CONTROLADO
──────────────────────────────────────

BANDA 1 (SUB-BASS): CONTROL SUAVE
├─ Threshold: -20 dB
├─ Ratio: 3:1
├─ Attack: 15 ms (permite transientes)
├─ Release: 120 ms
├─ Makeup Gain: +3 dB
└─ Efecto: Bajos presentes pero controlados

BANDA 2 (BASS): IMPACTO CONSISTENTE
├─ Threshold: -18 dB
├─ Ratio: 3:1
├─ Attack: 10 ms
├─ Release: 100 ms
├─ Makeup Gain: +3 dB
└─ Efecto: Kick drum consistente

BANDA 3 (MID): CUERPO
├─ Threshold: -16 dB
├─ Ratio: 2.5:1
├─ Attack: 8 ms
├─ Release: 80 ms
├─ Makeup Gain: +2 dB
└─ Efecto: Voces definidas

BANDA 4 (HIGH-MID): PRESENCIA
├─ Threshold: -15 dB
├─ Ratio: 2.5:1
├─ Attack: 5 ms
├─ Release: 60 ms
├─ Makeup Gain: +2 dB
└─ Efecto: Voz al frente

BANDA 5 (TREBLE): AIRE CONTROLADO
├─ Threshold: -13 dB
├─ Ratio: 2:1
├─ Attack: 2 ms
├─ Release: 40 ms
├─ Makeup Gain: +1 dB
└─ Efecto: Brillantez sin sibilancia

═══════════════════════════════════════════════════════════════

📈 EQ GRÁFICO
─────────────

20 Hz:   +1 dB  (sub-bajos)
50 Hz:   +2 dB  (bajos)
100 Hz:  +1 dB  (presencia bajos)
250 Hz:   0 dB  (neutro)
500 Hz:  -1 dB  (ligera reducción)
1 kHz:    0 dB  (referencia)
2 kHz:   +1 dB  (presencia)
4 kHz:   +2 dB  (claridad)
8 kHz:   +1.5 dB (aire)
16 kHz:  +1 dB  (brillo)

═══════════════════════════════════════════════════════════════

🔒 DUAL BAND LIMITER
────────────────────

LOW BAND: PROTECCIÓN BAJOS
├─ Threshold: -18 dB
├─ Ratio: 4:1 (limitador de bajos)
└─ Previene boom en kickdrum

HIGH BAND: PROTECCIÓN GENERAL
├─ Threshold: -14 dB
├─ Ratio: 3:1
└─ Evita clipping en transientes

═══════════════════════════════════════════════════════════════

🎸 BASS EQ
──────────
├─ Bass Boost: +5 dB
├─ Bass Frequency: 80 Hz
└─ Efecto: Impacto de bajos bien definido

═══════════════════════════════════════════════════════════════

🔄 STEREO ENHANCER
──────────────────
├─ Width: 1.25x (expansión leve)
├─ Mono Compatible: ON (broadcasting seguro)
└─ Efecto: Imagen estéreo mejorada pero mono-compatible

═══════════════════════════════════════════════════════════════

📤 OUTPUT
─────────
├─ Master Volume: -5 dB (margen para picos)
├─ Output Level: -10 dB a -6 dB
└─ Meta: Máximo energía sin clipping

═══════════════════════════════════════════════════════════════

📊 ANÁLISIS ESPECTRAL IDEAL
──────────────────────────
├─ Bajos (20-250 Hz): 30% energía
├─ Medios (250-2k Hz): 35% energía
├─ Agudos (2-20k Hz): 35% energía
└─ Distribución: Balanceada, vibrante, dinámica
```

---

## 4️⃣ MASTERIZACIÓN RÁPIDA EN VOZ

### Procesamiento Profesional de Voces

```
OBJETIVO: Voz grabada lista para radio, podcast o YouTube

═══════════════════════════════════════════════════════════════

🎙️ INPUT
────────
├─ Input Gain: -8 dB (voces grabadas)
└─ Meta: Evitar clipping, espacio para procesamiento

═══════════════════════════════════════════════════════════════

🎛️ EQ PARAMÉTRICO - VOCES PROFESIONALES
─────────────────────────────────────────

Band 1 (Sub-Bass): -6.0 dB
  └─ Elimina completamente rumble y ruido ambiental

Band 2 (Bass): -2.5 dB
  └─ Reduce boominess de micrófono cercano

Band 3 (Mid): +4.0 dB ⭐ CRÍTICO
  └─ Máxima inteligibilidad y presencia de voz

Band 4 (High-Mid): +2.5 dB
  └─ Claridad, articulación, "brillo"

Band 5 (Treble): 0.0 dB
  └─ Mantiene natural, evita sibilancia excesiva

═══════════════════════════════════════════════════════════════

📈 EQ GRÁFICO - CIRUGÍA DE FRECUENCIAS
───────────────────────────────────────

20 Hz:   -6 dB  (elimina rumble)
50 Hz:   -4 dB  (elimina boominess)
100 Hz:  -2 dB  (reduce resonancia)
250 Hz:  -1 dB  (reduce "caja")
500 Hz:   0 dB  (neutro)
1 kHz:    0 dB  (referencia)
2 kHz:   +2 dB  (presencia)
4 kHz:   +3 dB  (claridad)
8 kHz:   +1 dB  (aire)
16 kHz: -1 dB   (evita dureza)

═══════════════════════════════════════════════════════════════

🎚️ COMPRESOR MULTIBANDA - CONTROL CONSISTENTE
────────────────────────────────────────────────

BANDA 1: ELIMINADA
└─ Threshold: -30 dB (sin efecto, Sub-bass a -6dB EQ ya eliminado)

BANDA 2: MÍNIMA
├─ Threshold: -22 dB
├─ Ratio: 2:1
└─ Solo para protección

BANDA 3 (MID): CONTROL ACTIVO ⭐
├─ Threshold: -14 dB (sensible, aquí está la voz)
├─ Ratio: 3:1 (compresión clara)
├─ Attack: 8 ms
├─ Release: 120 ms (suave)
├─ Makeup Gain: +3 dB
└─ Efecto: Voz consistente, profesional

BANDA 4 (HIGH-MID): CONTROL PRESENCIA
├─ Threshold: -13 dB
├─ Ratio: 2.5:1
├─ Attack: 5 ms
├─ Release: 80 ms
├─ Makeup Gain: +2.5 dB
└─ Efecto: Presencia controlada

BANDA 5: PROTECCIÓN AGUDOS
├─ Threshold: -11 dB (alta sensibilidad)
├─ Ratio: 2:1
├─ Attack: 1 ms (rápida)
├─ Release: 40 ms
└─ Efecto: Evita sibilancia

═══════════════════════════════════════════════════════════════

🔒 DUAL BAND LIMITER - SEGURIDAD MÁXIMA
────────────────────────────────────────

LOW BAND: INACTIVO
├─ Threshold: -25 dB
└─ (Ya está controlado por EQ y compresor)

HIGH BAND: ACTIVO
├─ Threshold: -10 dB (muy sensible)
├─ Ratio: 8:1 (limitador duro)
├─ Attack: 0.5 ms (protección inmediata)
├─ Release: 30 ms
└─ Efecto: Última línea de defensa contra clipping

═══════════════════════════════════════════════════════════════

🎸 BASS EQ: DESACTIVADO
───────────────────────
├─ Bass Boost: 0 dB
└─ Razón: EQ paramétrico ya lo controla todo

═══════════════════════════════════════════════════════════════

🔄 STEREO ENHANCER
──────────────────
├─ Width: 1.0x (mono puro o estéreo mínimo)
├─ Mono Compatible: ON
└─ Razón: Voces en mono para máxima compatibilidad

═══════════════════════════════════════════════════════════════

📤 OUTPUT
─────────
├─ Master Volume: -12 dB (reserva máxima para edición posterior)
├─ Output Level Objetivo: -20 dB a -15 dB
└─ Razón: Permitir ganancia después en DAW

═══════════════════════════════════════════════════════════════

✅ CHECKLIST VARIAS TOMAS
────────────────────────
□ Procesa 3 tomas diferentes
□ Compara sonidos antes/después
□ Verifica sibilancia (escucha "s" y "sh")
□ Verifica claridad de consonantes (p, t, k)
□ Verifica resonancia (no hay boom)
□ Nivel consistente durante tomas largas
□ Sin clipping en ningún momento
```

---

## 5️⃣ MASTERIZACIÓN DE MÚSICA ELECTRÓNICA

### Para Música EDM, Synthwave, Darkwave

```
OBJETIVO: Bajos profundos, dinámicos controlados, brillo sin dureza

═══════════════════════════════════════════════════════════════

🎵 INPUT
────────
├─ Input Gain: -4 dB (música masterizada, ya comprimida)
└─ Meta: Preservar dinámicos sin clipping

═══════════════════════════════════════════════════════════════

🎛️ EQ PARAMÉTRICO - BAJOS MONSTRUOSOS
──────────────────────────────────────

Band 1 (Sub-Bass): +5.0 dB ⭐ ULTRA BAJOS
  └─ Bajos profundos, sub-20 Hz presente

Band 2 (Bass): +4.5 dB
  └─ Punch de kick drum, impacto

Band 3 (Mid): -1.5 dB
  └─ Ligera reducción para evitar masking

Band 4 (High-Mid): +0.5 dB
  └─ Ligera presencia en sintetizadores

Band 5 (Treble): +2.5 dB
  └─ Brillo, aire, "sizzle" de hi-hats

═══════════════════════════════════════════════════════════════

📈 EQ GRÁFICO - EXCESIVO
────────────────────────

20 Hz:   +5 dB  ⭐ SUB-BAJOS EXTREMOS
50 Hz:   +4 dB  (bajos)
100 Hz:  +3 dB  (presencia bajos)
250 Hz:   0 dB  (neutro)
500 Hz:  -2 dB  (corte para claridad)
1 kHz:   -1 dB  (ligera reducción)
2 kHz:   +1 dB  (presencia)
4 kHz:   +2 dB  (claridad)
8 kHz:   +3 dB  (sizzle)
16 kHz:  +2 dB  (aire)

═══════════════════════════════════════════════════════════════

🎚️ COMPRESOR MULTIBANDA - CONTROL BAJOS
──────────────────────────────────────────

BANDA 1 (SUB-BASS): COMPRESIÓN AGRESIVA
├─ Threshold: -25 dB (muy sensible)
├─ Ratio: 5:1 (fuerte)
├─ Attack: 20 ms (permite transiente de kick)
├─ Release: 150 ms (mantiene control)
├─ Makeup Gain: +5 dB (compensa)
└─ Efecto: Bajos profundos pero muy controlados

BANDA 2 (BASS): IMPACTO CONSISTENTE
├─ Threshold: -22 dB
├─ Ratio: 4:1
├─ Attack: 15 ms
├─ Release: 120 ms
├─ Makeup Gain: +4 dB
└─ Efecto: Kick drum en el mismo nivel siempre

BANDA 3 (MID): LIGERO
├─ Threshold: -16 dB
├─ Ratio: 2:1
├─ Attack: 10 ms
├─ Release: 100 ms
└─ Efecto: Previene masking

BANDA 4: MÍNIMO
├─ Threshold: -14 dB
├─ Ratio: 1.5:1
└─ Solo protección

BANDA 5 (TREBLE): PROTECCIÓN
├─ Threshold: -12 dB
├─ Ratio: 2:1
├─ Attack: 2 ms
└─ Evita clipping en hi-hats

═══════════════════════════════════════════════════════════════

🔒 DUAL BAND LIMITER - CRÍTICO
───────────────────────────────

LOW BAND: LIMITADOR DURO
├─ Threshold: -15 dB
├─ Ratio: 8:1 (máximo)
├─ Attack: 15 ms
└─ Release: 100 ms
└─ Previene boom digital

HIGH BAND: LIMITADOR MEDIO
├─ Threshold: -12 dB
├─ Ratio: 4:1
└─ Protección general

═══════════════════════════════════════════════════════════════

🎸 BASS EQ - MONSTER MODE
──────────────────────────
├─ Bass Boost: +12 dB ⭐ MÁXIMO
├─ Bass Frequency: 40 Hz (muy profundo)
└─ Efecto: Bajos casi sub-sónicos

═══════════════════════════════════════════════════════════════

🔄 STEREO ENHANCER
──────────────────
├─ Width: 1.3x (expansión controlada)
├─ Mono Compatible: ON (seguridad)
└─ Efecto: Espacioso pero seguro

═══════════════════════════════════════════════════════════════

📤 OUTPUT - CUIDADO
───────────────────
├─ Master Volume: -10 dB (margen amplio)
├─ Output Level: -12 dB a -8 dB
└─ CRÍTICO: Evitar clipping digital

═══════════════════════════════════════════════════════════════

⚠️ NOTAS IMPORTANTES
────────────────────
1. Escucha en VARIOS sistemas de sonido:
   └─ Auriculares, altavoces pequeños, bajos de auto

2. Verifica en MONO:
   └─ Asegúrate que bajos no cancelen

3. Toma descansos auditivos:
   └─ La fatiga auditiva afecta juicio

4. Compara con referencias:
   └─ Ten track profesional similar para comparar

5. Cuidado con exceso:
   └─ Bajos extremos pueden ser demasiado para parlantes pequeños
```

---

## 6️⃣ CONFIGURACIÓN PARA VOZ CANTADA

### Procesamiento de Vocalista en Vivo o Estudio

```
OBJETIVO: Voz clara, presencia, compresión natural, sonido profesional

═══════════════════════════════════════════════════════════════

🎤 INPUT
────────
├─ Input Gain: -8 dB (evitar clipping en notas fuertes)
├─ Input Device: Micrófono de condensador de estudio
└─ Meta: Input Level entre -18 y -12 dB

═══════════════════════════════════════════════════════════════

🎛️ EQ PARAMÉTRICO - VOCALISTA PRO
──────────────────────────────────

Band 1 (Sub-Bass): -8.0 dB
  └─ Elimina completamente subsónicos y rumble

Band 2 (Bass): -1.0 dB
  └─ Preserva cuerpo, reduce boominess

Band 3 (Mid): +2.0 dB
  └─ Cuerpo vocal, calidez

Band 4 (High-Mid): +3.0 dB ⭐
  └─ CRÍTICO: Presencia, distingo, claridad

Band 5 (Treble): +0.5 dB
  └─ Aire sin sibilancia

═══════════════════════════════════════════════════════════════

📈 EQ GRÁFICO - FINO
───────────────────

20 Hz:   -8 dB  (elimina rumble)
50 Hz:   -4 dB  (reduce boominess)
100 Hz:  -1 dB  (preserva cuerpo)
250 Hz:  +1 dB  (cuerpo vocal)
500 Hz:   0 dB  (neutro)
1 kHz:   +1 dB  (claridad)
2 kHz:   +2 dB  (presencia)
4 kHz:   +3 dB  (distingo)
8 kHz:   +1 dB  (aire)
16 kHz: -1 dB   (evita sibilancia de "S")

═══════════════════════════════════════════════════════════════

🎚️ COMPRESOR MULTIBANDA - CONTROL VOCÁLICO
──────────────────────────────────────────────

BANDA 1: BYPASS (ya eliminado por EQ)

BANDA 2: LIGERO
├─ Threshold: -20 dB
├─ Ratio: 1.5:1
└─ Solo estabilización

BANDA 3 (MID): CONTROL SUAVE
├─ Threshold: -16 dB
├─ Ratio: 2:1 (muy suave)
├─ Attack: 10 ms
├─ Release: 150 ms (natural)
├─ Makeup Gain: +2 dB
└─ Efecto: Estabiliza cuerpo sin cambiar timbre

BANDA 4 (HIGH-MID): CONTROL PRESENCIA ⭐
├─ Threshold: -14 dB
├─ Ratio: 2.5:1
├─ Attack: 5 ms
├─ Release: 80 ms
├─ Makeup Gain: +2.5 dB
└─ Efecto: Mantiene presencia consistente

BANDA 5 (TREBLE): PROTECCIÓN
├─ Threshold: -12 dB
├─ Ratio: 2:1
├─ Attack: 2 ms
├─ Release: 50 ms
└─ Evita sibilancia

═══════════════════════════════════════════════════════════════

🔒 DUAL BAND LIMITER
────────────────────

LOW BAND: MÍNIMO
├─ Threshold: -18 dB
├─ Ratio: 2:1
└─ Solo protección

HIGH BAND: ACTIVO
├─ Threshold: -12 dB
├─ Ratio: 3:1
├─ Attack: 2 ms
└─ Release: 40 ms

═══════════════════════════════════════════════════════════════

🎸 BASS EQ
──────────
├─ Bass Boost: +1 dB (mínimo)
└─ Razón: Queremos voz en primer plano

═══════════════════════════════════════════════════════════════

🔄 STEREO ENHANCER
──────────────────
├─ Width: 1.0x (mono puro para voz)
├─ Mono Compatible: ON (siempre)
└─ Razón: La voz es instrumento mono

═══════════════════════════════════════════════════════════════

📤 OUTPUT
─────────
├─ Master Volume: -8 dB (margen para dinámicos de voz)
├─ Output Level: -14 dB a -10 dB
└─ Picos: -3 dB máximo

═══════════════════════════════════════════════════════════════

🎤 TIPS VOCALES
───────────────
1. Prueba diferentes tipos de canciones:
   └─ Aguda (soprano) vs grave (bajo)

2. Verifica "S" y "SH":
   └─ Deben ser presentes pero no duras

3. Verifica "B" y "P":
   └─ Deben ser claras sin plosiva

4. Toma descansos auditivos cada 5 min:
   └─ Fatiga = mal juicio

5. Mezcla con referencia:
   └─ Compara con cantante profesional similar
```

---

## 🎯 TABLA COMPARATIVA RÁPIDA

```
╔════════════════════╦═════════╦══════════╦═════════╦═══════════════╗
║   APLICACIÓN       ║  INPUT  ║  SUB-B   ║  BASS   ║  HIGH-MID     ║
║                    ║  GAIN   ║  BAND    ║  BAND   ║   BAND        ║
╠════════════════════╬═════════╬══════════╬═════════╬═══════════════╣
║ Radio FM           ║  -12 dB ║  +1.5 dB ║ +2.5 dB ║   +2.0 dB     ║
║ Podcast            ║  -10 dB ║  -4.0 dB ║ -2.0 dB ║   +2.0 dB     ║
║ Música Viva        ║   -6 dB ║  +2.0 dB ║ +2.5 dB ║   +1.5 dB     ║
║ Voz Cantada        ║   -8 dB ║  -8.0 dB ║ -1.0 dB ║   +3.0 dB ⭐  ║
║ Electrónica        ║   -4 dB ║  +5.0 dB ║ +4.5 dB ║   +0.5 dB     ║
║ Masterización Voz  ║   -8 dB ║  -6.0 dB ║ -2.5 dB ║   +2.5 dB     ║
╚════════════════════╩═════════╩══════════╩═════════╩═══════════════╝
```

---

## 📝 NOTAS FINALES

### Principios Generales

1. **Nunca confíes solo en un sistema**
   - Escucha en auriculares, altavoces, coche, auto

2. **Compara con referencia**
   - Ten un track profesional similar para comparar

3. **Toma descansos**
   - 5 minutos cada 20 minutos

4. **Confía en tu instinto**
   - Si suena bien, probablemente lo es

5. **Cuidado con excesos**
   - Menos es más en 90% de casos

6. **Documentar tus ajustes**
   - Anota qué funcionó para futuros proyectos

---

**RADIO PRO - Advanced Presets v1.0** | ¡Disfruta del procesamiento profesional! 🎛️✨
