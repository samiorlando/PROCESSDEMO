# 🎛️ RADIO PRO - Procesador de Audio Profesional en Tiempo Real

![Version](https://img.shields.io/badge/version-1.0-blue)
![License](https://img.shields.io/badge/license-MIT-green)
![Platform](https://img.shields.io/badge/platform-Web-orange)

---

## 📌 ¿QUÉ ES RADIO PRO?

**RADIO PRO** es una aplicación web profesional de procesamiento de audio en tiempo real, diseñada como un procesador de broadcast estilo radio profesional (inspirado en Optimod-style processors). 

Proporciona **DSP de studio-quality** directamente en tu navegador, sin necesidad de instalar software ni pagar suscripciones.

### ✨ Características Principales

✅ **Interfaz Profesional**: Consola de audio tipo radio con tema oscuro  
✅ **Procesamiento en Tiempo Real**: Latencia mínima (<20ms típico)  
✅ **Ecualizadores Avanzados**: Paramétrico 5-bandas + Gráfico 10-bandas  
✅ **Compresores Multibanda**: 5 compresores independientes + Dual-band limiter  
✅ **Analizador de Espectro**: FFT en vivo para visualización  
✅ **Medidores Profesionales**: Input/Output level, clipping detection  
✅ **4 Presets Profesionales**: Radio FM, Voz Clara, Música, Ultra Bass  
✅ **100% Web API**: Usa Web Audio API, sin plugins  
✅ **Completamente Local**: Sin conexión a internet requerida  

---

## 📂 CONTENIDO DEL PAQUETE

```
📦 RADIO PRO Package
├── 📄 audio-processor.html          (Aplicación web principal)
├── 📖 README.md                     (Este archivo)
├── 🚀 QUICK_START.md                (Guía de 5 minutos - EMPEZAR AQUÍ)
├── 📚 RADIO_PRO_DOCUMENTATION.md    (Documentación técnica completa)
├── ⚙️ ADVANCED_PRESETS.md           (Configuraciones especializadas)
└── 📋 Este README
```

---

## 🚀 INICIO RÁPIDO

### 1. Abrir la Aplicación
```bash
# Simplemente abre el archivo HTML en tu navegador:
Doble clic en: audio-processor.html
```

### 2. Permitir Micrófono
```
El navegador te pedirá permiso
Haz clic en "Permitir" para continuar
```

### 3. Encender el Procesador
```
Panel Izquierdo → Botón "POWER ON"
(Cambiará a color verde cuando esté activo)
```

### 4. Seleccionar Preset
```
Panel Izquierdo → Elige uno de estos:
├─ "Radio FM" para voz clara
├─ "Voz Clara" para máxima inteligibilidad
├─ "Música" para sonido musical
└─ "Ultra Bass" para bajos profundos
```

### 5. Ajustar Volumen
```
Observa los medidores "Input Level" y "Output Level"
Ambos deben estar en AMARILLO (óptimo)
```

✅ **¡Listo!** Tu audio está siendo procesado profesionalmente.

Para guía detallada → Ver `QUICK_START.md`

---

## 🎯 CASOS DE USO

### 📻 Radio Profesional
- Transmisión de voz clara y potente
- Sonido consistente tipo broadcast
- Control de dinámicos automático

### 🎤 Podcasting
- Voz clara y definida
- Eliminación de ruido de fondo
- Sonido profesional sin equipamiento costoso

### 🎵 Música en Vivo
- Streaming de conciertos
- Retransmisión de eventos musicales
- Mezcla rápida de multiples fuentes

### 📢 Conferencias/Webinars
- Voz clara y consistente
- Audio profesional en tiempo real
- Monitoreo de niveles

### 🎙️ Producción de Audio
- Masterización rápida
- Prueba de mezclas
- Referencia de audio profesional

---

## 🎛️ ARQUITECTURA DEL SISTEMA

### Módulos Principales

```
INPUT → GAIN CONTROL → ANALYSER
           ↓
    ┌──────────────────────────────┐
    │  DSP PROCESSING CHAIN         │
    ├──────────────────────────────┤
    │ ├─ EQ Paramétrico (5-bandas) │
    │ ├─ Multiband Compressor      │
    │ ├─ Graphic EQ (10-bandas)    │
    │ ├─ Dual Band Limiter         │
    │ ├─ Bass EQ (Low Shelf)       │
    │ └─ Stereo Enhancer           │
    └──────────────────────────────┘
           ↓
    MASTER GAIN → ANALYSER → OUTPUT
```

### Flujo de Audio

```
Micrófono
   ↓
Input Gain Node (-24 a +24 dB)
   ↓
Analyser (Input Metering)
   ↓
[5x DSP Processors]
   ↓
Master Volume Node (-40 a +6 dB)
   ↓
Analyser (Output Metering)
   ↓
Audio Context Destination (Altavoces/Auriculares)
```

---

## 📊 ESPECIFICACIONES TÉCNICAS

### Audio
```
Frecuencia de Muestreo: 48 kHz (automático)
Profundidad de Bits: 32 bits float
Latencia Típica: 10-20 ms
Buffer Size: 4096 muestras
Resolución FFT: 2048 puntos (~23 Hz por bin)
```

### Navegadores Soportados
```
✅ Chrome/Chromium 70+
✅ Firefox 75+
✅ Safari 14+
✅ Edge 79+
✅ Opera 57+
```

### Requisitos del Sistema
```
Mínimo:
├─ Procesador: Dual Core 2.0 GHz
├─ RAM: 2 GB
└─ Navegador moderno

Recomendado:
├─ Procesador: Quad Core 2.4 GHz+
├─ RAM: 4 GB+
└─ Navegador actualizado
```

---

## 🎚️ CONTROLES PRINCIPALES

### Sección INPUT
```
🎤 Audio Input          | Selector de dispositivo de entrada
📊 Input Gain           | -24 dB a +24 dB (amplificación/atenuación)
📈 Input Level Meter    | Visualización de nivel en tiempo real
🔴 Clipping Detector    | LED rojo intermitente si hay clipping
```

### Sección OUTPUT
```
🔊 Output Device        | Selector de dispositivo de salida
🎚️ Master Volume        | -40 dB a +6 dB (volumen principal)
📈 Output Level Meter   | Visualización de nivel procesado
🔴 Output Clipping      | LED rojo intermitente si hay clipping
```

### Procesamiento DSP

**EQ Paramétrico (5 Bandas)**
```
Sub-Bass   (20Hz-60Hz)      | Control de bajos profundos
Bass       (60Hz-250Hz)     | Control de bajos
Mid        (250Hz-2kHz)     | Control de cuerpo
High-Mid   (2kHz-6kHz)      | Control de presencia
Treble     (6kHz-16kHz)     | Control de agudos/aire
```

**Compresor Multibanda**
```
5 compresores independientes, uno por banda:
├─ Threshold   | Nivel en el que comienza compresión (-60 a 0 dB)
├─ Ratio       | Relación de compresión (1:1 a 8:1)
├─ Attack      | Tiempo de reacción (1-100 ms)
├─ Release     | Tiempo de recuperación (10-500 ms)
└─ Makeup Gain | Ganancia de compensación
```

**EQ Gráfico (10 Bandas)**
```
20Hz / 50Hz / 100Hz / 250Hz / 500Hz / 1kHz / 2kHz / 4kHz / 8kHz / 16kHz
Rango: -12 dB a +12 dB (ajuste fino por frecuencia)
```

**Dual Band Compressor/Limiter**
```
LOW Band  (20Hz-500Hz)  | Control independiente de bajos
HIGH Band (500Hz-20kHz) | Control independiente de agudos
```

---

## 💻 TECNOLOGÍA

### Backend Audio
```
Web Audio API
├─ AudioContext
├─ GainNode
├─ AnalyserNode
├─ MediaStreamSource
└─ Destination
```

### Frontend
```
HTML5
├─ Canvas para gráficos (Spectrum, EQ Curve)
├─ Input ranges (sliders)
└─ Select elements (device selection)

CSS3
├─ Grid layout
├─ Flexbox
├─ Gradientes
├─ Animaciones
└─ Media queries (responsive)

JavaScript (Vanilla)
├─ Web Audio API integration
├─ Real-time FFT visualization
├─ UI event handling
├─ State management
└─ Audio device enumeration
```

---

## 🎓 DOCUMENTACIÓN

### Para Comenzar
📖 **`QUICK_START.md`** - Lee esto primero (5 minutos)
- Instrucciones paso a paso
- Solución rápida de problemas
- Configuraciones recomendadas
- Monitoreo en tiempo real

### Documentación Completa
📚 **`RADIO_PRO_DOCUMENTATION.md`** - Referencia técnica (50 páginas)
- Descripción detallada de cada módulo
- Arquitectura del sistema
- Guía de uso completa
- Presets predefinidos
- Consejos profesionales
- Troubleshooting avanzado
- Especificaciones técnicas

### Configuraciones Avanzadas
⚙️ **`ADVANCED_PRESETS.md`** - Para usuarios avanzados
- Radio FM profesional
- Podcast optimizado
- Música en vivo
- Masterización de voces
- Electrónica/EDM
- Voz cantada
- Tabla comparativa de presets
- Principios de procesamiento

---

## 🎯 WORKFLOW RECOMENDADO

### Para Principiantes (10 minutos)
```
1. Abre audio-processor.html
2. Lee QUICK_START.md (5 min)
3. Sigue los 5 pasos iniciales
4. Experimenta con cada preset
5. Observa cómo cambia el sonido
```

### Para Usuarios Intermedios (30 minutos)
```
1. Aplica preset base
2. Lee sección relevante en RADIO_PRO_DOCUMENTATION.md
3. Ajusta EQ paramétrico para tu caso de uso
4. Configura compresor multibanda
5. Afina volúmenes finales
6. Guarda configuración (mental o anotado)
```

### Para Usuarios Avanzados (1+ horas)
```
1. Estudia ADVANCED_PRESETS.md completamente
2. Lee sección de Arquitectura en RADIO_PRO_DOCUMENTATION.md
3. Crea presets personalizados para casos específicos
4. Experimenta con mezclas de parámetros
5. Desarrolla workflow personalizado
6. Documenta tus hallazgos
```

---

## 🛠️ CARACTERÍSTICAS TÉCNICAS

### Medición y Análisis
```
✅ Medidores de nivel RMS en dB
✅ Detección de clipping en tiempo real
✅ Analizador de espectro FFT
✅ Visualización de curva EQ
✅ Indicadores LED de estado
✅ Visualización de frecuencias
```

### Procesamiento
```
✅ Compresión multibanda (5 bandas)
✅ Ecualización paramétrica (5 bandas)
✅ Ecualización gráfica (10 bandas)
✅ Limitador de salida
✅ Control de ganancia en cada etapa
✅ Protección contra clipping
```

### Controles Intuitivos
```
✅ Sliders tipo radio profesional
✅ Knobs para ajuste fino
✅ Selector de dispositivos
✅ LEDs de estado
✅ Medidores visuales
✅ Presets con un clic
```

---

## ⚙️ CONFIGURACIÓN INICIAL

### Requisitos Previos
```
✅ Navegador web moderno (Chrome, Firefox, Safari, Edge)
✅ Micrófono o entrada de audio
✅ Altavoces o auriculares para monitoreo
✅ Permiso de acceso a micrófono en navegador
```

### Instalación
```
1. Descarga los archivos
2. Guarda audio-processor.html en tu computadora
3. Doble clic en el archivo
4. Se abre automáticamente en tu navegador
5. El navegador pide permiso de micrófono
6. Haz clic en "Permitir"
7. ¡Listo!
```

### Primera Ejecución
```
1. Encender Power
2. Seleccionar dispositivo de entrada
3. Ajustar Input Gain
4. Seleccionar preset
5. Ajustar Master Volume
6. Verificar niveles
7. Comenzar a usar
```

---

## 📈 CASOS DE USO REALES

### Caso 1: Podcast de Voz Hablada
```
Objetivo: Voz clara, profesional, sin ruido
Preset Base: "Voz Clara"
Ajustes:
├─ Input Gain: -10 dB
├─ Presencia: +2 dB (High-Mid)
├─ Master Volume: -8 dB
└─ Resultado: Voz inteligible, limpia, profesional
```

### Caso 2: Transmisión de Radio
```
Objetivo: Voz potente, consistente, tipo comercial
Preset Base: "Radio FM"
Ajustes:
├─ Input Gain: -12 dB
├─ Bass: +2 dB
├─ Compresión: Threshold -20 dB
└─ Resultado: Voz tipo radio, sonido broadcast
```

### Caso 3: Música en Vivo
```
Objetivo: Sonido dinámico, musical, potente
Preset Base: "Música"
Ajustes:
├─ Input Gain: -6 dB
├─ Bass Boost: +4 dB
├─ Compresor suave
└─ Resultado: Música balanceada, potente, musical
```

### Caso 4: Bajos Profundos
```
Objetivo: Bajos enormes para electrónica
Preset Base: "Ultra Bass"
Ajustes:
├─ Input Gain: -4 dB
├─ Bass Boost: +12 dB
├─ Compresor agresivo en bajos
└─ ⚠️ Master Volume: -10 dB (crítico)
```

---

## 🎓 APRENDIZAJE

### Conceptos Básicos
```
1. Ecualización (EQ): Cambiar balance de frecuencias
2. Compresión: Reducir dinámicos, hacer sonido más consistente
3. Ganancia (Gain): Amplificar o atenuar volumen
4. Clipping: Distorsión por volumen excesivo
5. Threshold: Nivel en el que comienza la compresión
```

### Técnicas Profesionales
```
1. Gain Staging: Niveles correctos en cada etapa
2. Compresión Transparente: Invisible pero efectiva
3. Ecualización Sustractiva: Atenúar en lugar de aumentar
4. Limitador: Barrera final contra clipping
5. Multiband Processing: Procesar diferentes frecuencias diferente
```

### Mejores Prácticas
```
1. Menos es más: Cambios pequeños de ±1-2 dB
2. Escuchar en descansos: Fatiga auditiva afecta juicio
3. Comparar con referencia: Tener track profesional similar
4. Evitar clipping: Una instancia lo arruina todo
5. Documentar: Guardar configuraciones que funcionan
```

---

## 📊 ANÁLISIS Y MONITOREO

### Medidores de Nivel
```
Input Level
├─ Verde (< -20 dB): Demasiado bajo
├─ Amarillo (-20 a -1 dB): Óptimo ✅
└─ Rojo (> -1 dB): Clipping, reducir

Output Level
├─ Verde (< -20 dB): Demasiado bajo
├─ Amarillo (-12 a -8 dB): Óptimo ✅
└─ Rojo (> -2 dB): Reducir Master Volume
```

### Analizador de Espectro
```
Visualización en tiempo real de frecuencias
├─ Barras: Energía en cada frecuencia
├─ Línea: Envelope del espectro
├─ Grid: Referencias de frecuencias
└─ Colores: Gradiente visual

Qué buscar:
├─ Distribución equilibrada (no picos agresivos)
├─ Energía en bajos, medios y agudos
├─ Sin gaps significativos
└─ Movimiento consistente según entrada
```

---

## 🎁 BONUS FEATURES

### Presets Predefinidos
```
🎙️ Radio FM       | Voz clara tipo radio comercial
📢 Voz Clara      | Máxima inteligibilidad
🎵 Música         | Sonido balanceado y musical
🔊 Ultra Bass     | Bajos profundos y controlados
```

### Características Profesionales
```
✅ Medidores de nivel profesionales
✅ Detección de clipping en tiempo real
✅ Analizador de espectro FFT vivo
✅ Múltiples dispositivos de entrada/salida
✅ Interfaz tipo consola radio
✅ Indicadores LED de estado
✅ Tema oscuro para estudio
```

---

## 🔒 PRIVACIDAD Y SEGURIDAD

```
✅ Completamente local (no se envía datos a internet)
✅ No requiere cuenta ni registro
✅ No recolecta datos personales
✅ No requiere conexión a servidores
✅ HTML/CSS/JS puro, sin dependencias externas
✅ Puedes usar offline después de cargar
```

---

## 🚀 FUTURO ROADMAP

```
Versión 1.1:
├─ Guardado de presets personalizados
├─ Exportación de audio procesado
└─ Interface táctil para móvil

Versión 1.2:
├─ Automatización de parámetros (LFO)
├─ Múltiples cadenas de procesamiento
└─ Grabación de sesiones

Versión 2.0:
├─ Integración con OBS/streaming
├─ Plugin para DAWs
├─ Análisis avanzado
└─ Configuraciones personalizadas en la nube
```

---

## 💬 SOPORTE

### Solución Rápida de Problemas
```
Problema: No escucho nada
└─ Verifica: Power ON, dispositivo correcto, volumen

Problema: Clipping rojo
└─ Solución: Reduce Input Gain o Master Volume

Problema: Sonido distorsionado
└─ Solución: Reduce niveles en 5-10 dB

Problema: Sonido apagado
└─ Solución: Aumenta Treble en EQ Paramétrico

Para más ayuda: Ver sección Troubleshooting en documentación
```

---

## 📝 LICENCIA

Este proyecto se proporciona como está, con fines educativos y profesionales.

```
Libre para usar, modificar y distribuir
Reconocimiento apreciado pero no requerido
Sin garantía de ningún tipo
```

---

## 📞 CONTACTO Y CONTRIBUCIONES

```
¿Ideas para mejorar?
├─ Prueba los controles y experimenta
├─ Documenta lo que funciona
└─ Comparte tus hallazgos

¿Encontraste un bug?
├─ Describe qué pasó
├─ Qué navegador usabas
└─ Qué pasos para reproducir

¿Quieres contribuir?
├─ Mejora la interfaz
├─ Agrega nuevos procesadores
├─ Mejora la documentación
└─ Crea nuevos presets
```

---

## 🎉 ¡COMIENZA AHORA!

1. **Abre**: `audio-processor.html`
2. **Lee**: `QUICK_START.md` (5 minutos)
3. **Experimenta**: Con los presets y controles
4. **Domina**: Estudiando la documentación completa

**¡Tu procesador de audio profesional de broadcast está listo!** 🎛️✨

---

## 📚 REFERENCIAS

```
Web Audio API Specification:
└─ https://www.w3.org/TR/webaudio/

Professional Audio Processing:
├─ Broadcast Standards
├─ Radio Broadcasting Techniques
└─ Audio Engineering Practices

Compresión y Dinámica:
├─ Threshold, Ratio, Attack, Release
├─ Makeup Gain, Look-ahead
└─ Multiband Compression

Ecualización:
├─ Shelving Filters
├─ Peak Filters
├─ Parametric EQ
└─ Graphic EQ
```

---

**RADIO PRO v1.0**
*Procesador de Audio Profesional en Tiempo Real*
*Inspirado en Broadcast Processors tipo Optimod*

**Creado con ❤️ para audiofilos y profesionales**

¡Disfruta del procesamiento de audio profesional! 🎛️✨

---

*Última actualización: 2024 | Versión 1.0 | Web Audio API v1.2*
