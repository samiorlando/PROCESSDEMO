# 🎛️ RADIO PRO - Procesador de Audio Profesional
## Documentación Técnica y Guía de Uso

---

## 📋 TABLA DE CONTENIDOS
1. Descripción General
2. Características Principales
3. Arquitectura del Sistema
4. Guía de Uso
5. Presets Predefinidos
6. Consejos Profesionales
7. Especificaciones Técnicas

---

## 1️⃣ DESCRIPCIÓN GENERAL

**RADIO PRO** es una aplicación web profesional de procesamiento de audio en tiempo real, diseñada siguiendo los estándares de procesadores de broadcast tipo radio (Optimod-style). Utiliza la **Web Audio API** para proporcionar DSP de alta calidad directamente en el navegador.

### Características Clave:
- ✅ Interfaz estilo consola de radio profesional (Dark Mode)
- ✅ Procesamiento de audio en tiempo real sin latencia perceptible
- ✅ Ecualizadores multibanda y gráficos
- ✅ Compresores independientes por banda de frecuencia
- ✅ Limitador de salida para evitar clipping
- ✅ Analizador de espectro en vivo (FFT)
- ✅ Medidores de nivel en tiempo real
- ✅ Presets predefinidos para radio, voz, música
- ✅ Controles intuitivos tipo perillas (Knobs) y sliders

---

## 2️⃣ CARACTERÍSTICAS PRINCIPALES

### A. SECCIÓN INPUT (Entrada de Audio)
**Ubicación**: Panel Izquierdo

#### Selector de Dispositivo de Entrada
```
Audio Input → Select Device...
```
- Enumera automáticamente todos los dispositivos de entrada disponibles
- Micrófono, línea de entrada, entrada del sistema
- Requiere permiso del navegador la primera vez

#### Control de Ganancia de Entrada
```
Input Gain: -24 dB a +24 dB
```
- Ajusta el nivel de captura antes del procesamiento
- Rango: -24 dB a +24 dB (paso de 0.1 dB)
- Uso: Evitar clipping en la entrada o amplificar señales débiles

#### Medidor de Nivel de Entrada (VU Meter)
```
Rango visual: -60 dB a 0 dB
```
- Barra de color: Verde → Amarillo → Rojo
- Verde (< -20 dB): Nivel seguro
- Amarillo (-20 a -1 dB): Nivel óptimo
- Rojo (> -1 dB): Riesgo de clipping

#### LED de Detección de Clipping
```
🔴 Rojo intermitente = Clipping detectado
🟢 Apagado = Sin clipping
```

---

### B. SECCIÓN OUTPUT (Salida de Audio)
**Ubicación**: Panel Izquierdo

#### Selector de Dispositivo de Salida
```
Output Device → Select Device...
```
- Selecciona el dispositivo de salida
- Altavoces, auriculares, interfaz de audio externa

#### Control de Volumen Master
```
Master Volume: -40 dB a +6 dB
```
- Control principal de volumen de salida
- Paso de 0.1 dB
- Rango: -40 dB (muy bajo) a +6 dB (muy fuerte)

#### Medidor de Nivel de Salida (Peak + RMS)
```
Rango visual: -60 dB a 0 dB
```
- Muestra el nivel después de todo el procesamiento
- Ideal para evitar distorsión digital final

---

### C. EQ PARAMÉTRICO (5 Bandas)
**Ubicación**: Panel Central Superior

#### Estructura de Bandas:
```
1. SUB-BASS (20Hz - 60Hz)
   ├─ Rango de Ganancia: -12 dB a +12 dB
   └─ Uso: Bajos muy profundos

2. BASS (60Hz - 250Hz)
   ├─ Rango de Ganancia: -12 dB a +12 dB
   └─ Uso: Bajos controlados, presencia

3. MID (250Hz - 2kHz)
   ├─ Rango de Ganancia: -12 dB a +12 dB
   └─ Uso: Claridad, riqueza tonal

4. HIGH-MID (2kHz - 6kHz)
   ├─ Rango de Ganancia: -12 dB a +12 dB
   └─ Uso: Presencia, claridad de voz

5. TREBLE (6kHz - 16kHz)
   ├─ Rango de Ganancia: -12 dB a +12 dB
   └─ Uso: Brillantez, agudos
```

