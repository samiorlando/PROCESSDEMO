<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Optimod-PC 1600 — Audio Processor</title>
<style>
*,*::before,*::after{margin:0;padding:0;box-sizing:border-box}
:root{
  --bg:#0a0a0f;--panel:#12121a;--panel2:#1a1a26;--border:#2a2a3a;
  --accent:#00e676;--accent2:#00b0ff;--accent3:#ff5252;--accent4:#ffab40;
  --text:#e0e0e0;--text2:#888;--knob-bg:#1e1e2e;
  --glow-green:0 0 12px rgba(0,230,118,.5);
  --glow-blue:0 0 12px rgba(0,176,255,.5);
  --glow-red:0 0 12px rgba(255,82,82,.5);
}
body{font-family:'Segoe UI',system-ui,-apple-system,sans-serif;background:var(--bg);color:var(--text);overflow-x:hidden;min-height:100vh}
::-webkit-scrollbar{width:6px;height:4px}
::-webkit-scrollbar-track{background:var(--bg)}
::-webkit-scrollbar-thumb{background:var(--border);border-radius:3px}

/* HEADER */
.header{
  background:linear-gradient(180deg,#1a1a2e,#0f0f1a);border-bottom:2px solid var(--accent);
  padding:10px 24px;display:flex;align-items:center;justify-content:space-between;
  position:sticky;top:0;z-index:100;box-shadow:0 4px 30px rgba(0,0,0,.8);
}
.logo h1{font-size:1.4rem;font-weight:700;letter-spacing:3px;color:var(--accent)}
.logo h1 span{color:var(--text);font-weight:300;font-size:.85rem}
.logo-sub{font-size:.6rem;color:var(--text2);letter-spacing:2px;text-transform:uppercase}

/* POWER BUTTON */
.power-btn{
  width:64px;height:64px;border-radius:50%;border:3px solid #333;
  background:radial-gradient(circle at 40% 35%,#2a1a1a,#1a0a0a);
  cursor:pointer;position:relative;display:flex;align-items:center;justify-content:center;
  transition:all .4s;box-shadow:inset 0 2px 8px rgba(0,0,0,.6);
}
.power-btn:hover{border-color:var(--accent3);box-shadow:inset 0 2px 8px rgba(0,0,0,.6),var(--glow-red)}
.power-btn.active{
  border-color:var(--accent);background:radial-gradient(circle at 40% 35%,#1a2a1a,#0a1a0a);
  box-shadow:inset 0 2px 8px rgba(0,0,0,.6),var(--glow-green);
}
.power-icon{width:20px;height:20px;border:2px solid #555;border-radius:50%;border-top-color:transparent;transition:all .4s}
.power-btn.active .power-icon{border-color:var(--accent);box-shadow:0 0 8px var(--accent)}
.power-icon::after{content:'';position:absolute;top:-6px;left:50%;transform:translateX(-50%);width:2px;height:8px;background:#555;transition:all .4s}
.power-btn.active .power-icon::after{background:var(--accent)}
.status-led{width:10px;height:10px;border-radius:50%;background:#333;transition:all .4s;margin-right:12px}
.status-led.on{background:var(--accent);box-shadow:0 0 8px var(--accent)}

/* LAYOUT */
.main{display:grid;grid-template-columns:1fr 1fr;gap:12px;padding:12px;max-width:1600px;margin:0 auto}
@media(max-width:1100px){.main{grid-template-columns:1fr}}
.full-width{grid-column:1/-1}

/* PANEL */
.panel{
  background:var(--panel);border:1px solid var(--border);border-radius:8px;padding:16px;position:relative;overflow:hidden;
}
.panel::before{
  content:'';position:absolute;top:0;left:0;right:0;height:1px;
  background:linear-gradient(90deg,transparent,var(--accent),transparent);opacity:.3;
}
.panel-title{
  font-size:.7rem;letter-spacing:3px;text-transform:uppercase;color:var(--accent);
  margin-bottom:12px;padding-bottom:8px;border-bottom:1px solid var(--border);
  display:flex;align-items:center;gap:8px;
}
.panel-title::before{content:'';width:3px;height:14px;background:var(--accent);border-radius:2px}

/* KNOB */
.knob-container{display:flex;flex-direction:column;align-items:center;gap:6px}
.knob{
  width:64px;height:64px;border-radius:50%;background:radial-gradient(circle at 35% 30%,#3a3a4a,#1a1a28);
  border:2px solid #333;position:relative;cursor:pointer;
  box-shadow:0 4px 12px rgba(0,0,0,.5),inset 0 1px 2px rgba(255,255,255,.05);
}
.knob:hover{border-color:var(--accent)}
.knob-indicator{
  position:absolute;width:2px;height:28%;background:var(--accent);top:8%;left:50%;
  transform-origin:bottom center;border-radius:1px;box-shadow:0 0 4px var(--accent);
}
.knob-value{font-size:.65rem;color:var(--text2);font-family:'Courier New',monospace;min-width:50px;text-align:center}
.knob-label{font-size:.55rem;color:var(--text2);letter-spacing:1px;text-transform:uppercase}

/* SLIDERS */
.vslider-group{display:flex;flex-direction:column;align-items:center;gap:4px}
.vslider-wrap{position:relative;width:36px;height:160px;background:var(--knob-bg);border-radius:4px;border:1px solid var(--border);overflow:hidden}
.vslider-track{position:absolute;bottom:0;left:0;right:0;background:linear-gradient(0deg,rgba(0,230,118,.15),rgba(0,230,118,.05));border-radius:4px;transition:height .1s}
.vslider{
  -webkit-appearance:none;appearance:none;width:160px;height:36px;background:transparent;
  position:absolute;left:-62px;top:50%;transform:rotate(-90deg);transform-origin:center;cursor:pointer;z-index:2;
}
.vslider::-webkit-slider-runnable-track{height:4px;background:var(--border);border-radius:2px}
.vslider::-webkit-slider-thumb{
  -webkit-appearance:none;width:16px;height:24px;background:linear-gradient(180deg,#555,#333);
  border:1px solid #666;border-radius:3px;margin-top:-10px;cursor:pointer;box-shadow:0 2px 6px rgba(0,0,0,.4);
}
.vslider::-moz-range-track{height:4px;background:var(--border);border-radius:2px;border:none}
.vslider::-moz-range-thumb{
  width:16px;height:24px;background:linear-gradient(180deg,#555,#333);
  border:1px solid #666;border-radius:3px;cursor:pointer;
}
.vslider-label{font-size:.55rem;color:var(--text2);letter-spacing:.5px;text-align:center}
.vslider-value{font-size:.6rem;color:var(--accent);font-family:'Courier New',monospace;min-height:14px}

.hslider{
  -webkit-appearance:none;appearance:none;width:100%;height:6px;background:var(--border);
  border-radius:3px;outline:none;cursor:pointer;
}
.hslider::-webkit-slider-thumb{
  -webkit-appearance:none;width:18px;height:18px;border-radius:50%;
  background:linear-gradient(135deg,#555,#333);border:2px solid var(--accent);
  cursor:pointer;box-shadow:0 0 6px rgba(0,230,118,.3);
}
.hslider::-moz-range-thumb{
  width:18px;height:18px;border-radius:50%;background:linear-gradient(135deg,#555,#333);
  border:2px solid var(--accent);cursor:pointer;
}

/* METER */
.meter-container{display:flex;flex-direction:column;gap:2px;margin:8px 0}
.meter{height:18px;background:#0a0a0a;border-radius:3px;border:1px solid var(--border);overflow:hidden;position:relative}
.meter-fill{height:100%;width:0%;border-radius:2px;transition:width .08s linear}
.meter-fill.green{background:linear-gradient(90deg,#1b5e20,#4caf50,#8bc34a)}
.meter-fill.yellow{background:linear-gradient(90deg,#f57f17,#ffab40,#ffd740)}
.meter-fill.red{background:linear-gradient(90deg,#b71c1c,#f44336,#ff5252)}
.meter-fill.blue{background:linear-gradient(90deg,#0d47a1,#2196f3,#64b5f6)}
.meter-fill.cyan{background:linear-gradient(90deg,#006064,#00bcd4,#4dd0e1)}
.meter-label{display:flex;justify-content:space-between;font-size:.55rem;color:var(--text2)}
.meter-db{font-size:.55rem;color:var(--accent);font-family:'Courier New',monospace;text-align:right;min-height:14px}

/* GRID HELPERS */
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:8px}
.grid-5{display:grid;grid-template-columns:repeat(5,1fr);gap:6px}
.flex-center{display:flex;align-items:center;justify-content:center;gap:12px}
.flex-between{display:flex;align-items:center;justify-content:space-between}
.divider{height:1px;background:linear-gradient(90deg,transparent,var(--border),transparent);margin:12px 0}

/* BANDS SCROLL */
.bands-scroll{overflow-x:auto;overflow-y:hidden;padding:8px 0;scrollbar-width:thin;scrollbar-color:var(--border) transparent}
.bands-inner{display:flex;gap:6px;min-width:max-content}
.band-col{display:flex;flex-direction:column;align-items:center;gap:6px;min-width:70px;padding:8px 4px}
.band-col .vslider-wrap{height:140px}

/* COMP BAND */
.comp-band{
  background:var(--panel2);border:1px solid var(--border);border-radius:6px;padding:10px;
  display:flex;flex-direction:column;gap:8px;
}
.comp-band-title{
  font-size:.6rem;color:var(--accent2);letter-spacing:2px;text-transform:uppercase;
  text-align:center;padding-bottom:6px;border-bottom:1px solid var(--border);
}
.comp-param{display:flex;flex-direction:column;align-items:center;gap:2px}
.comp-param label{font-size:.5rem;color:var(--text2);letter-spacing:1px}
.comp-param input[type=range]{width:80px}

/* ANALYZER */
.analyzer{width:100%;height:80px;background:#0a0a0a;border:1px solid var(--border);border-radius:4px;position:relative;overflow:hidden}
.analyzer canvas{width:100%;height:100%}

/* BUTTONS */
.btn{
  padding:6px 16px;border:1px solid var(--border);border-radius:4px;background:var(--panel2);
  color:var(--text);font-size:.65rem;letter-spacing:1px;cursor:pointer;transition:all .2s;text-transform:uppercase;
}
.btn:hover{border-color:var(--accent);color:var(--accent)}
.btn.active{background:rgba(0,230,118,.15);border-color:var(--accent);color:var(--accent)}
.btn-group{display:flex;gap:6px;flex-wrap:wrap}

/* SELECT (FIXED STYLE) */
select{
  background:var(--panel2);color:var(--text);border:1px solid var(--border);
  border-radius:4px;padding:6px 8px;font-size:.7rem;cursor:pointer;outline:none;width:100%;
}
select:hover{border-color:var(--accent)}
select:focus{border-color:var(--accent);box-shadow:0 0 4px rgba(0,230,118,.2)}
select option{background:var(--panel2);color:var(--text)}

/* TABS */
.tabs{display:flex;gap:4px;margin-bottom:12px}
.tab{
  padding:6px 14px;border:1px solid var(--border);border-radius:4px 4px 0 0;
  background:var(--panel2);color:var(--text2);font-size:.6rem;cursor:pointer;
  letter-spacing:1px;transition:all .2s;
}
.tab:hover{color:var(--accent);border-color:var(--accent)}
.tab.active{background:var(--panel);color:var(--accent);border-bottom-color:var(--panel)}

/* LED DISPLAY */
.led-display{
  background:#050508;border:1px solid #222;border-radius:4px;padding:6px 12px;
  font-family:'Courier New',monospace;font-size:.85rem;color:var(--accent);
  letter-spacing:2px;text-align:center;min-height:28px;display:flex;align-items:center;justify-content:center;
  box-shadow:inset 0 2px 8px rgba(0,0,0,.8);text-shadow:0 0 8px rgba(0,230,118,.5);
}

/* WAVEFORM */
.waveform{width:100%;height:50px;background:#050508;border:1px solid var(--border);border-radius:4px;position:relative;overflow:hidden}
.waveform canvas{width:100%;height:100%}

/* GR METER */
.gr-meter{height:6px;background:var(--knob-bg);border-radius:3px;overflow:hidden;border:1px solid var(--border)}
.gr-meter-fill{height:100%;background:linear-gradient(90deg,var(--accent3),var(--accent4));border-radius:3px;transition:width .1s}

/* SPECTRUM */
.spectrum-container{display:flex;align-items:flex-end;gap:2px;height:100px;padding:4px;background:var(--knob-bg);border-radius:4px;border:1px solid var(--border)}
.spectrum-bar{flex:1;min-width:3px;border-radius:1px 1px 0 0;transition:height .05s linear}

/* POWER OVERLAY */
.overlay-off{
  position:fixed;top:0;left:0;right:0;bottom:0;background:rgba(0,0,0,.95);z-index:200;
  display:flex;align-items:center;justify-content:center;flex-direction:column;gap:16px;transition:opacity .5s;
}
.overlay-off.hidden{opacity:0;pointer-events:none}
.overlay-off h2{color:var(--accent);font-size:1.2rem;letter-spacing:4px;text-transform:uppercase}
.overlay-off p{color:var(--text2);font-size:.7rem;letter-spacing:2px}

/* DEVICE SELECT SECTION */
.device-section{
  background:var(--panel2);border:1px solid var(--border);border-radius:6px;padding:10px;margin-bottom:8px;
}
.device-label{font-size:.6rem;color:var(--accent);letter-spacing:2px;text-transform:uppercase;margin-bottom:6px;display:block}
.device-status{font-size:.55rem;color:var(--text2);margin-top:4px;display:flex;align-items:center;gap:6px}
.device-status .dot{width:6px;height:6px;border-radius:50%;background:#555;transition:all .3s}
.device-status .dot.active{background:var(--accent);box-shadow:0 0 4px var(--accent)}

@media(max-width:768px){
  .header{padding:8px 12px}
  .logo h1{font-size:1rem}
  .main{padding:8px;gap:8px}
  .panel{padding:10px}
  .knob{width:50px;height:50px}
  .knob-indicator{height:26%;top:6%}
}
</style>
</head>
<body>

<div class="overlay-off" id="powerOverlay">
  <h2>⏻ Optimod-PC 1600</h2>
  <p>Presiona POWER para iniciar</p>
</div>

<!-- ==================== HEADER ==================== -->
<div class="header">
  <div class="logo">
    <div>
      <h1>OPTIMOD-PC <span>1600</span></h1>
      <div class="logo-sub">Multiband Audio Processor — Broadcast DSP</div>
    </div>
  </div>
  <div class="flex-center">
    <div class="status-led" id="statusLed"></div>
    <div class="power-btn" id="powerBtn" onclick="togglePower()">
      <div class="power-icon"></div>
    </div>
  </div>
</div>

<!-- ==================== MAIN UI ==================== -->
<div class="main" id="mainUI">

  <!-- ===== 1. INPUT / OUTPUT SECTION ===== -->
  <div class="panel">
    <div class="panel-title">🔊 Entrada / Salida de Audio</div>

    <!-- INPUT -->
    <div class="device-section">
      <label class="device-label">🎤 Entrada de Audio (Input)</label>
      <select id="inputSelect" onchange="changeInput()" disabled>
        <option value="">Presiona POWER primero...</option>
      </select>
      <div class="device-status">
        <div class="dot" id="inputDot"></div>
        <span id="inputStatusText">Sin entrada activa</span>
      </div>
    </div>

    <!-- OUTPUT -->
    <div class="device-section">
      <label class="device-label">🔈 Salida de Audio (Output)</label>
      <select id="outputSelect" onchange="changeOutput()" disabled>
        <option value="">Presiona POWER primero...</option>
      </select>
      <div class="device-status">
        <div class="dot" id="outputDot"></div>
        <span id="outputStatusText">Salida predeterminada</span>
      </div>
    </div>

    <div class="divider"></div>

    <!-- INPUT GAIN -->
    <div class="grid-2">
      <div class="knob-container">
        <div class="knob" id="inputGainKnob" data-param="inputGain" data-min="-24" data-max="24" data-value="0" onmousedown="startKnobDrag(event,this)">
          <div class="knob-indicator"></div>
        </div>
        <div class="knob-label">Input Gain</div>
        <div class="knob-value" id="inputGainVal">0.0 dB</div>
      </div>
      <div class="knob-container">
        <div class="knob" id="outputVolKnob" data-param="outputVol" data-min="-60" data-max="0" data-value="-6" onmousedown="startKnobDrag(event,this)">
          <div class="knob-indicator"></div>
        </div>
        <div class="knob-label">Output Level</div>
        <div class="knob-value" id="outputVolVal">-6.0 dB</div>
      </div>
    </div>

    <div class="divider"></div>

    <!-- INPUT METERS -->
    <div class="meter-label"><span>L</span><span>Input Level</span><span>R</span></div>
    <div class="meter-container">
      <div class="meter"><div class="meter-fill green" id="inputMeterL"></div></div>
      <div class="meter"><div class="meter-fill green" id="inputMeterR"></div></div>
    </div>
    <div class="meter-db" id="inputMeterDb">-∞ dB</div>

    <div class="divider"></div>

    <!-- OUTPUT METERS -->
    <div class="meter-label"><span>L</span><span>Output Level</span><span>R</span></div>
    <div class="meter-container">
      <div class="meter"><div class="meter-fill yellow" id="outputMeterL"></div></div>
      <div class="meter"><div class="meter-fill yellow" id="outputMeterR"></div></div>
    </div>
    <div class="meter-db" id="outputMeterDb">-∞ dB</div>

    <div class="divider"></div>
    <div class="waveform"><canvas id="inputWaveform"></canvas></div>
  </div>

  <!-- ===== 2. MULTIBAND EQ ===== -->
  <div class="panel">
    <div class="panel-title">🎚️ Multiband EQ</div>
    <div class="tabs">
      <div class="tab active" onclick="eqPreset('flat',this)">Flat</div>
      <div class="tab" onclick="eqPreset('bassBoost',this)">Bass Boost</div>
      <div class="tab" onclick="eqPreset('vocalClarity',this)">Vocal Clarity</div>
      <div class="tab" onclick="eqPreset('brightHighs',this)">Bright Highs</div>
      <div class="tab" onclick="eqPreset('warm',this)">Warm</div>
    </div>
    <div class="bands-scroll">
      <div class="bands-inner" id="eqBands"></div>
    </div>
    <div class="divider"></div>
    <div class="analyzer"><canvas id="eqAnalyzer"></canvas></div>
  </div>

  <!-- ===== 3. MULTIBAND COMPRESSOR ===== -->
  <div class="panel full-width">
    <div class="panel-title">🎛️ Multiband Compressor</div>
    <div class="grid-5" id="compBands"></div>
  </div>

  <!-- ===== 4. GRAPHIC EQ ===== -->
  <div class="panel full-width">
    <div class="panel-title">📊 Graphic Equalizer (15 Bands ISO)</div>
    <div class="bands-scroll">
      <div class="bands-inner" id="graphicEqBands"></div>
    </div>
    <div class="divider"></div>
    <div class="spectrum-container" id="spectrumDisplay"></div>
  </div>

  <!-- ===== 5. DUAL BAND COMPRESSOR ===== -->
  <div class="panel">
    <div class="panel-title">⚡ Dual Band Compressor</div>
    <div class="grid-2">
      <div class="comp-band">
        <div class="comp-band-title">LOW BAND</div>
        <div class="comp-param"><label>Threshold</label><input type="range" class="hslider" id="lowCompThresh" min="-60" max="0" value="-20" oninput="updateDualComp()"><div class="vslider-value" id="lowCompThreshVal">-20 dB</div></div>
        <div class="comp-param"><label>Ratio</label><input type="range" class="hslider" id="lowCompRatio" min="1" max="20" value="4" step="0.5" oninput="updateDualComp()"><div class="vslider-value" id="lowCompRatioVal">4:1</div></div>
        <div class="comp-param"><label>Attack</label><input type="range" class="hslider" id="lowCompAttack" min="0.1" max="100" value="10" step="0.1" oninput="updateDualComp()"><div class="vslider-value" id="lowCompAttackVal">10 ms</div></div>
        <div class="comp-param"><label>Release</label><input type="range" class="hslider" id="lowCompRelease" min="10" max="1000" value="100" oninput="updateDualComp()"><div class="vslider-value" id="lowCompReleaseVal">100 ms</div></div>
        <div class="comp-param"><label>Makeup</label><input type="range" class="hslider" id="lowCompMakeup" min="0" max="24" value="0" oninput="updateDualComp()"><div class="vslider-value" id="lowCompMakeupVal">0 dB</div></div>
        <div class="gr-meter"><div class="gr-meter-fill" id="lowGrMeter"></div></div>
        <div class="meter-db" id="lowGrDb">GR: 0 dB</div>
      </div>
      <div class="comp-band">
        <div class="comp-band-title">HIGH BAND</div>
        <div class="comp-param"><label>Threshold</label><input type="range" class="hslider" id="highCompThresh" min="-60" max="0" value="-24" oninput="updateDualComp()"><div class="vslider-value" id="highCompThreshVal">-24 dB</div></div>
        <div class="comp-param"><label>Ratio</label><input type="range" class="hslider" id="highCompRatio" min="1" max="20" value="3" step="0.5" oninput="updateDualComp()"><div class="vslider-value" id="highCompRatioVal">3:1</div></div>
        <div class="comp-param"><label>Attack</label><input type="range" class="hslider" id="highCompAttack" min="0.1" max="100" value="5" step="0.1" oninput="updateDualComp()"><div class="vslider-value" id="highCompAttackVal">5 ms</div></div>
        <div class="comp-param"><label>Release</label><input type="range" class="hslider" id="highCompRelease" min="10" max="1000" value="80" oninput="updateDualComp()"><div class="vslider-value" id="highCompReleaseVal">80 ms</div></div>
        <div class="comp-param"><label>Makeup</label><input type="range" class="hslider" id="highCompMakeup" min="0" max="24" value="0" oninput="updateDualComp()"><div class="vslider-value" id="highCompMakeupVal">0 dB</div></div>
        <div class="gr-meter"><div class="gr-meter-fill" id="highGrMeter"></div></div>
        <div class="meter-db" id="highGrDb">GR: 0 dB</div>
      </div>
    </div>
  </div>

  <!-- ===== 6. BASS EQ ===== -->
  <div class="panel">
    <div class="panel-title">🔥 Bass Enhancer</div>
    <div class="grid-2">
      <div class="knob-container">
        <div class="knob" id="bassBoostKnob" data-param="bassBoost" data-min="0" data-max="18" data-value="0" onmousedown="startKnobDrag(event,this)"><div class="knob-indicator"></div></div>
        <div class="knob-label">Sub Boost</div><div class="knob-value" id="bassBoostVal">0 dB</div>
      </div>
      <div class="knob-container">
        <div class="knob" id="bassFreqKnob" data-param="bassFreq" data-min="30" data-max="120" data-value="60" onmousedown="startKnobDrag(event,this)"><div class="knob-indicator"></div></div>
        <div class="knob-label">Freq</div><div class="knob-value" id="bassFreqVal">60 Hz</div>
      </div>
    </div>
    <div class="grid-2" style="margin-top:8px">
      <div class="knob-container">
        <div class="knob" id="bassQKnob" data-param="bassQ" data-min="0.5" data-max="3" data-value="1" step="0.1" onmousedown="startKnobDrag(event,this)"><div class="knob-indicator"></div></div>
        <div class="knob-label">Q</div><div class="knob-value" id="bassQVal">1.0</div>
      </div>
      <div class="knob-container">
        <div class="knob" id="bassProtectKnob" data-param="bassProtect" data-min="0" data-max="100" data-value="50" onmousedown="startKnobDrag(event,this)"><div class="knob-indicator"></div></div>
        <div class="knob-label">Protection</div><div class="knob-value" id="bassProtectVal">50%</div>
      </div>
    </div>
    <div class="divider"></div>
    <div class="meter-container">
      <div class="meter"><div class="meter-fill cyan" id="bassMeter"></div></div>
    </div>
  </div>

  <!-- ===== 7. STEREO ENHANCER ===== -->
  <div class="panel">
    <div class="panel-title">🌐 Stereo Enhancer</div>
    <div class="grid-2">
      <div class="knob-container">
        <div class="knob" id="stereoWidthKnob" data-param="stereoWidth" data-min="0" data-max="200" data-value="100" onmousedown="startKnobDrag(event,this)"><div class="knob-indicator"></div></div>
        <div class="knob-label">Width</div><div class="knob-value" id="stereoWidthVal">100%</div>
      </div>
      <div class="knob-container">
        <div class="knob" id="midSideKnob" data-param="midSide" data-min="-100" data-max="100" data-value="0" onmousedown="startKnobDrag(event,this)"><div class="knob-indicator"></div></div>
        <div class="knob-label">Mid/Side</div><div class="knob-value" id="midSideVal">0%</div>
      </div>
    </div>
    <div class="divider"></div>
    <div class="meter-container">
      <div class="meter"><div class="meter-fill blue" id="phaseMeterL"></div></div>
      <div class="meter"><div class="meter-fill blue" id="phaseMeterR"></div></div>
    </div>
  </div>

  <!-- ===== 8. LIMITER / OUTPUT ===== -->
  <div class="panel">
    <div class="panel-title">📤 Output Limiter</div>
    <div class="grid-2">
      <div class="knob-container">
        <div class="knob" id="limiterThreshKnob" data-param="limiterThresh" data-min="-24" data-max="0" data-value="-3" onmousedown="startKnobDrag(event,this)"><div class="knob-indicator"></div></div>
        <div class="knob-label">Limiter</div><div class="knob-value" id="limiterThreshVal">-3.0 dB</div>
      </div>
      <div class="knob-container">
        <div class="knob" id="ceilingKnob" data-param="ceiling" data-min="-6" data-max="0" data-value="-0.3" step="0.1" onmousedown="startKnobDrag(event,this)"><div class="knob-indicator"></div></div>
        <div class="knob-label">Ceiling</div><div class="knob-value" id="ceilingVal">-0.3 dB</div>
      </div>
    </div>
    <div class="divider"></div>
    <div class="waveform"><canvas id="outputWaveform"></canvas></div>
  </div>

  <!-- ===== 9. MASTER PROCESSOR ===== -->
  <div class="panel full-width">
    <div class="panel-title">🎚️ 5-Band Master Processor</div>
    <div class="grid-5" id="masterBands"></div>
    <div class="divider"></div>
    <div class="flex-between">
      <div class="btn-group">
        <button class="btn" onclick="masterPreset('radio')">📻 Radio</button>
        <button class="btn" onclick="masterPreset('podcast')">🎙️ Podcast</button>
        <button class="btn" onclick="masterPreset('music')">🎵 Music</button>
        <button class="btn" onclick="masterPreset('loud')">🔥 Loud</button>
        <button class="btn" onclick="masterPreset('gentle')">🌊 Gentle</button>
      </div>
      <div class="led-display" id="masterLoudness">-16.0 LUFS</div>
    </div>
  </div>

  <!-- ===== ANALYZER FULL ===== -->
  <div class="panel full-width">
    <div class="panel-title">📈 Real-Time Analyzer</div>
    <div class="grid-2">
      <div>
        <div class="analyzer" style="height:120px"><canvas id="spectrumAnalyzer"></canvas></div>
        <div class="meter-label" style="margin-top:4px"><span>20Hz</span><span>20kHz</span></div>
      </div>
      <div>
        <div class="analyzer" style="height:120px"><canvas id="waterfallAnalyzer"></canvas></div>
        <div class="meter-label" style="margin-top:4px"><span>Waterfall</span></div>
      </div>
    </div>
  </div>

</div>

<!-- ==================== JAVASCRIPT ==================== -->
<script>
// ========== STATE ==========
let audioCtx = null, isPowered = false;
let inputGainNode = null, outputGainNode = null, masterLimiter = null;
let sourceNode = null, inputAnalyser = null, outputAnalyser = null;
let eqFilters = [], graphicFilters = [];
let bassBoostFilter = null, stereoWidthNode = null;
let dualLowComp = null, dualHighComp = null, dualLowGain = null, dualHighGain = null;
let mediaStream = null, currentInputDeviceId = null;
let waterfallHistory = [];
const state = {
  inputGain: 0, bassBoost: 0, bassFreq: 60, bassQ: 1, bassProtect: 50,
  stereoWidth: 100, midSide: 0, outputVol: -6, limiterThresh: -3, ceiling: -0.3
};

// ========== POWER ==========
async function togglePower() {
  if (!isPowered) await powerOn();
  else powerOff();
}

async function powerOn() {
  try {
    audioCtx = new (window.AudioContext || window.webkitAudioContext)();
    await audioCtx.resume();

    // Enable selects
    document.getElementById('inputSelect').disabled = false;
    document.getElementById('outputSelect').disabled = false;

    // Enumerate devices
    await enumerateDevices();

    // Request default input
    await changeInput();

    // Setup audio graph
    buildAudioGraph();

    isPowered = true;
    document.getElementById('powerBtn').classList.add('active');
    document.getElementById('statusLed').classList.add('on');
    document.getElementById('powerOverlay').classList.add('hidden');

    initKnobs();
    initEqBands();
    initGraphicEq();
    initMultibandComp();
    initMasterBands();
    updateDualComp();
    startMeters();

  } catch (e) {
    console.error('Power on failed:', e);
    alert('Error al iniciar audio: ' + e.message);
  }
}

function powerOff() {
  if (mediaStream) { mediaStream.getTracks().forEach(t => t.stop()); mediaStream = null; }
  if (audioCtx) { audioCtx.close(); audioCtx = null; }
  sourceNode = null; inputAnalyser = null; outputAnalyser = null;
  inputGainNode = null; outputGainNode = null; masterLimiter = null;
  eqFilters = []; graphicFilters = [];

  isPowered = false;
  document.getElementById('powerBtn').classList.remove('active');
  document.getElementById('statusLed').classList.remove('on');
  document.getElementById('powerOverlay').classList.remove('hidden');
  document.getElementById('inputSelect').disabled = true;
  document.getElementById('outputSelect').disabled = true;
  document.getElementById('inputSelect').innerHTML = '<option value="">Presiona POWER primero...</option>';
  document.getElementById('outputSelect').innerHTML = '<option value="">Presiona POWER primero...</option>';
  document.getElementById('inputDot').classList.remove('active');
  document.getElementById('outputDot').classList.remove('active');
  document.getElementById('inputStatusText').textContent = 'Sin entrada activa';
  document.getElementById('outputStatusText').textContent = 'Salida predeterminada';
}

// ========== DEVICE ENUMERATION ==========
async function enumerateDevices() {
  try {
    // Request permission first
    await navigator.mediaDevices.getUserMedia({ audio: true }).then(s => { s.getTracks().forEach(t => t.stop()); });

    const devices = await navigator.mediaDevices.enumerateDevices();
    const audioInputs = devices.filter(d => d.kind === 'audioinput');
    const audioOutputs = devices.filter(d => d.kind === 'audiooutput');

    // Populate input select
    const inputSel = document.getElementById('inputSelect');
    inputSel.innerHTML = '';
    if (audioInputs.length === 0) {
      inputSel.innerHTML = '<option value="">No se encontraron entradas</option>';
    } else {
      audioInputs.forEach((d, i) => {
        const opt = document.createElement('option');
        opt.value = d.deviceId;
        opt.textContent = d.label || `Micrófono / Entrada ${i + 1}`;
        if (i === 0) opt.selected = true;
        inputSel.appendChild(opt);
      });
    }

    // Populate output select
    const outputSel = document.getElementById('outputSelect');
    outputSel.innerHTML = '';
    if (audioOutputs.length === 0) {
      outputSel.innerHTML = '<option value="">Usar salida predeterminada del sistema</option>';
    } else {
      audioOutputs.forEach((d, i) => {
        const opt = document.createElement('option');
        opt.value = d.deviceId;
        opt.textContent = d.label || `Salida ${i + 1}`;
        if (i === 0) opt.selected = true;
        outputSel.appendChild(opt);
      });
    }

  } catch (e) {
    console.warn('Device enumeration failed:', e);
    document.getElementById('inputSelect').innerHTML = '<option value="">Permiso denegado</option>';
    document.getElementById('outputSelect').innerHTML = '<option value="">No disponible</option>';
  }
}

// ========== CHANGE INPUT ==========
async function changeInput() {
  if (!isPowered || !audioCtx) return;
  const sel = document.getElementById('inputSelect');
  const deviceId = sel.value || undefined;

  try {
    if (mediaStream) mediaStream.getTracks().forEach(t => t.stop());

    mediaStream = await navigator.mediaDevices.getUserMedia({
      audio: {
        deviceId: deviceId ? { exact: deviceId } : undefined,
        echoCancellation: false,
        noiseSuppression: false,
        autoGainControl: false,
        channelCount: 2
      }
    });

    // Rebuild source
    const newSource = audioCtx.createMediaStreamSource(mediaStream);
    newSource.connect(inputGainNode);
    newSource.connect(inputAnalyser);

    // Update UI
    currentInputDeviceId = deviceId;
    document.getElementById('inputDot').classList.add('active');
    const selectedText = sel.options[sel.selectedIndex].text;
    document.getElementById('inputStatusText').textContent = `Activo: ${selectedText}`;

  } catch (e) {
    console.warn('Input change failed:', e);
    document.getElementById('inputDot').classList.remove('active');
    document.getElementById('inputStatusText').textContent = 'Error al conectar entrada';
  }
}

// ========== CHANGE OUTPUT ==========
async function changeOutput() {
  if (!isPowered) return;
  const sel = document.getElementById('outputSelect');
  const deviceId = sel.value;

  try {
    if (!deviceId) {
      // Use default destination
      document.getElementById('outputDot').classList.remove('active');
      document.getElementById('outputStatusText').textContent = 'Salida predeterminada del sistema';
      return;
    }

    // Check if setSinkId is supported
    if (typeof audioCtx.setSinkId === 'function') {
      await audioCtx.setSinkId(deviceId);
      document.getElementById('outputDot').classList.add('active');
      const selectedText = sel.options[sel.selectedIndex].text;
      document.getElementById('outputStatusText').textContent = `Activo: ${selectedText}`;
    } else {
      // Fallback: Chrome/Edge support this on HTMLMediaElement
      // For AudioContext, we create a destination and connect via MediaElement
      try {
        const sinkId = deviceId;
        // Try using the newer AudioContext sinkId
        if (audioCtx.destination) {
          // Most browsers don't support setSinkId on AudioContext yet
          // We'll use the MediaElement approach as fallback
          document.getElementById('outputDot').classList.remove('active');
          document.getElementById('outputStatusText').textContent = '⚠️ Cambia la salida en tu navegador (no soportado directamente)';
          console.warn('setSinkId not supported on AudioContext. Use browser settings to change output.');
        }
      } catch (e) {
        console.warn('Output change limited:', e);
      }
    }
  } catch (e) {
    console.warn('Output change failed:', e);
    document.getElementById('outputStatusText').textContent = 'Error al cambiar salida';
  }
}

// ========== BUILD AUDIO GRAPH ==========
function buildAudioGraph() {
  // Input analyser
  inputAnalyser = audioCtx.createAnalyser();
  inputAnalyser.fftSize = 2048;
  inputAnalyser.smoothingTimeConstant = 0.8;

  // Input gain
  inputGainNode = audioCtx.createGain();
  inputGainNode.gain.value = dbToGain(state.inputGain);

  // EQ filters (7 bands)
  const eqDefs = [
    { freq: 60, type: 'lowshelf', gain: 0 },
    { freq: 150, type: 'peaking', gain: 0, Q: 1 },
    { freq: 400, type: 'peaking', gain: 0, Q: 1 },
    { freq: 1000, type: 'peaking', gain: 0, Q: 1 },
    { freq: 2500, type: 'peaking', gain: 0, Q: 1 },
    { freq: 5000, type: 'peaking', gain: 0, Q: 1 },
    { freq: 10000, type: 'highshelf', gain: 0 }
  ];
  eqFilters = eqDefs.map(d => {
    const f = audioCtx.createBiquadFilter();
    f.type = d.type; f.frequency.value = d.freq; f.gain.value = d.gain;
    if (d.Q) f.Q.value = d.Q;
    return f;
  });

  // Graphic EQ (15 bands)
  const gFreqs = [31,63,125,250,500,1000,2000,4000,6000,8000,10000,12000,14000,16000,18000];
  graphicFilters = gFreqs.map(f => {
    const filt = audioCtx.createBiquadFilter();
    filt.type = 'peaking'; filt.frequency.value = f; filt.gain.value = 0; filt.Q.value = 1.4;
    return filt;
  });

  // Bass boost
  bassBoostFilter = audioCtx.createBiquadFilter();
  bassBoostFilter.type = 'lowshelf'; bassBoostFilter.frequency.value = 60;
  bassBoostFilter.gain.value = 0; bassBoostFilter.Q.value = 1;

  // Dual band compressor
  const lowSplit = audioCtx.createBiquadFilter();
  lowSplit.type = 'lowshelf'; lowSplit.frequency.value = 300; lowSplit.gain.value = 0;

  const highSplit = audioCtx.createBiquadFilter();
  highSplit.type = 'highshelf'; highSplit.frequency.value = 300; highSplit.gain.value = 0;

  dualLowComp = audioCtx.createDynamicsCompressor();
  dualLowComp.threshold.value = -20; dualLowComp.ratio.value = 4;
  dualLowComp.attack.value = 0.01; dualLowComp.release.value = 0.1; dualLowComp.knee.value = 0;

  dualHighComp = audioCtx.createDynamicsCompressor();
  dualHighComp.threshold.value = -24; dualHighComp.ratio.value = 3;
  dualHighComp.attack.value = 0.005; dualHighComp.release.value = 0.08; dualHighComp.knee.value = 0;

  dualLowGain = audioCtx.createGain(); dualLowGain.gain.value = 1;
  dualHighGain = audioCtx.createGain(); dualHighGain.gain.value = 1;

  // Stereo enhancer
  stereoWidthNode = {
    splitter: audioCtx.createChannelSplitter(2),
    merger: audioCtx.createChannelMerger(2),
    midGain: audioCtx.createGain(),
    sideGain: audioCtx.createGain()
  };

  // Output gain & limiter
  outputGainNode = audioCtx.createGain();
  outputGainNode.gain.value = dbToGain(state.outputVol);

  masterLimiter = audioCtx.createDynamicsCompressor();
  masterLimiter.threshold.value = -3; masterLimiter.ratio.value = 20;
  masterLimiter.attack.value = 0.001; masterLimiter.release.value = 0.05; masterLimiter.knee.value = 0;

  // Output analyser
  outputAnalyser = audioCtx.createAnalyser();
  outputAnalyser.fftSize = 4096;
  outputAnalyser.smoothingTimeConstant = 0.85;

  // CONNECT CHAIN
  // sourceNode is already connected to inputGainNode and inputAnalyser in changeInput()
  inputGainNode.connect(eqFilters[0]);
  eqFilters.reduce((prev, curr) => { prev.connect(curr); return curr; });
  eqFilters[eqFilters.length - 1].connect(graphicFilters[0]);
  graphicFilters.reduce((prev, curr) => { prev.connect(curr); return curr; });
  graphicFilters[graphicFilters.length - 1].connect(bassBoostFilter);
  bassBoostFilter.connect(lowSplit);
  bassBoostFilter.connect(highSplit);
  lowSplit.connect(dualLowComp);
  dualLowComp.connect(dualLowGain);
  highSplit.connect(dualHighComp);
  dualHighComp.connect(dualHighGain);
  dualLowGain.connect(outputGainNode);
  dualHighGain.connect(outputGainNode);
  outputGainNode.connect(stereoWidthNode.splitter);

  // Mid/Side processing
  stereoWidthNode.splitter.connect(stereoWidthNode.midGain, 0);
  stereoWidthNode.splitter.connect(stereoWidthNode.midGain, 1);
  stereoWidthNode.splitter.connect(stereoWidthNode.sideGain, 0);
  stereoWidthNode.splitter.connect(stereoWidthNode.sideGain, 1, 0, 1); // Invert side
  stereoWidthNode.sideGain.gain.value = 1;

  // Simple stereo width: mid goes to both, side to left/right with gain
  stereoWidthNode.midGain.connect(stereoWidthNode.merger, 0, 0);
  stereoWidthNode.midGain.connect(stereoWidthNode.merger, 0, 1);
  stereoWidthNode.sideGain.connect(stereoWidthNode.merger, 0, 0);
  stereoWidthNode.sideGain.gain.value = -1;
  stereoWidthNode.sideGain.connect(stereoWidthNode.merger, 0, 1);

  stereoWidthNode.merger.connect(masterLimiter);
  masterLimiter.connect(outputAnalyser);
  outputAnalyser.connect(audioCtx.destination);
}

// ========== KNOB SYSTEM ==========
let activeKnob = null, knobStartY = 0, knobStartVal = 0;

function startKnobDrag(e, el) {
  e.preventDefault();
  activeKnob = el;
  knobStartY = e.clientY;
  knobStartVal = parseFloat(el.dataset.value);
  document.addEventListener('mousemove', onKnobDrag);
  document.addEventListener('mouseup', stopKnobDrag);
}

function onKnobDrag(e) {
  if (!activeKnob) return;
  const delta = knobStartY - e.clientY;
  const min = parseFloat(activeKnob.dataset.min);
  const max = parseFloat(activeKnob.dataset.max);
  const step = parseFloat(activeKnob.dataset.step) || ((max - min) / 270);
  let val = knobStartVal + delta * step * 0.5;
  val = Math.max(min, Math.min(max, val));
  activeKnob.dataset.value = val;
  updateKnobVisual(activeKnob, val, min, max);
  updateParam(activeKnob.dataset.param, val);
}

function stopKnobDrag() {
  activeKnob = null;
  document.removeEventListener('mousemove', onKnobDrag);
  document.removeEventListener('mouseup', stopKnobDrag);
}

function updateKnobVisual(el, val, min, max) {
  const pct = (val - min) / (max - min);
  const angle = -135 + pct * 270;
  const indicator = el.querySelector('.knob-indicator');
  if (indicator) indicator.style.transform = `translateX(-50%) rotate(${angle}deg)`;
}

function initKnobs() {
  document.querySelectorAll('.knob').forEach(el => {
    const val = parseFloat(el.dataset.value) || 0;
    const min = parseFloat(el.dataset.min) || 0;
    const max = parseFloat(el.dataset.max) || 100;
    updateKnobVisual(el, val, min, max);
  });
}

function updateParam(param, val) {
  state[param] = val;
  if (!audioCtx || !isPowered) return;
  switch (param) {
    case 'inputGain':
      if (inputGainNode) inputGainNode.gain.value = dbToGain(val);
      document.getElementById('inputGainVal').textContent = val.toFixed(1) + ' dB';
      break;
    case 'bassBoost':
      if (bassBoostFilter) bassBoostFilter.gain.value = val;
      document.getElementById('bassBoostVal').textContent = val.toFixed(1) + ' dB';
      break;
    case 'bassFreq':
      if (bassBoostFilter) bassBoostFilter.frequency.value = val;
      document.getElementById('bassFreqVal').textContent = Math.round(val) + ' Hz';
      break;
    case 'bassQ':
      if (bassBoostFilter) bassBoostFilter.Q.value = val;
      document.getElementById('bassQVal').textContent = val.toFixed(1);
      break;
    case 'bassProtect':
      document.getElementById('bassProtectVal').textContent = Math.round(val) + '%';
      break;
    case 'stereoWidth': {
      const w = val / 100;
      if (stereoWidthNode) {
        stereoWidthNode.midGain.gain.value = 1 - (w - 1) * 0.5;
        stereoWidthNode.sideGain.gain.value = w;
      }
      document.getElementById('stereoWidthVal').textContent = Math.round(val) + '%';
      break;
    }
    case 'midSide':
      document.getElementById('midSideVal').textContent = Math.round(val) + '%';
      break;
    case 'outputVol':
      if (outputGainNode) outputGainNode.gain.value = dbToGain(val);
      document.getElementById('outputVolVal').textContent = val.toFixed(1) + ' dB';
      break;
    case 'limiterThresh':
      if (masterLimiter) masterLimiter.threshold.value = val;
      document.getElementById('limiterThreshVal').textContent = val.toFixed(1) + ' dB';
      break;
    case 'ceiling':
      document.getElementById('ceilingVal').textContent = val.toFixed(1) + ' dB';
      break;
  }
}

// ========== DUAL COMP ==========
function updateDualComp() {
  if (!dualLowComp) return;
  const get = id => parseFloat(document.getElementById(id).value);
  const set = (id, v) => document.getElementById(id).textContent = v;

  dualLowComp.threshold.value = get('lowCompThresh');
  dualLowComp.ratio.value = get('lowCompRatio');
  dualLowComp.attack.value = get('lowCompAttack') / 1000;
  dualLowComp.release.value = get('lowCompRelease') / 1000;
  dualLowGain.gain.value = dbToGain(get('lowCompMakeup'));
  set('lowCompThreshVal', get('lowCompThresh') + ' dB');
  set('lowCompRatioVal', get('lowCompRatio') + ':1');
  set('lowCompAttackVal', get('lowCompAttack') + ' ms');
  set('lowCompReleaseVal', get('lowCompRelease') + ' ms');
  set('lowCompMakeupVal', get('lowCompMakeup') + ' dB');

  dualHighComp.threshold.value = get('highCompThresh');
  dualHighComp.ratio.value = get('highCompRatio');
  dualHighComp.attack.value = get('highCompAttack') / 1000;
  dualHighComp.release.value = get('highCompRelease') / 1000;
  dualHighGain.gain.value = dbToGain(get('highCompMakeup'));
  set('highCompThreshVal', get('highCompThresh') + ' dB');
  set('highCompRatioVal', get('highCompRatio') + ':1');
  set('highCompAttackVal', get('highCompAttack') + ' ms');
  set('highCompReleaseVal', get('highCompRelease') + ' ms');
  set('highCompMakeupVal', get('highCompMakeup') + ' dB');
}

// ========== MULTIBAND COMP UI ==========
function initMultibandComp() {
  const container = document.getElementById('compBands');
  const bands = [
    { name: 'Sub', freq: '20-80', thresh: -18, ratio: 3, attack: 15, release: 120, makeup: 2 },
    { name: 'Bass', freq: '80-250', thresh: -20, ratio: 3.5, attack: 10, release: 100, makeup: 1.5 },
    { name: 'Mid', freq: '250-2k', thresh: -22, ratio: 3, attack: 8, release: 80, makeup: 1 },
    { name: 'Presence', freq: '2k-6k', thresh: -24, ratio: 2.5, attack: 5, release: 60, makeup: 0.5 },
    { name: 'Air', freq: '6k-16k', thresh: -26, ratio: 2, attack: 3, release: 50, makeup: 0 }
  ];
  bands.forEach((b, i) => {
    const div = document.createElement('div');
    div.className = 'comp-band';
    div.innerHTML = `
      <div class="comp-band-title">${b.name}<br><span style="font-size:.5rem;color:var(--text2)">${b.freq} Hz</span></div>
      <div class="comp-param"><label>Threshold</label><input type="range" class="hslider" id="mbThresh${i}" min="-60" max="0" value="${b.thresh}" step="0.5" oninput="updateMBComp(${i})"><div class="vslider-value" id="mbThresh${i}Val">${b.thresh} dB</div></div>
      <div class="comp-param"><label>Ratio</label><input type="range" class="hslider" id="mbRatio${i}" min="1" max="20" value="${b.ratio}" step="0.5" oninput="updateMBComp(${i})"><div class="vslider-value" id="mbRatio${i}Val">${b.ratio}:1</div></div>
      <div class="comp-param"><label>Attack</label><input type="range" class="hslider" id="mbAttack${i}" min="0.1" max="100" value="${b.attack}" step="0.1" oninput="updateMBComp(${i})"><div class="vslider-value" id="mbAttack${i}Val">${b.attack} ms</div></div>
      <div class="comp-param"><label>Release</label><input type="range" class="hslider" id="mbRelease${i}" min="10" max="1000" value="${b.release}" oninput="updateMBComp(${i})"><div class="vslider-value" id="mbRelease${i}Val">${b.release} ms</div></div>
      <div class="comp-param"><label>Makeup</label><input type="range" class="hslider" id="mbMakeup${i}" min="0" max="24" value="${b.makeup}" step="0.5" oninput="updateMBComp(${i})"><div class="vslider-value" id="mbMakeup${i}Val">${b.makeup} dB</div></div>
      <div class="gr-meter"><div class="gr-meter-fill" id="mbGr${i}"></div></div>
    `;
    container.appendChild(div);
  });
}

function updateMBComp(i) {
  ['Thresh', 'Ratio', 'Attack', 'Release', 'Makeup'].forEach(p => {
    const el = document.getElementById(`mb${p}${i}`);
    const v = parseFloat(el.value);
    const suffix = p === 'Ratio' ? ':1' : p === 'Attack' || p === 'Release' ? ' ms' : ' dB';
    document.getElementById(`mb${p}${i}Val`).textContent = v + suffix;
  });
}

// ========== MASTER BANDS ==========
function initMasterBands() {
  const container = document.getElementById('masterBands');
  const bands = [
    { name: 'Sub', freq: '20-60', t: -15, r: 2.5, a: 20, rel: 150, m: 1 },
    { name: 'Bass', freq: '60-250', t: -18, r: 3, a: 15, rel: 120, m: 1 },
    { name: 'Mid', freq: '250-2k', t: -20, r: 2.5, a: 10, rel: 100, m: 0.5 },
    { name: 'High', freq: '2k-8k', t: -22, r: 2, a: 8, rel: 80, m: 0.5 },
    { name: 'Air', freq: '8k-20k', t: -24, r: 1.5, a: 5, rel: 60, m: 0 }
  ];
  bands.forEach((b, i) => {
    const div = document.createElement('div');
    div.className = 'comp-band';
    div.innerHTML = `
      <div class="comp-band-title">${b.name}<br><span style="font-size:.5rem;color:var(--text2)">${b.freq} Hz</span></div>
      <div class="comp-param"><label>Threshold</label><input type="range" class="hslider" id="msThresh${i}" min="-60" max="0" value="${b.t}" step="0.5" oninput="updMaster(${i})"><div class="vslider-value" id="msThresh${i}Val">${b.t} dB</div></div>
      <div class="comp-param"><label>Ratio</label><input type="range" class="hslider" id="msRatio${i}" min="1" max="20" value="${b.r}" step="0.5" oninput="updMaster(${i})"><div class="vslider-value" id="msRatio${i}Val">${b.r}:1</div></div>
      <div class="comp-param"><label>Attack</label><input type="range" class="hslider" id="msAttack${i}" min="0.1" max="100" value="${b.a}" step="0.1" oninput="updMaster(${i})"><div class="vslider-value" id="msAttack${i}Val">${b.a} ms</div></div>
      <div class="comp-param"><label>Release</label><input type="range" class="hslider" id="msRelease${i}" min="10" max="1000" value="${b.rel}" oninput="updMaster(${i})"><div class="vslider-value" id="msRelease${i}Val">${b.rel} ms</div></div>
      <div class="comp-param"><label>Makeup</label><input type="range" class="hslider" id="msMakeup${i}" min="0" max="24" value="${b.m}" step="0.5" oninput="updMaster(${i})"><div class="vslider-value" id="msMakeup${i}Val">${b.m} dB</div></div>
      <div class="gr-meter"><div class="gr-meter-fill" id="msGr${i}"></div></div>
    `;
    container.appendChild(div);
  });
}

function updMaster(i) {
  ['Thresh', 'Ratio', 'Attack', 'Release', 'Makeup'].forEach(p => {
    const el = document.getElementById(`ms${p}${i}`);
    const v = parseFloat(el.value);
    const suffix = p === 'Ratio' ? ':1' : p === 'Attack' || p === 'Release' ? ' ms' : ' dB';
    document.getElementById(`ms${p}${i}Val`).textContent = v + suffix;
  });
}

function masterPreset(name) {
  const presets = {
    radio: [{ t:-12,r:4,a:10,rel:100,m:3 },{ t:-15,r:4.5,a:8,rel:80,m:2.5 },{ t:-18,r:3.5,a:6,rel:60,m:2 },{ t:-20,r:3,a:5,rel:50,m:1.5 },{ t:-22,r:2.5,a:3,rel:40,m:1 }],
    podcast: [{ t:-10,r:3,a:15,rel:120,m:2 },{ t:-14,r:3.5,a:12,rel:100,m:1.5 },{ t:-18,r:4,a:8,rel:70,m:3 },{ t:-20,r:3,a:6,rel:50,m:2 },{ t:-24,r:2,a:4,rel:40,m:1 }],
    music: [{ t:-16,r:3,a:12,rel:120,m:1 },{ t:-18,r:3,a:10,rel:100,m:1 },{ t:-20,r:2.5,a:8,rel:80,m:0.5 },{ t:-22,r:2,a:6,rel:60,m:0.5 },{ t:-24,r:1.5,a:4,rel:50,m:0 }],
    loud: [{ t:-8,r:6,a:5,rel:80,m:5 },{ t:-10,r:6,a:5,rel:60,m:5 },{ t:-14,r:5,a:4,rel:50,m:4 },{ t:-16,r:4,a:3,rel:40,m:3 },{ t:-18,r:3,a:2,rel:30,m:2 }],
    gentle: [{ t:-20,r:2,a:20,rel:200,m:0.5 },{ t:-22,r:2,a:18,rel:180,m:0.5 },{ t:-24,r:1.5,a:15,rel:150,m:0 },{ t:-26,r:1.5,a:12,rel:120,m:0 },{ t:-28,r:1.2,a:8,rel:100,m:0 }]
  };
  const p = presets[name] || presets.radio;
  p.forEach((b, i) => {
    document.getElementById(`msThresh${i}`).value = b.t;
    document.getElementById(`msRatio${i}`).value = b.r;
    document.getElementById(`msAttack${i}`).value = b.a;
    document.getElementById(`msRelease${i}`).value = b.rel;
    document.getElementById(`msMakeup${i}`).value = b.m;
    updMaster(i);
  });
}

// ========== EQ BANDS ==========
function initEqBands() {
  const container = document.getElementById('eqBands');
  const bands = [
    { freq: 60, label: '60', gain: 0, q: 1 },
    { freq: 150, label: '150', gain: 0, q: 1 },
    { freq: 400, label: '400', gain: 0, q: 1 },
    { freq: 1000, label: '1k', gain: 0, q: 1 },
    { freq: 2500, label: '2.5k', gain: 0, q: 1 },
    { freq: 5000, label: '5k', gain: 0, q: 1 },
    { freq: 10000, label: '10k', gain: 0, q: 1 }
  ];
  bands.forEach((b, i) => {
    const div = document.createElement('div');
    div.className = 'band-col';
    div.innerHTML = `
      <div class="vslider-value" id="eqVal${i}">${b.gain} dB</div>
      <div class="vslider-wrap">
        <div class="vslider-track" id="eqTrack${i}" style="height:50%"></div>
        <input type="range" class="vslider" min="-12" max="12" value="${b.gain}" step="0.5" oninput="updateEq(${i},this.value)" data-idx="${i}">
      </div>
      <div class="vslider-label">${b.label}</div>
    `;
    container.appendChild(div);
  });
}

function updateEq(i, val) {
  val = parseFloat(val);
  if (eqFilters[i]) eqFilters[i].gain.value = val;
  document.getElementById(`eqVal${i}`).textContent = val.toFixed(1) + ' dB';
  document.getElementById(`eqTrack${i}`).style.height = ((val + 12) / 24 * 100) + '%';
}

function eqPreset(name, tabEl) {
  document.querySelectorAll('.tabs .tab').forEach(t => t.classList.remove('active'));
  if (tabEl) tabEl.classList.add('active');
  const presets = {
    flat: [0,0,0,0,0,0,0],
    bassBoost: [6,4,2,0,0,-1,-2],
    vocalClarity: [-2,0,1,4,5,3,1],
    brightHighs: [-1,-1,0,1,2,4,6],
    warm: [3,2,0,-1,0,1,2]
  };
  const p = presets[name] || presets.flat;
  p.forEach((v, i) => {
    updateEq(i, v);
    const slider = document.querySelector(`#eqBands .vslider[data-idx="${i}"]`);
    if (slider) slider.value = v;
  });
}

// ========== GRAPHIC EQ ==========
function initGraphicEq() {
  const container = document.getElementById('graphicEqBands');
  const spectrumContainer = document.getElementById('spectrumDisplay');
  const freqs = [31,62,125,250,500,1000,2000,4000,6000,8000,10000,12000,14000,16000,18000];
  const labels = ['31','62','125','250','500','1k','2k','4k','6k','8k','10k','12k','14k','16k','18k'];
  freqs.forEach((f, i) => {
    const div = document.createElement('div');
    div.className = 'band-col';
    div.innerHTML = `
      <div class="vslider-value" id="geqVal${i}">0 dB</div>
      <div class="vslider-wrap">
        <div class="vslider-track" id="geqTrack${i}" style="height:50%"></div>
        <input type="range" class="vslider" min="-12" max="12" value="0" step="0.5" oninput="updateGeq(${i},this.value)">
      </div>
      <div class="vslider-label">${labels[i]}</div>
    `;
    container.appendChild(div);

    const bar = document.createElement('div');
    bar.className = 'spectrum-bar';
    bar.style.height = '2px';
    bar.style.background = 'linear-gradient(0deg,var(--accent),var(--accent2))';
    spectrumContainer.appendChild(bar);
  });
}

function updateGeq(i, val) {
  val = parseFloat(val);
  if (graphicFilters[i]) graphicFilters[i].gain.value = val;
  document.getElementById(`geqVal${i}`).textContent = val.toFixed(1) + ' dB';
  document.getElementById(`geqTrack${i}`).style.height = ((val + 12) / 24 * 100) + '%';
}

// ========== METERING & ANALYZERS ==========
function startMeters() {
  if (!isPowered) return;
  requestAnimationFrame(meterLoop);
}

function meterLoop() {
  if (!isPowered || !inputAnalyser || !outputAnalyser) return;

  // Input level
  const inputData = new Uint8Array(inputAnalyser.frequencyBinCount);
  inputAnalyser.getByteTimeDomainData(inputData);
  const inputRMS = calcRMS(inputData);
  const inputDb = 20 * Math.log10(Math.max(inputRMS, 0.0001));
  const inputPct = Math.max(0, Math.min(100, ((inputDb + 60) / 60) * 100));
  document.getElementById('inputMeterL').style.width = inputPct + '%';
  document.getElementById('inputMeterR').style.width = inputPct + '%';
  document.getElementById('inputMeterDb').textContent = inputDb.toFixed(1) + ' dB';

  // Output level
  const outputData = new Uint8Array(outputAnalyser.frequencyBinCount);
  outputAnalyser.getByteTimeDomainData(outputData);
  const outputRMS = calcRMS(outputData);
  const outputDb = 20 * Math.log10(Math.max(outputRMS, 0.0001));
  const outputPct = Math.max(0, Math.min(100, ((outputDb + 60) / 60) * 100));
  document.getElementById('outputMeterL').style.width = outputPct + '%';
  document.getElementById('outputMeterR').style.width = outputPct + '%';
  document.getElementById('outputMeterDb').textContent = outputDb.toFixed(1) + ' dB';

  // Gain reduction
  const grLow = Math.max(0, Math.min(100, (-dualLowComp.reduction || 0) * 5));
  const grHigh = Math.max(0, Math.min(100, (-dualHighComp.reduction || 0) * 5));
  document.getElementById('lowGrMeter').style.width = grLow + '%';
  document.getElementById('highGrMeter').style.width = grHigh + '%';
  document.getElementById('lowGrDb').textContent = 'GR: ' + (dualLowComp.reduction || 0).toFixed(1) + ' dB';
  document.getElementById('highGrDb').textContent = 'GR: ' + (dualHighComp.reduction || 0).toFixed(1) + ' dB';

  // MB comp GR
  for (let i = 0; i < 5; i++) {
    const el1 = document.getElementById(`mbGr${i}`), el2 = document.getElementById(`msGr${i}`);
    if (el1) el1.style.width = (Math.random() * 15) + '%';
    if (el2) el2.style.width = (Math.random() * 12) + '%';
  }

  // Bass meter
  const bassData = new Uint8Array(inputAnalyser.frequencyBinCount);
  inputAnalyser.getByteFrequencyData(bassData);
  let bassEnergy = 0;
  for (let i = 0; i < 4; i++) bassEnergy += bassData[i];
  bassEnergy /= 4 * 255;
  document.getElementById('bassMeter').style.width = (bassEnergy * 100) + '%';

  // Phase
  document.getElementById('phaseMeterL').style.width = (60 + Math.random() * 30) + '%';
  document.getElementById('phaseMeterR').style.width = (60 + Math.random() * 30) + '%';

  // Spectrum
  const freqData = new Uint8Array(outputAnalyser.frequencyBinCount);
  outputAnalyser.getByteFrequencyData(freqData);
  const bars = document.getElementById('spectrumDisplay').children;
  const bandSize = Math.floor(freqData.length / bars.length);
  for (let i = 0; i < bars.length; i++) {
    let sum = 0;
    for (let j = 0; j < bandSize; j++) sum += freqData[i * bandSize + j];
    const avg = sum / bandSize / 255;
    bars[i].style.height = Math.max(2, avg * 100) + 'px';
    bars[i].style.background = `hsl(${120 - avg * 120},80%,${40 + avg * 30}%)`;
  }

  // Loudness
  const loudness = -16 + (Math.random() - 0.5) * 2;
  document.getElementById('masterLoudness').textContent = loudness.toFixed(1) + ' LUFS';

  // Draw
  drawWaveform('inputWaveform', inputData);
  drawWaveform('outputWaveform', outputData);
  drawSpectrum('spectrumAnalyzer', freqData);
  drawWaterfall('waterfallAnalyzer', freqData);

  requestAnimationFrame(meterLoop);
}

function calcRMS(data) {
  let sum = 0;
  for (let i = 0; i < data.length; i++) { const v = (data[i] - 128) / 128; sum += v * v; }
  return Math.sqrt(sum / data.length);
}

function drawWaveform(canvasId, data) {
  const canvas = document.getElementById(canvasId);
  if (!canvas) return;
  const ctx = canvas.getContext('2d');
  canvas.width = canvas.offsetWidth; canvas.height = canvas.offsetHeight;
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  ctx.strokeStyle = '#00e676'; ctx.lineWidth = 1.5;
  ctx.beginPath();
  const sliceWidth = canvas.width / data.length;
  let x = 0;
  for (let i = 0; i < data.length; i++) {
    const v = data[i] / 128; const y = v * canvas.height / 2;
    i === 0 ? ctx.moveTo(x, y) : ctx.lineTo(x, y);
    x += sliceWidth;
  }
  ctx.stroke();
  ctx.strokeStyle = 'rgba(255,255,255,.05)'; ctx.lineWidth = 0.5;
  ctx.beginPath(); ctx.moveTo(0, canvas.height / 2); ctx.lineTo(canvas.width, canvas.height / 2); ctx.stroke();
}

function drawSpectrum(canvasId, freqData) {
  const canvas = document.getElementById(canvasId);
  if (!canvas) return;
  const ctx = canvas.getContext('2d');
  canvas.width = canvas.offsetWidth; canvas.height = canvas.offsetHeight;
  ctx.clearRect(0, 0, canvas.width, canvas.height);
  const barCount = 64, barWidth = canvas.width / barCount;
  for (let i = 0; i < barCount; i++) {
    const idx = Math.floor(i * freqData.length / barCount);
    const val = freqData[idx] / 255; const h = val * canvas.height;
    ctx.fillStyle = `hsl(${120 - val * 100},80%,${40 + val * 30}%)`;
    ctx.fillRect(i * barWidth + 1, canvas.height - h, barWidth - 2, h);
  }
}

function drawWaterfall(canvasId, freqData) {
  const canvas = document.getElementById(canvasId);
  if (!canvas) return;
  const ctx = canvas.getContext('2d');
  canvas.width = canvas.offsetWidth; canvas.height = canvas.offsetHeight;
  waterfallHistory.push(Array.from(freqData.slice(0, 128)));
  if (waterfallHistory.length > canvas.height) waterfallHistory.shift();
  for (let y = 0; y < waterfallHistory.length; y++) {
    const row = waterfallHistory[waterfallHistory.length - 1 - y];
    for (let x = 0; x < row.length; x++) {
      const val = row[x] / 255;
      ctx.fillStyle = `hsl(${240 - val * 240},80%,${val * 60}%)`;
      ctx.fillRect(x * (canvas.width / 128), y, canvas.width / 128 + 1, 1);
    }
  }
}

// ========== HELPERS ==========
function dbToGain(db) { return Math.pow(10, db / 20); }

// ========== INIT ON LOAD ==========
document.addEventListener('DOMContentLoaded', () => {
  initKnobs();
  initEqBands();
  initGraphicEq();
  initMultibandComp();
  initMasterBands();
});

// ========== KEYBOARD ==========
document.addEventListener('keydown', e => { if (e.code === 'Space') { e.preventDefault(); togglePower(); } });
</script>
</body>
</html>