#### Visualización de Curva EQ:
- Gráfico en tiempo real que muestra la curva de ecualización
- Permite ver cómo cada banda afecta el espectro general
- Grid de referencia para frecuencias

#### Control Individual:
- Deslizador vertical por banda
- Visualización de valor en dB
- Intervalo mínimo: 0.1 dB

---

### D. ANALIZADOR DE ESPECTRO (FFT)
**Ubicación**: Panel Central

#### Características:
```
Resolución: FFT 2048 puntos
Rango de Frecuencia: 20Hz - 20kHz
Actualización: 60 FPS (tiempo real)
```

#### Visualización:
- Barras de frecuencia con colores
- Línea superpuesta (envelope)
- Grid de referencia
- Análisis tanto de entrada como de salida

---

### E. COMPRESOR MULTIBANDA (5 Bandas Independientes)
**Ubicación**: Panel Central

#### Parámetros por Banda:

**Threshold (Umbral de Compresión)**
```
Rango: -60 dB a 0 dB
Uso: Nivel en el que comienza la compresión
Recomendación:
  ├─ Bajos: -20 dB a -15 dB
  ├─ Medios: -20 dB a -18 dB
  └─ Agudos: -18 dB a -12 dB
```

**Ratio (Relación de Compresión)**
```
Rango: 1:1 a 8:1
Valores comunes:
  ├─ 1:1 = Sin compresión
  ├─ 2:1 = Compresión suave
  ├─ 4:1 = Compresión media
  ├─ 6:1 = Compresión fuerte
  └─ 8:1 = Compresión extrema (Limitador)
```

**Attack (Tiempo de Ataque)**
```
Rango: 1 ms a 100 ms
Uso: Qué tan rápido reacciona el compresor
Valores recomendados:
  ├─ Bajos: 10-20 ms (respuesta controlada)
  ├─ Medios: 5-10 ms (respuesta rápida)
  └─ Agudos: 1-5 ms (respuesta muy rápida)
```

**Release (Tiempo de Liberación)**
```
Rango: 10 ms a 500 ms
Uso: Qué tan rápido vuelve a su nivel normal
Valores recomendados:
  ├─ Bajos: 100-200 ms (respuesta natural)
  ├─ Medios: 50-100 ms (respuesta media)
  └─ Agudos: 30-50 ms (respuesta rápida)
```

**Makeup Gain (Ganancia de Compensación)**
```
Rango: 0 dB a +12 dB
Uso: Compensa la reducción de ganancia por compresión
Automático en la mayoría de casos
```

---

### F. ECUALIZADOR GRÁFICO (10 Bandas)
**Ubicación**: Panel Derecho

#### Frecuencias:
```
1.  20 Hz   (Sub-bass profundo)
2.  50 Hz   (Sub-bass)
3.  100 Hz  (Bass)
4.  250 Hz  (Bass/Mids)
5.  500 Hz  (Mids bajos)
6.  1 kHz   (Mids)
7.  2 kHz   (Mids altos)
8.  4 kHz   (Presence)
9.  8 kHz   (Brilliance)
10. 16 kHz  (Air)
```

#### Rango de Ganancia por Banda:
```
-12 dB (Atenúa) ↔ 0 dB (Neutral) ↔ +12 dB (Refuerza)
```

#### Controles Verticales:
- Cada frecuencia tiene un deslizador vertical
- Posición visual de arriba hacia abajo
- Valores en dB mostrados en tiempo real

---

### G. DUAL BAND COMPRESSOR LIMITER
**Ubicación**: Panel Derecho

#### División de Bandas:
```
LOW BAND: 20 Hz - 500 Hz
├─ Threshold: -60 dB a 0 dB
├─ Ratio: 1:1 a 8:1
├─ Attack: 1 ms a 100 ms
└─ Release: 10 ms a 500 ms

HIGH BAND: 500 Hz - 20 kHz
├─ Threshold: -60 dB a 0 dB
├─ Ratio: 1:1 a 8:1
├─ Attack: 1 ms a 100 ms
└─ Release: 10 ms a 500 ms
```

#### Configuración Recomendada para Broadcast:
```
LOW BAND (Graves):
├─ Threshold: -20 dB
├─ Ratio: 4:1
├─ Attack: 10 ms
└─ Release: 100 ms

HIGH BAND (Treble):
├─ Threshold: -15 dB
├─ Ratio: 3:1
├─ Attack: 5 ms
└─ Release: 50 ms
```

---

### H. BASS EQ (GRAVES ESPECIALIZADOS)
**Ubicación**: Panel Derecho

#### Bass Boost
```
Rango: 0 dB a +12 dB
Paso: 0.1 dB
Uso: Refuerzo controlado de bajos
```

#### Bass Frequency
```
Rango: 20 Hz a 200 Hz
Paso: 5 Hz
Uso: Seleccionar la frecuencia central del refuerzo
```

#### Filtro Low Shelf:
```
Tipo: Shelving filter
Atenuación: -12 dB a +12 dB
Pendiente: 0.5 octavas / octava
```

#### "Bass Boost Pro" Botón:
```
Aplica un refuerzo automático inteligente
├─ Aumenta el impacto percibido
├─ Mantiene el control
└─ Evita distorsión
```

---

### I. STEREO ENHANCER
**Ubicación**: Panel Derecho

#### Width (Ancho Estéreo)
```
Rango: 0.0x a 2.0x
Valores:
├─ 0.0x = Mono puro
├─ 0.5x = Estéreo reducido
├─ 1.0x = Estéreo normal
├─ 1.5x = Estéreo expandido
└─ 2.0x = Estéreo extremo
```

#### Modo Mono Compatible:
```
Checkbox: Mono Compatible
Uso: Asegurar compatibilidad con sistemas mono
      sin cancelación de fase
```

---

## 3️⃣ ARQUITECTURA DEL SISTEMA

### Diagrama de Flujo de Audio:

```
┌─────────────────────────────────────────────────────────────┐
│                    ENTRADA DE AUDIO                         │
│        (Micrófono / Entrada del Sistema)                   │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│              INPUT GAIN NODE                                │
│           Amplificación / Atenuación (-24 a +24 dB)        │
└────────────────────────┬────────────────────────────────────┘
                         │
                         ▼
┌─────────────────────────────────────────────────────────────┐
│         ANALYSER NODE (Input Metering)                      │
│         VU Meter, Clipping Detection, Spectrum             │
└────────────────────────┬────────────────────────────────────┘
                         │
                   ┌─────┴──────────────────────────┐
                   │                                │
                   ▼                                ▼
            ┌──────────────┐            ┌──────────────────┐
            │  EQ BAND 1   │            │  COMPRESSOR 1    │
            │  (20-60 Hz)  │            │  (Threshold...)  │
            └──────────────┘            └──────────────────┘
                   │                                │
                   ▼                                ▼
            ┌──────────────┐            ┌──────────────────┐
            │  EQ BAND 2   │            │  COMPRESSOR 2    │
            │  (60-250 Hz) │            │  (Threshold...)  │
            └──────────────┘            └──────────────────┘
                   │                                │
                   ▼                                ▼
            ┌──────────────┐            ┌──────────────────┐
            │  EQ BAND 3   │            │  COMPRESSOR 3    │
            │  (250-2kHz)  │            │  (Threshold...)  │
            └──────────────┘            └──────────────────┘
                   │                                │
                   ▼                                ▼
            ┌──────────────┐            ┌──────────────────┐
            │  EQ BAND 4   │            │  COMPRESSOR 4    │
            │  (2-6 kHz)   │            │  (Threshold...)  │
            └──────────────┘            └──────────────────┘
                   │                                │
                   ▼                                ▼
            ┌──────────────┐            ┌──────────────────┐
            │  EQ BAND 5   │            │  COMPRESSOR 5    │
            │  (6-16 kHz)  │            │  (Threshold...)  │
            └──────────────┘            └──────────────────┘
                   │                                │
                   └──────────┬────────────────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │  GRAPHIC EQ          │
                   │  10-Band Equalizer   │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │  DUAL BAND           │
                   │  Compressor/Limiter  │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │  BASS EQ             │
                   │  Low Shelf Filter    │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │  STEREO ENHANCER     │
                   │  Width Control       │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │  LIMITER FINAL       │
                   │  Prevención Clipping │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │  MASTER VOLUME       │
                   │  (-40 a +6 dB)       │
                   └──────────┬───────────┘
                              │
                              ▼
        ┌─────────────────────────────────────────┐
        │  OUTPUT ANALYSER NODE                   │
        │  Level Metering, Clipping Detection    │
        └─────────────────────┬───────────────────┘
                              │
                              ▼
        ┌─────────────────────────────────────────┐
        │        SALIDA DE AUDIO                  │
        │    (Altavoces / Auriculares)           │
        └─────────────────────────────────────────┘
```

### Módulos JavaScript:

```javascript
1. AudioProcessor
   ├─ init()              // Inicializar Web Audio API
   ├─ startAudio()        // Iniciar captura
   ├─ stopAudio()         // Detener captura
   ├─ getAudioDevices()   // Enumerar dispositivos
   └─ state              // Estado DSP

2. UI Controls
   ├─ initializeUI()     // Inicializar interfaz
   ├─ updateInputGain()  // Actualizar ganancia entrada
   ├─ updateMasterVolume() // Actualizar volumen
   └─ drawEQCurve()      // Dibujar gráfico EQ

3. Analysis
   ├─ startAnalysis()    // Análisis en vivo
   ├─ calculateLevel()   // Cálculo de nivel en dB
   ├─ updateSpectrum()   // Actualizar espectro
   └─ updateMeters()     // Actualizar medidores
```

---

## 4️⃣ GUÍA DE USO

### Paso 1: Iniciar la Aplicación

1. Abre el archivo `audio-processor.html` en tu navegador web moderno
   - Soportados: Chrome 70+, Firefox 75+, Safari 14+, Edge 79+

2. Haz clic en el botón **"⚪ POWER ON"** en la esquina superior izquierda

3. El navegador te pedirá permiso para acceder al micrófono
   - Selecciona "Permitir" para continuar

4. Cuando esté activo verás:
   - Botón cambia a "⚫ POWER OFF" de color verde
   - LED de estado verde junto a "Status: Grabando"
   - Medidores de nivel mostrando actividad

### Paso 2: Seleccionar Dispositivos

**Input Device:**
```
1. Haz clic en el selector "Audio Input"
2. Elige tu micrófono o entrada de sistema
3. La captura comenzará automáticamente
```

**Output Device:**
```
1. Haz clic en el selector "Output Device"
2. Elige tus altavoces o auriculares
3. El audio procesado saldrá por este dispositivo
```

### Paso 3: Ajustar Input Gain

```
Objetivo: Que el medidor "Input Level" esté en amarillo (-20 a -10 dB)

Procedimiento:
1. Habla o genera sonido en el micrófono
2. Observa la barra "Input Level"
   ├─ Si está muy baja (verde): Aumenta Input Gain
   ├─ Si está en amarillo: ¡Perfecto!
   └─ Si está roja: Reduce Input Gain
3. Ajusta con el deslizador de "Input Gain" (-24 a +24 dB)
```

### Paso 4: Aplicar Preset

**Para comenzar rápidamente:**

```
Botones disponibles en Panel Izquierdo:

🎙️ RADIO FM: Perfecto para voz clara y transmisión
└─ EQ optimizado para inteligibilidad
└─ Compresión para consistencia

📢 VOZ CLARA: Ideal para podcasts y voz
└─ Aumento de medios para presencia
└─ Reducción de bajos para claridad

🎵 MÚSICA: Para música de fondo
└─ EQ balanceado
└─ Compresión suave

🔊 ULTRA BASS: Para énfasis en bajos
└─ Refuerzo de frecuencias bajas
└─ Compresión de bajos controlada
```

### Paso 5: Afinar Ecualizador Paramétrico

```
Panel Central > EQ Paramétrico (5 Bandas)

Para incrementar CLARIDAD en la voz:
├─ SUB-BASS: -2 dB (reducir ruido de fondo)
├─ BASS: 0 dB (mantener presencia)
├─ MID: +3 dB (mejorar inteligibilidad)
├─ HIGH-MID: +2 dB (presencia de voz)
└─ TREBLE: 0 dB (mantener naturalidad)

Para incrementar BAJOS POTENTES:
├─ SUB-BASS: +4 dB (bajos profundos)
├─ BASS: +3 dB (impacto)
├─ MID: 0 dB (mantener equilibrio)
├─ HIGH-MID: 0 dB
└─ TREBLE: 0 dB

Para SONIDO BRILLANTE Y AIREADO:
├─ SUB-BASS: -1 dB (reducir)
├─ BASS: 0 dB
├─ MID: -1 dB (ligera reducción)
├─ HIGH-MID: +2 dB (presencia)
└─ TREBLE: +3 dB (aire y claridad)
```

### Paso 6: Configurar Compresor Multibanda

**Para BROADCAST PROFESIONAL:**

```
BAND 1 (SUB-BASS: 20-60 Hz):
├─ Threshold: -22 dB
├─ Ratio: 4:1
├─ Attack: 15 ms
└─ Release: 120 ms

BAND 2 (BASS: 60-250 Hz):
├─ Threshold: -20 dB
├─ Ratio: 4:1
├─ Attack: 10 ms
└─ Release: 100 ms

BAND 3 (MID: 250-2k Hz):
├─ Threshold: -18 dB
├─ Ratio: 3:1
├─ Attack: 8 ms
└─ Release: 80 ms

BAND 4 (HIGH-MID: 2-6k Hz):
├─ Threshold: -16 dB
├─ Ratio: 3:1
├─ Attack: 5 ms
└─ Release: 60 ms

BAND 5 (TREBLE: 6-16k Hz):
├─ Threshold: -14 dB
├─ Ratio: 2.5:1
├─ Attack: 2 ms
└─ Release: 40 ms
```

### Paso 7: Usar Ecualizador Gráfico

```
Panel Derecho > EQ Gráfico (10 Bandas)

Para CORREGIR PROBLEMAS ESPECÍFICOS:

Problema: Ruido de aire acondicionado (~50 Hz)
Solución: Atenúa la banda de 50 Hz (-6 dB)

Problema: Resonancia o "boom" en la voz
Solución: Atenúa 100-250 Hz (-4 dB)

Problema: Falta de presencia en voz
Solución: Aumenta 2-4 kHz (+3 dB)

Problema: Demasiados agudos / sibilancia
Solución: Atenúa 5-8 kHz (-3 dB)
```

### Paso 8: Configurar Dual Band Limiter

```
CONFIGURACIÓN RECOMENDADA:

LOW BAND (20 Hz - 500 Hz):
├─ Threshold: -20 dB (Evita bajos excesivos)
├─ Ratio: 4:1
├─ Attack: 10 ms
└─ Release: 100 ms

HIGH BAND (500 Hz - 20 kHz):
├─ Threshold: -15 dB (Protección de agudos)
├─ Ratio: 3:1
├─ Attack: 5 ms
└─ Release: 50 ms
```

### Paso 9: Aplicar Bass EQ

```
Para BAJOS PROFUNDOS Y CONTROLADOS:

1. Bass Boost: +4 dB a +8 dB
2. Bass Frequency: 60 Hz (estándar)
3. Haz clic en "Bass Boost Pro"
   └─ Aplicará compresión automática de bajos

RESULTADO:
├─ Bajos más presentes
├─ Sin distorsión
└─ Controlados en dinámicos
```

### Paso 10: Ajustar Master Volume

```
PROCEDIMIENTO:

1. Observa el medidor "Output Level"
2. Ajusta Master Volume para que:
   ├─ Esté principalmente en amarillo (-20 a -10 dB)
   └─ Solo toque rojo ocasionalmente (picos)

3. Valores típicos:
   ├─ -5 dB a -10 dB: Nivel equilibrado
   └─ -15 dB a -20 dB: Más seguro (menos picos)
```

### Paso 11: Monitorear Análisis de Espectro

```
PANEL CENTRAL > Spectrum Analyzer

Qué buscar:
├─ Distribución equilibrada de frecuencias
├─ Sin picos excesivos en ninguna banda
├─ Energía presente en bajos, medios y agudos
└─ Indicador de clipping rojo = Ajustar niveles
```

---

## 5️⃣ PRESETS PREDEFINIDOS

### 🎙️ RADIO FM
**Ideal para:** Transmisión de radio, voz clara, comunicaciones

```
EQ Paramétrico:
├─ Sub-Bass:   +2.0 dB
├─ Bass:       +3.0 dB
├─ Mid:        -1.0 dB
├─ High-Mid:   +2.0 dB
└─ Treble:     +1.0 dB

Compresor Multibanda:
├─ Threshold: -20 dB
├─ Ratio: 4:1
├─ Attack: 10 ms
└─ Release: 100 ms (todos)

Bass EQ:
├─ Boost: +3.0 dB
└─ Frequency: 60 Hz

Master Volume: 0 dB
```

**Características:**
- Voz muy clara y presente
- Bajos controlados pero perceptibles
- Sonido consistente tipo radio profesional

---

### 📢 VOZ CLARA
**Ideal para:** Podcasts, conferencias, voz hablada

```
EQ Paramétrico:
├─ Sub-Bass:   -2.0 dB
├─ Bass:       -1.0 dB
├─ Mid:        +3.0 dB
├─ High-Mid:   +2.0 dB
└─ Treble:     -1.0 dB

Dual Band Limiter:
├─ Low Threshold: -20 dB
├─ High Threshold: -16 dB

Bass EQ:
├─ Boost: +1.0 dB
└─ Frequency: 60 Hz

Master Volume: 0 dB
```

**Características:**
- Máxima inteligibilidad
- Énfasis en medios (riqueza vocal)
- Mínimo ruido de fondo

---

### 🎵 MÚSICA POTENTE
**Ideal para:** Música en vivo, transmisión musical, producciones

```
EQ Paramétrico:
├─ Sub-Bass:   +1.0 dB
├─ Bass:       +2.0 dB
├─ Mid:        0.0 dB
├─ High-Mid:   +1.0 dB
└─ Treble:     +2.0 dB

Compresor Multibanda:
├─ Threshold: -18 dB (suave)
├─ Ratio: 3:1
├─ Attack: 10 ms
└─ Release: 100 ms

Bass EQ:
├─ Boost: +4.0 dB
└─ Frequency: 60 Hz

Stereo Enhancer:
├─ Width: 1.2x
└─ Mono Compatible: OFF

Master Volume: -3 dB (seguridad)
```

**Características:**
- Sonido balanceado y musical
- Bajos profundos pero controlados
- Agudos brillantes sin dureza
- Imagen estéreo mejorada

---

### 🔊 ULTRA BASS
**Ideal para:** Música electrónica, bajos profundos, géneros heavy

```
EQ Paramétrico:
├─ Sub-Bass:   +6.0 dB
├─ Bass:       +5.0 dB
├─ Mid:        -2.0 dB
├─ High-Mid:   0.0 dB
└─ Treble:     -1.0 dB

Compresor Multibanda:
├─ Threshold BAJOS: -25 dB
├─ Ratio BAJOS: 5:1
├─ Attack: 15 ms
└─ Release: 150 ms

Bass EQ:
├─ Boost: +12.0 dB
└─ Frequency: 40 Hz

Dual Band Limiter:
├─ Low Threshold: -25 dB (Ratio 6:1)
└─ High Threshold: -20 dB

Master Volume: -8 dB (muy importante!)
```

**Características:**
- Bajos enormes y impactantes
- Control de compresión inteligente
- Protección contra clipping
- ⚠️ Requiere Master Volume bajo

---

## 6️⃣ CONSEJOS PROFESIONALES

### A. Workflow Recomendado

```
1. CAPTURA DE ENTRADA (5 min)
   ├─ Prueba el micrófono
   ├─ Ajusta Input Gain
   ├─ Observa el nivel de entrada
   └─ Confirma sin clipping

2. APLICAR PRESET (2 min)
   ├─ Selecciona el preset más apropiado
   ├─ Escucha cómo suena
   └─ Ajusta si es necesario

3. AFINAR EQ PARAMÉTRICO (5 min)
   ├─ Observa la curva EQ
   ├─ Realiza ajustes sutiles
   └─ Prueba cada banda

4. CONFIGURAR COMPRESOR (3 min)
   ├─ Aumenta Threshold hasta que active
   ├─ Ajusta Ratio para suavidad
   ├─ Calibra Attack y Release
   └─ Escucha la estabilidad

5. CONTROLAR MASTER VOLUME (2 min)
   ├─ Observa Output Level
   ├─ Ajusta para máximo nivel sin clipping
   └─ Prueba con material de prueba

6. ANÁLISIS FINAL (5 min)
   ├─ Observa el espectro
   ├─ Realiza ajustes finales
   └─ Valida en auriculares
```

### B. Consejos de Gain Staging

```
ENTRADA:
├─ Input Gain: -12 dB a +0 dB (típico)
├─ Objetivo: -18 dB en Input Level
└─ Nunca permitas clipping rojo continuo

PROCESAMIENTO:
├─ Makeup Gain en Compresores: +3 dB a +6 dB
├─ EQ Boosts: Máximo +6 dB por banda
└─ Bass Boost: Máximo +12 dB

SALIDA:
├─ Master Volume: -6 dB a 0 dB
├─ Output Level Objetivo: -10 dB a -5 dB
└─ Picos ocasionales a -2 dB son aceptables
```

### C. Técnicas de Compresión Efectivas

```
COMPRESIÓN TRANSPARENTE (Invisible):
├─ Threshold: -15 dB
├─ Ratio: 2:1
├─ Attack: 10 ms
├─ Release: 100 ms
└─ Resultado: Sonido natural, más controlado

COMPRESIÓN PALPABLE (Audible):
├─ Threshold: -20 dB
├─ Ratio: 4:1
├─ Attack: 5 ms
├─ Release: 50 ms
└─ Resultado: Efecto notorio, carácter agresivo

COMPRESIÓN VINTAGE (Suave):
├─ Threshold: -10 dB
├─ Ratio: 1.5:1
├─ Attack: 20 ms
├─ Release: 200 ms
└─ Resultado: Glue, cohesión, naturalidad
```

### D. Técnicas de Ecualización

```
PARA MEJORAR CLARIDAD:
├─ Banda 3 (Mid): +2 dB a +4 dB
├─ Banda 4 (High-Mid): +1 dB a +2 dB
└─ Banda 5 (Treble): 0 dB (evitar dureza)

PARA MEJORAR BAJOS:
├─ Banda 1 (Sub-Bass): +2 dB a +4 dB
├─ Banda 2 (Bass): +1 dB a +3 dB
└─ Banda 3 (Mid): 0 dB (no nublar)

PARA REDUCIR PROBLEMAS:
├─ Ruido 60 Hz: Atenúa Banda 1 (-4 dB)
├─ Boominess 100 Hz: Atenúa Banda 2 (-3 dB)
├─ Sibilancia 5-8 kHz: Atenúa Banda 5 (-2 dB)
└─ Harshness 4 kHz: Atenúa Banda 4 (-2 dB)
```

### E. Análisis Espectral

```
LECTURA DEL ESPECTRO:

Poco energía en bajos (< 100 Hz):
├─ Posible causa: Micrófono de mala calidad
├─ Solución: Aumentar Bass EQ
└─ O usar otro micrófono

Mucha energía en medios (1-4 kHz):
├─ Posible causa: Sonido "nasal" o chillón
├─ Solución: Atenuar leve en High-Mid
└─ Aumentar bajos para equilibrio

Poco energía en agudos (> 8 kHz):
├─ Posible causa: Sonido "apagado" o sordo
├─ Solución: Aumentar Treble en EQ
└─ Cuidado: No crear sibilancia

Energía irregular:
├─ Posible causa: Resonancias específicas
├─ Solución: Usar EQ gráfico para corregir
└─ Rellena los "huecos" de frecuencia
```

### F. Troubleshooting (Solución de Problemas)

```
PROBLEMA: Audio muy bajo
├─ Causas posibles:
│  ├─ Input Gain muy bajo
│  ├─ Master Volume muy bajo
│  └─ Micrófono inactivo
└─ Solución:
   ├─ Aumentar Input Gain a -6 dB
   ├─ Aumentar Master Volume a 0 dB
   └─ Verificar dispositivo de entrada

PROBLEMA: Clipping rojo constante
├─ Causas posibles:
│  ├─ Input Gain demasiado alto
│  ├─ Master Volume demasiado alto
│  └─ Sonido demasiado fuerte en micrófono
└─ Solución:
   ├─ Reducir Input Gain a -12 dB
   ├─ Reducir Master Volume a -6 dB
   └─ Alejar el micrófono

PROBLEMA: Sonido distorsionado
├─ Causas posibles:
│  ├─ Clipping en salida
│  ├─ Compresión excesiva
│  └─ EQ Boost demasiado alto
└─ Solución:
   ├─ Reducir Master Volume
   ├─ Reducir Threshold del compresor
   └─ Reducir EQ Boosts a máximo +6 dB

PROBLEMA: Sonido apagado / sordo
├─ Causas posibles:
│  ├─ EQ muy atenuado en agudos
│  ├─ Micrófono de baja calidad
│  └─ Compresión excesiva
└─ Solución:
   ├─ Aumentar Treble en EQ
   ├─ Usar Treble en EQ Gráfico
   └─ Reducir Attack de compresión

PROBLEMA: Volumen inconsistente
├─ Causas posibles:
│  ├─ Threshold del compresor demasiado alto
│  ├─ Release muy rápido
│  └─ Dinámicos del micrófono altos
└─ Solución:
   ├─ Reducir Threshold a -18 dB
   ├─ Aumentar Release a 100-150 ms
   └─ Aumentar Ratio a 4:1 o 5:1
```

---

## 7️⃣ ESPECIFICACIONES TÉCNICAS

### Hardware Requerido

```
MÍNIMO:
├─ Procesador: Dual Core 2.0 GHz
├─ RAM: 2 GB
├─ Conexión: Micrófono 3.5 mm o USB
└─ Navegador: Chrome 70+ / Firefox 75+

RECOMENDADO:
├─ Procesador: Quad Core 2.4 GHz+
├─ RAM: 4 GB+
├─ Conexión: Interfaz de audio USB profesional
└─ Navegador: Versión actual de cualquier navegador moderno
```

### Especificaciones de Audio

```
CAPTURA:
├─ Frecuencia de muestreo: 48 kHz (automático)
├─ Profundidad de bits: 32 bits float
├─ Latencia típica: 10-20 ms
└─ Buffer size: 4096 muestras

PROCESAMIENTO:
├─ FFT Size: 2048 puntos
├─ Resolución frecuencial: ~23 Hz por bin
├─ Tasa de actualización: 60 FPS
└─ Precisión: 32 bits float (máxima)

SALIDA:
├─ Frecuencia de muestreo: Igual a entrada
├─ Profundidad de bits: 32 bits float
├─ Rango dinámico: > 120 dB
└─ Respuesta en frecuencia: 20 Hz - 20 kHz ± 3 dB
```

### Navegadores Soportados

```
CHROME/CHROMIUM:
├─ Versión: 70+
├─ Soporte Web Audio API: ✅ Completo
├─ Performance: Excelente
└─ Recomendado: SÍ

FIREFOX:
├─ Versión: 75+
├─ Soporte Web Audio API: ✅ Completo
├─ Performance: Muy bueno
└─ Recomendado: SÍ

SAFARI:
├─ Versión: 14+
├─ Soporte Web Audio API: ✅ Completo (con webkit)
├─ Performance: Bueno
└─ Recomendado: SÍ (macOS/iOS)

EDGE:
├─ Versión: 79+
├─ Soporte Web Audio API: ✅ Completo
├─ Performance: Excelente
└─ Recomendado: SÍ
```

### Permisos Requeridos

```
MICRÓFONO (Obligatorio):
└─ Necesario para capturar audio

ALMACENAMIENTO LOCAL (Opcional):
└─ Para guardar presets personalizados (futura implementación)

NO REQUIERE:
├─ Acceso a cámara
├─ Conexión de red (totalmente local)
├─ Datos personales
└─ Información de ubicación
```

---

## 📝 NOTAS FINALES

### Características Futuras Planeadas

- ✨ Guardado de presets personalizados
- 📊 Exportación de datos de análisis
- 🎚️ Automatización de parámetros (LFO)
- 🔊 Varias cadenas de procesamiento
- 📱 Versión móvil con interfaz táctil optimizada
- 🎙️ Integración con streaming (OBS, etc.)
- 💾 Grabación de audio procesado

### Limitaciones Conocidas

```
1. La latencia varía según el navegador (10-50 ms típico)
2. El máximo de dispositivos de audio depende del SO
3. Solo mono o estéreo (no surround)
4. Web Audio API no permite acceso a hardware en tiempo real
5. Algunos navegadores pueden tener limitaciones en FFT
```

### Support y Documentación

```
Para problemas técnicos:
1. Verifica que usas un navegador soportado
2. Prueba con otro dispositivo de entrada
3. Cierra otras aplicaciones de audio
4. Recarga la página si hay comportamientos extraños
5. Consulta la sección Troubleshooting
```

---

**RADIO PRO v1.0** | Procesador de Audio Profesional en Tiempo Real
Desarrollado con Web Audio API | Compatible con navegadores modernos

¡Disfruta del procesamiento de audio profesional directamente en tu navegador! 🎛️✨
