<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>CMMS · Sistema de Información de Mantenimiento · ECCI</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
<style>
:root{
  --bg:#0a0c10;
  --surface:#111318;
  --surface2:#181c24;
  --border:#22293a;
  --accent:#00e5a0;
  --accent2:#ff6b35;
  --accent3:#4e9cff;
  --accent4:#ffd166;
  --text:#eef2ff;
  --muted:#7b8ab8;
  --red:#ff4d6d;
  --green:#00e5a0;
  --yellow:#ffd166;
  --font-head:'Syne',sans-serif;
  --font-mono:'Space Mono',monospace;
  --radius:12px;
}
*{margin:0;padding:0;box-sizing:border-box;}
body{background:var(--bg);color:var(--text);font-family:var(--font-head);min-height:100vh;}

/* NAV */
nav{
  display:flex;align-items:center;justify-content:space-between;
  padding:18px 32px;
  border-bottom:1px solid var(--border);
  background:rgba(10,12,16,.95);
  position:sticky;top:0;z-index:100;
  backdrop-filter:blur(12px);
}
.nav-logo{display:flex;align-items:center;gap:12px;}
.nav-logo .badge{
  background:var(--accent);color:#000;
  font-family:var(--font-mono);font-size:11px;font-weight:700;
  padding:4px 10px;border-radius:4px;letter-spacing:.05em;
}
.nav-title{font-size:15px;font-weight:700;color:var(--text);}
.nav-sub{font-size:11px;color:var(--muted);font-family:var(--font-mono);}
.nav-tabs{display:flex;gap:4px;}
.tab-btn{
  background:none;border:1px solid transparent;
  color:var(--muted);font-family:var(--font-head);font-size:13px;font-weight:600;
  padding:7px 16px;border-radius:8px;cursor:pointer;transition:.2s;
}
.tab-btn.active{border-color:var(--accent);color:var(--accent);background:rgba(0,229,160,.07);}
.tab-btn:hover:not(.active){border-color:var(--border);color:var(--text);}
.nav-right{font-family:var(--font-mono);font-size:11px;color:var(--muted);}

/* MAIN */
main{padding:28px 32px;max-width:1400px;margin:0 auto;}
.page{display:none;animation:fadeIn .3s ease;}
.page.active{display:block;}
@keyframes fadeIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:none}}

/* SECTION HEADER */
.section-header{margin-bottom:24px;}
.section-header h2{font-size:24px;font-weight:800;letter-spacing:-.02em;}
.section-header p{color:var(--muted);font-size:13px;margin-top:4px;font-family:var(--font-mono);}

/* KPI GRID */
.kpi-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:16px;margin-bottom:28px;}
.kpi-card{
  background:var(--surface);border:1px solid var(--border);
  border-radius:var(--radius);padding:20px;position:relative;overflow:hidden;
  transition:.25s;
}
.kpi-card:hover{border-color:var(--accent);transform:translateY(-2px);}
.kpi-card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:3px;
  background:var(--kpi-color,var(--accent));
}
.kpi-label{font-size:11px;color:var(--muted);font-family:var(--font-mono);text-transform:uppercase;letter-spacing:.08em;margin-bottom:8px;}
.kpi-value{font-size:32px;font-weight:800;line-height:1;letter-spacing:-.03em;}
.kpi-unit{font-size:13px;color:var(--muted);margin-left:4px;font-weight:400;}
.kpi-delta{display:inline-flex;align-items:center;gap:4px;margin-top:8px;font-size:11px;font-family:var(--font-mono);padding:3px 8px;border-radius:4px;}
.kpi-delta.up{background:rgba(0,229,160,.12);color:var(--green);}
.kpi-delta.down{background:rgba(255,77,109,.12);color:var(--red);}
.kpi-delta.neutral{background:rgba(255,209,102,.1);color:var(--yellow);}

/* GRID LAYOUTS */
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:20px;}
.grid-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:20px;margin-bottom:20px;}
.grid-1-2{display:grid;grid-template-columns:1fr 2fr;gap:20px;margin-bottom:20px;}
.grid-2-1{display:grid;grid-template-columns:2fr 1fr;gap:20px;margin-bottom:20px;}
@media(max-width:900px){.grid-2,.grid-3,.grid-1-2,.grid-2-1{grid-template-columns:1fr;}}

/* CARD */
.card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;}
.card-header{padding:16px 20px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;}
.card-header h3{font-size:14px;font-weight:700;letter-spacing:-.01em;}
.card-tag{font-size:10px;font-family:var(--font-mono);color:var(--muted);background:var(--surface2);padding:3px 8px;border-radius:4px;border:1px solid var(--border);}
.card-body{padding:20px;}

/* TABLE */
.data-table{width:100%;border-collapse:collapse;font-size:13px;}
.data-table th{padding:10px 14px;text-align:left;font-size:10px;font-family:var(--font-mono);text-transform:uppercase;letter-spacing:.08em;color:var(--muted);border-bottom:1px solid var(--border);white-space:nowrap;}
.data-table td{padding:11px 14px;border-bottom:1px solid rgba(34,41,58,.5);color:var(--text);}
.data-table tr:last-child td{border:none;}
.data-table tr:hover td{background:var(--surface2);}
.badge{display:inline-block;padding:3px 9px;border-radius:4px;font-size:10px;font-family:var(--font-mono);font-weight:700;}
.badge-green{background:rgba(0,229,160,.15);color:var(--green);}
.badge-red{background:rgba(255,77,109,.15);color:var(--red);}
.badge-yellow{background:rgba(255,209,102,.12);color:var(--yellow);}
.badge-blue{background:rgba(78,156,255,.12);color:var(--accent3);}

/* RELIABILITY BARS */
.rel-bar-wrap{margin-bottom:14px;}
.rel-bar-top{display:flex;justify-content:space-between;margin-bottom:5px;font-size:12px;}
.rel-bar-name{font-weight:600;}
.rel-bar-val{font-family:var(--font-mono);color:var(--muted);}
.rel-bar-bg{height:8px;background:var(--surface2);border-radius:4px;overflow:hidden;}
.rel-bar-fill{height:100%;border-radius:4px;transition:width 1s ease;}

/* CHART CONTAINER */
.chart-wrap{position:relative;padding:20px;}
.chart-wrap canvas{max-height:280px;}

/* HEATMAP */
.heatmap{display:grid;gap:4px;font-size:10px;font-family:var(--font-mono);}
.hm-cell{
  padding:8px 4px;border-radius:6px;text-align:center;cursor:default;
  font-weight:700;transition:.2s;font-size:11px;
}
.hm-cell:hover{transform:scale(1.08);}
.hm-header{color:var(--muted);font-weight:400;background:transparent!important;}

/* INSIGHTS */
.insight{display:flex;gap:12px;padding:14px;background:var(--surface2);border-radius:10px;margin-bottom:10px;border-left:3px solid var(--insight-color,var(--accent));}
.insight-icon{font-size:18px;flex-shrink:0;}
.insight-text{font-size:12px;line-height:1.6;color:var(--text);}
.insight-text strong{color:var(--insight-color,var(--accent));}

/* GAUGE */
.gauge-wrap{display:flex;flex-direction:column;align-items:center;padding:20px;}
.gauge-svg{overflow:visible;}
.gauge-value{font-size:28px;font-weight:800;font-family:var(--font-mono);}
.gauge-label{font-size:11px;color:var(--muted);margin-top:4px;font-family:var(--font-mono);}

/* PHASE TIMELINE */
.timeline{position:relative;padding-left:28px;}
.timeline::before{content:'';position:absolute;left:10px;top:0;bottom:0;width:2px;background:var(--border);}
.tl-item{position:relative;margin-bottom:20px;}
.tl-dot{
  position:absolute;left:-22px;top:4px;
  width:12px;height:12px;border-radius:50%;
  background:var(--tl-color,var(--muted));border:2px solid var(--bg);
}
.tl-item.done .tl-dot{background:var(--green);}
.tl-item.active .tl-dot{background:var(--accent);box-shadow:0 0 0 4px rgba(0,229,160,.2);}
.tl-date{font-size:10px;font-family:var(--font-mono);color:var(--muted);margin-bottom:3px;}
.tl-title{font-size:13px;font-weight:700;}
.tl-desc{font-size:11px;color:var(--muted);margin-top:2px;line-height:1.5;}

/* RELIABILITY METRICS SECTION */
.metric-big{text-align:center;padding:24px 16px;}
.metric-big .val{font-size:48px;font-weight:800;font-family:var(--font-mono);letter-spacing:-.04em;}
.metric-big .unit{font-size:16px;color:var(--muted);}
.metric-big .lbl{font-size:11px;color:var(--muted);margin-top:6px;font-family:var(--font-mono);text-transform:uppercase;letter-spacing:.1em;}
.metric-big .sub{font-size:11px;color:var(--muted);margin-top:8px;line-height:1.5;max-width:160px;margin-inline:auto;}

.divider{height:1px;background:var(--border);margin:24px 0;}
.formula-box{
  background:var(--surface2);border:1px solid var(--border);
  border-radius:8px;padding:14px 18px;
  font-family:var(--font-mono);font-size:12px;color:var(--accent);
  margin-bottom:16px;
}
.formula-box span{color:var(--muted);}

/* RESPONSIVE */
@media(max-width:600px){
  nav{padding:12px 16px;flex-wrap:wrap;gap:8px;}
  main{padding:16px;}
  .kpi-value{font-size:24px;}
}
</style>
</head>
<body>

<nav>
  <div class="nav-logo">
    <div class="badge">CMMS</div>
    <div>
      <div class="nav-title">Sistema de Información de Mantenimiento</div>
      <div class="nav-sub">Electiva Profundización I · Universidad ECCI · 2026-1</div>
    </div>
  </div>
  <div class="nav-tabs">
    <button class="tab-btn active" onclick="showPage('dashboard')">Dashboard</button>
    <button class="tab-btn" onclick="showPage('confiabilidad')">Confiabilidad</button>
    <button class="tab-btn" onclick="showPage('ordenes')">Órdenes de Trabajo</button>
    <button class="tab-btn" onclick="showPage('equipos')">Equipos</button>
    <button class="tab-btn" onclick="showPage('fases')">Fases</button>
  </div>
  <div class="nav-right">HOY: 23-ABR-2026</div>
</nav>

<main>

<!-- ══════════════════ DASHBOARD ══════════════════ -->
<div id="page-dashboard" class="page active">
  <div class="section-header">
    <h2>Resumen Ejecutivo</h2>
    <p>Planta Hipotética · Indicadores clave de mantenimiento · Abril 2026</p>
  </div>

  <div class="kpi-grid">
    <div class="kpi-card" style="--kpi-color:#00e5a0">
      <div class="kpi-label">Disponibilidad</div>
      <div class="kpi-value">89.4<span class="kpi-unit">%</span></div>
      <div class="kpi-delta up">↑ +2.1% vs mes ant.</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#4e9cff">
      <div class="kpi-label">MTTR Promedio</div>
      <div class="kpi-value">4.2<span class="kpi-unit">h</span></div>
      <div class="kpi-delta up">↓ −0.8h mejor</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ffd166">
      <div class="kpi-label">MTTF Promedio</div>
      <div class="kpi-value">34.6<span class="kpi-unit">h</span></div>
      <div class="kpi-delta up">↑ +3.2h vs meta</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ff6b35">
      <div class="kpi-label">% Cumpl. OT</div>
      <div class="kpi-value">82.3<span class="kpi-unit">%</span></div>
      <div class="kpi-delta neutral">→ Meta: 90%</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ff4d6d">
      <div class="kpi-label">OT Abiertas</div>
      <div class="kpi-value">14<span class="kpi-unit">OT</span></div>
      <div class="kpi-delta down">↑ +3 críticas</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#a78bfa">
      <div class="kpi-label">Costo Repuestos</div>
      <div class="kpi-value">$4.7<span class="kpi-unit">M</span></div>
      <div class="kpi-delta neutral">→ Ppto: $5.0M</div>
    </div>
  </div>

  <div class="grid-2-1">
    <div class="card">
      <div class="card-header"><h3>📈 Disponibilidad Mensual por Equipo</h3><span class="card-tag">FY2025-2026</span></div>
      <div class="chart-wrap"><canvas id="trendChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>🔍 Hallazgos Automáticos</h3></div>
      <div class="card-body">
        <div class="insight" style="--insight-color:#ff4d6d">
          <span class="insight-icon">🚨</span>
          <div class="insight-text"><strong>Compresor C-101</strong> muestra MTTR de 7.1h — 69% sobre la meta. Revisar causa raíz.</div>
        </div>
        <div class="insight" style="--insight-color:#ffd166">
          <span class="insight-icon">⚠️</span>
          <div class="insight-text"><strong>Bomba P-204</strong> presenta tendencia decreciente de disponibilidad: −5.2% en 3 meses.</div>
        </div>
        <div class="insight" style="--insight-color:#00e5a0">
          <span class="insight-icon">✅</span>
          <div class="insight-text"><strong>Turbina T-01</strong> supera la meta de disponibilidad con 96.1% — mejor equipo del mes.</div>
        </div>
        <div class="insight" style="--insight-color:#4e9cff">
          <span class="insight-icon">💡</span>
          <div class="insight-text"><strong>14 OT pendientes</strong>: 3 críticas (prioridad 1). Planner debe reasignar técnicos esta semana.</div>
        </div>
        <div class="insight" style="--insight-color:#a78bfa">
          <span class="insight-icon">📦</span>
          <div class="insight-text">Stock de <strong>rodamientos SKF</strong> en nivel mínimo (2 unidades). Generar orden de compra.</div>
        </div>
      </div>
    </div>
  </div>

  <div class="grid-2">
    <div class="card">
      <div class="card-header"><h3>📊 Disponibilidad por Equipo (Promedio)</h3></div>
      <div class="chart-wrap"><canvas id="barChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>🔥 Mapa de Calor · Disponibilidad % Equipo × Mes</h3></div>
      <div class="card-body" id="heatmapContainer" style="padding:12px;"></div>
    </div>
  </div>
</div>

<!-- ══════════════════ CONFIABILIDAD ══════════════════ -->
<div id="page-confiabilidad" class="page">
  <div class="section-header">
    <h2>Indicadores de Confiabilidad</h2>
    <p>MTTR · MTTF · Disponibilidad calculada · Datos hipotéticos para actividad académica</p>
  </div>

  <div class="formula-box">
    <span>// Fórmulas base de confiabilidad</span><br>
    Disponibilidad (%) = MTTF / (MTTF + MTTR) × 100<br>
    MTTR = Tiempo Total de Reparación / N° de Fallas<br>
    MTTF = Tiempo Total de Operación / N° de Fallas
  </div>

  <div class="grid-3" style="margin-bottom:20px;">
    <div class="card" style="--kpi-color:#4e9cff">
      <div class="metric-big">
        <div class="val" style="color:var(--accent3)">4.2<span style="font-size:20px;color:var(--muted)">h</span></div>
        <div class="lbl">MTTR Global</div>
        <div class="sub">Tiempo Medio para Reparar · Promedio flota completa</div>
      </div>
    </div>
    <div class="card">
      <div class="metric-big">
        <div class="val" style="color:var(--yellow)">34.6<span style="font-size:20px;color:var(--muted)">h</span></div>
        <div class="lbl">MTTF Global</div>
        <div class="sub">Tiempo Medio Entre Fallas · Promedio flota completa</div>
      </div>
    </div>
    <div class="card">
      <div class="metric-big">
        <div class="val" style="color:var(--green)">89.4<span style="font-size:20px;color:var(--muted)">%</span></div>
        <div class="lbl">Disponibilidad</div>
        <div class="sub">MTTF/(MTTF+MTTR) · Meta: 92%</div>
      </div>
    </div>
  </div>

  <!-- Tabla detalle MTTR MTTF por equipo -->
  <div class="card" style="margin-bottom:20px;">
    <div class="card-header"><h3>📋 MTTR & MTTF por Equipo · Datos Hipotéticos</h3><span class="card-tag">ABR 2026</span></div>
    <div style="overflow-x:auto;">
      <table class="data-table" id="reliabilityTable"></table>
    </div>
  </div>

  <div class="grid-2">
    <div class="card">
      <div class="card-header"><h3>📉 MTTR por Equipo (horas)</h3><span class="card-tag">Meta ≤ 4h</span></div>
      <div class="chart-wrap"><canvas id="mttrChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>📈 MTTF por Equipo (horas)</h3><span class="card-tag">Meta ≥ 30h</span></div>
      <div class="chart-wrap"><canvas id="mttfChart"></canvas></div>
    </div>
  </div>

  <div class="card" style="margin-bottom:20px;">
    <div class="card-header"><h3>🎯 Disponibilidad Calculada por Equipo</h3><span class="card-tag">Línea roja = meta 92%</span></div>
    <div class="chart-wrap"><canvas id="dispChart"></canvas></div>
  </div>

  <div class="card">
    <div class="card-header"><h3>📊 Barras de Confiabilidad por Equipo</h3></div>
    <div class="card-body" id="relBarsContainer"></div>
  </div>
</div>

<!-- ══════════════════ ÓRDENES DE TRABAJO ══════════════════ -->
<div id="page-ordenes" class="page">
  <div class="section-header">
    <h2>Órdenes de Trabajo (OT)</h2>
    <p>Registro de actividades de mantenimiento · Módulo 2 de la actividad final</p>
  </div>

  <div class="kpi-grid" style="grid-template-columns:repeat(4,1fr);">
    <div class="kpi-card" style="--kpi-color:#00e5a0">
      <div class="kpi-label">OT Cerradas</div>
      <div class="kpi-value">47</div>
      <div class="kpi-delta up">↑ Este mes</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ffd166">
      <div class="kpi-label">OT En Proceso</div>
      <div class="kpi-value">11</div>
      <div class="kpi-delta neutral">→ Prog. esta sem.</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ff4d6d">
      <div class="kpi-label">OT Críticas Abiertas</div>
      <div class="kpi-value">3</div>
      <div class="kpi-delta down">↑ Requiere acción</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#4e9cff">
      <div class="kpi-label">% Cumplimiento OT</div>
      <div class="kpi-value">82.3<span class="kpi-unit">%</span></div>
      <div class="kpi-delta neutral">→ Meta 90%</div>
    </div>
  </div>

  <div class="grid-2" style="margin-bottom:20px;">
    <div class="card">
      <div class="card-header"><h3>🍩 Tipos de Mantenimiento</h3></div>
      <div class="chart-wrap"><canvas id="tipoOTChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>📅 OT por Mes · Cumplimiento</h3></div>
      <div class="chart-wrap"><canvas id="cumplOTChart"></canvas></div>
    </div>
  </div>

  <div class="card">
    <div class="card-header"><h3>📋 Registro de Órdenes de Trabajo</h3><span class="card-tag">Últimas 15 OT</span></div>
    <div style="overflow-x:auto;">
      <table class="data-table" id="otTable"></table>
    </div>
  </div>
</div>

<!-- ══════════════════ EQUIPOS ══════════════════ -->
<div id="page-equipos" class="page">
  <div class="section-header">
    <h2>Administración de Equipos</h2>
    <p>Inventario, criticidad y estado · Módulo 1 de la actividad final</p>
  </div>

  <div class="grid-2" style="margin-bottom:20px;">
    <div class="card">
      <div class="card-header"><h3>🏭 Equipos por Criticidad</h3></div>
      <div class="chart-wrap"><canvas id="criticidadChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>⚙️ Estado Operativo de la Flota</h3></div>
      <div class="chart-wrap"><canvas id="estadoChart"></canvas></div>
    </div>
  </div>

  <div class="card">
    <div class="card-header"><h3>📋 Inventario de Equipos</h3><span class="card-tag">Módulo 1</span></div>
    <div style="overflow-x:auto;">
      <table class="data-table" id="equiposTable"></table>
    </div>
  </div>
</div>

<!-- ══════════════════ FASES ══════════════════ -->
<div id="page-fases" class="page">
  <div class="section-header">
    <h2>Plan de Trabajo · Fases del Proyecto</h2>
    <p>Actividad Final · Electiva Profundización I · Prof. María Andrea Ramírez Morales</p>
  </div>

  <div class="grid-2">
    <div class="card">
      <div class="card-header"><h3>📅 Cronograma de Fases</h3></div>
      <div class="card-body">
        <div class="timeline">
          <div class="tl-item done">
            <div class="tl-dot"></div>
            <div class="tl-date">JUE 23-ABR-2026 · HOY ✓</div>
            <div class="tl-title">Fase 1 · Definición del Sistema</div>
            <div class="tl-desc">Objetivo del sistema, problemas a resolver, usuarios (técnico, planner, jefe).</div>
          </div>
          <div class="tl-item active">
            <div class="tl-dot"></div>
            <div class="tl-date">SEM 28–30 ABR 2026</div>
            <div class="tl-title">Fase 2 · Diseño de Módulos (Excel)</div>
            <div class="tl-desc">Equipos · OT · Personal · Materiales · Control de actividades.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot"></div>
            <div class="tl-date">SEM 5–7 MAY 2026</div>
            <div class="tl-title">Fase 3 · Integración del Sistema</div>
            <div class="tl-desc">Relacionar tablas: OT↔Equipos · Técnicos asignados · Consumo de repuestos.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot"></div>
            <div class="tl-date">SEM 12–14 MAY 2026</div>
            <div class="tl-title">Fase 4 · Indicadores KPI</div>
            <div class="tl-desc">% Cumplimiento OT · MTTR · Disponibilidad. Dashboard visual atractivo.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot"></div>
            <div class="tl-date">SEM 26–28 MAY 2026</div>
            <div class="tl-title">Fase 5 · Análisis</div>
            <div class="tl-desc">A) Problemas resueltos B) Decisiones posibles C) Limitaciones vs CMMS D) Mejoras propuestas.</div>
          </div>
        </div>
      </div>
    </div>

    <div>
      <div class="card" style="margin-bottom:20px;">
        <div class="card-header"><h3>🎯 Criterios de Evaluación</h3><span class="card-tag">100%</span></div>
        <div class="card-body">
          <div id="evalBars"></div>
        </div>
      </div>

      <div class="card">
        <div class="card-header"><h3>📦 Módulos del Sistema</h3></div>
        <div class="card-body" style="display:grid;gap:10px;">
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">⚙️</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 1 · Equipos</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">ID · Equipo · Ubicación · Estado · F. instalación · Criticidad</div></div>
          </div>
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">📋</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 2 · Órdenes de Trabajo</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">ID OT · Equipo · Fecha · Tipo · Falla · Técnico · Tiempo · Estado</div></div>
          </div>
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">👷</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 3 · Personal</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">ID · Nombre · Especialidad · Turno · Experiencia</div></div>
          </div>
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">🔩</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 4 · Materiales</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">Código · Repuesto · Stock · Consumo · Costo</div></div>
          </div>
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">📊</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 5 · Control Actividades</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">OT · Actividad · T. planificado · T. real · Cumplimiento</div></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

</main>

<script>
// ── DATA ───────────────────────────────────────────────────────────────────
const equipos = [
  {id:'EQ-001',nombre:'Compresor C-101',ubicacion:'Planta A',estado:'Operativo',instalacion:'2019-03-15',criticidad:'Alta',
   mttr:7.1,mttf:28.4,fallas:12,t_rep:85.2,t_op:340.8},
  {id:'EQ-002',nombre:'Bomba P-204',ubicacion:'Planta B',estado:'Operativo',instalacion:'2020-07-22',criticidad:'Alta',
   mttr:3.8,mttf:31.2,fallas:10,t_rep:38,t_op:312},
  {id:'EQ-003',nombre:'Turbina T-01',ubicacion:'Planta A',estado:'Operativo',instalacion:'2018-11-10',criticidad:'Crítica',
   mttr:2.1,mttf:50.3,fallas:6,t_rep:12.6,t_op:301.8},
  {id:'EQ-004',nombre:'Motor M-302',ubicacion:'Planta C',estado:'En Mantenimiento',instalacion:'2021-01-08',criticidad:'Media',
   mttr:4.5,mttf:33.6,fallas:8,t_rep:36,t_op:268.8},
  {id:'EQ-005',nombre:'Agitador AG-07',ubicacion:'Planta B',estado:'Operativo',instalacion:'2022-05-17',criticidad:'Baja',
   mttr:2.8,mttf:42.0,fallas:5,t_rep:14,t_op:210},
  {id:'EQ-006',nombre:'Caldera CA-02',ubicacion:'Planta A',estado:'Operativo',instalacion:'2017-09-30',criticidad:'Crítica',
   mttr:5.2,mttf:29.8,fallas:9,t_rep:46.8,t_op:268.2},
  {id:'EQ-007',nombre:'Banda BT-55',ubicacion:'Planta C',estado:'Fuera de Servicio',instalacion:'2020-03-12',criticidad:'Media',
   mttr:6.0,mttf:22.0,fallas:11,t_rep:66,t_op:242},
];

const meses = ['Jul','Ago','Sep','Oct','Nov','Dic','Ene','Feb','Mar','Abr'];
const disponibilidadMensual = {
  'Compresor C-101': [80,82,78,75,77,79,81,80,82,80],
  'Bomba P-204':     [88,87,86,84,83,82,85,84,83,89],
  'Turbina T-01':    [95,96,97,96,95,96,97,96,95,96],
  'Motor M-302':     [91,90,89,88,87,88,89,88,87,86],
  'Caldera CA-02':   [85,84,83,82,81,83,84,85,84,83],
};

const OTs = [
  {id:'OT-0041',equipo:'Compresor C-101',fecha:'2026-04-20',tipo:'Correctivo',falla:'Vibración excesiva',actividad:'Cambio rodamiento',tecnico:'J. Pérez',tiempo:8,estado:'Cerrada'},
  {id:'OT-0042',equipo:'Bomba P-204',fecha:'2026-04-21',tipo:'Preventivo',falla:'Mantenimiento prog.',actividad:'Cambio sellos',tecnico:'M. Torres',tiempo:3,estado:'Cerrada'},
  {id:'OT-0043',equipo:'Turbina T-01',fecha:'2026-04-22',tipo:'Predictivo',falla:'Análisis vibración',actividad:'Monitoreo',tecnico:'A. Gómez',tiempo:2,estado:'Cerrada'},
  {id:'OT-0044',equipo:'Motor M-302',fecha:'2026-04-22',tipo:'Correctivo',falla:'Sobrecalentamiento',actividad:'Revisión bobinado',tecnico:'J. Pérez',tiempo:6,estado:'En Proceso'},
  {id:'OT-0045',equipo:'Caldera CA-02',fecha:'2026-04-23',tipo:'Correctivo',falla:'Fuga vapor',actividad:'Cambio empaque',tecnico:'C. Ríos',tiempo:5,estado:'Abierta'},
  {id:'OT-0046',equipo:'Banda BT-55',fecha:'2026-04-23',tipo:'Correctivo',falla:'Banda rota',actividad:'Reemplazo banda',tecnico:'M. Torres',tiempo:7,estado:'Abierta'},
  {id:'OT-0047',equipo:'Agitador AG-07',fecha:'2026-04-19',tipo:'Preventivo',falla:'PM programado',actividad:'Lubricación general',tecnico:'A. Gómez',tiempo:2,estado:'Cerrada'},
  {id:'OT-0048',equipo:'Compresor C-101',fecha:'2026-04-18',tipo:'Correctivo',falla:'Presión baja',actividad:'Ajuste válvulas',tecnico:'C. Ríos',tiempo:4,estado:'Cerrada'},
  {id:'OT-0049',equipo:'Bomba P-204',fecha:'2026-04-17',tipo:'Correctivo',falla:'Ruido anormal',actividad:'Revisión impelente',tecnico:'J. Pérez',tiempo:5,estado:'Cerrada'},
  {id:'OT-0050',equipo:'Caldera CA-02',fecha:'2026-04-23',tipo:'Correctivo',falla:'Quemador falla',actividad:'Limpieza quemador',tecnico:'A. Gómez',tiempo:6,estado:'Abierta'},
  {id:'OT-0051',equipo:'Motor M-302',fecha:'2026-04-16',tipo:'Preventivo',falla:'PM mensual',actividad:'Limpieza y ajuste',tecnico:'M. Torres',tiempo:2,estado:'Cerrada'},
  {id:'OT-0052',equipo:'Turbina T-01',fecha:'2026-04-15',tipo:'Predictivo',falla:'Termografía',actividad:'Inspección IR',tecnico:'C. Ríos',tiempo:1,estado:'Cerrada'},
  {id:'OT-0053',equipo:'Agitador AG-07',fecha:'2026-04-14',tipo:'Correctivo',falla:'Motor sobrecarga',actividad:'Revisión protección',tecnico:'J. Pérez',tiempo:3,estado:'Cerrada'},
  {id:'OT-0054',equipo:'Banda BT-55',fecha:'2026-04-23',tipo:'Correctivo',falla:'Rodillo dañado',actividad:'Cambio rodillo',tecnico:'M. Torres',tiempo:4,estado:'En Proceso'},
  {id:'OT-0055',equipo:'Compresor C-101',fecha:'2026-04-23',tipo:'Predictivo',falla:'Análisis aceite',actividad:'Toma muestra aceite',tecnico:'A. Gómez',tiempo:1,estado:'En Proceso'},
];

// ── NAVIGATION ─────────────────────────────────────────────────────────────
function showPage(id){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  event.target.classList.add('active');
  // lazy init charts
  if(id==='confiabilidad' && !window._confInit){window._confInit=true;initConfiabilidad();}
  if(id==='ordenes' && !window._otInit){window._otInit=true;initOrdenes();}
  if(id==='equipos' && !window._eqInit){window._eqInit=true;initEquipos();}
  if(id==='fases' && !window._fasesInit){window._fasesInit=true;initFases();}
}

// ── COLORS ─────────────────────────────────────────────────────────────────
const COLORS=['#00e5a0','#4e9cff','#ffd166','#ff6b35','#a78bfa','#ff4d6d','#06d6a0'];
function alpha(hex,a){const r=parseInt(hex.slice(1,3),16),g=parseInt(hex.slice(3,5),16),b=parseInt(hex.slice(5,7),16);return `rgba(${r},${g},${b},${a})`;}

const CHART_DEFAULTS={
  color:'#7b8ab8',
  plugins:{legend:{labels:{color:'#7b8ab8',font:{family:"'Space Mono',monospace",size:11}}},tooltip:{backgroundColor:'#111318',borderColor:'#22293a',borderWidth:1,titleColor:'#eef2ff',bodyColor:'#7b8ab8'}},
  scales:{x:{grid:{color:'rgba(34,41,58,.5)'},ticks:{color:'#7b8ab8',font:{family:"'Space Mono',monospace",size:10}}},y:{grid:{color:'rgba(34,41,58,.5)'},ticks:{color:'#7b8ab8',font:{family:"'Space Mono',monospace",size:10}}}}
};
function mergeOpts(extra={}){return {...CHART_DEFAULTS,...extra,plugins:{...CHART_DEFAULTS.plugins,...(extra.plugins||{})},scales:{...CHART_DEFAULTS.scales,...(extra.scales||{})}};}

// ── DASHBOARD CHARTS ───────────────────────────────────────────────────────
const equipNames=Object.keys(disponibilidadMensual);
new Chart(document.getElementById('trendChart'),{
  type:'line',
  data:{labels:meses,datasets:equipNames.map((e,i)=>({
    label:e,data:disponibilidadMensual[e],borderColor:COLORS[i],
    backgroundColor:alpha(COLORS[i],.08),tension:.4,pointRadius:3,pointHoverRadius:5,fill:false
  }))},
  options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,min:70,max:100,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'%'}}}})
});

new Chart(document.getElementById('barChart'),{
  type:'bar',
  data:{
    labels:equipos.map(e=>e.nombre.split(' ')[0]+' '+e.nombre.split(' ')[1]),
    datasets:[{
      label:'Disponibilidad %',
      data:equipos.map(e=>+(e.mttf/(e.mttf+e.mttr)*100).toFixed(1)),
      backgroundColor:equipos.map((e,i)=>alpha(COLORS[i],.7)),
      borderColor:equipos.map((_,i)=>COLORS[i]),borderWidth:1,borderRadius:6
    }]
  },
  options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,min:60,max:100,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'%'}}}})
});

// HEATMAP
function buildHeatmap(){
  const cont=document.getElementById('heatmapContainer');
  const eqKeys=Object.keys(disponibilidadMensual);
  const cols=meses.length+1;
  const hm=document.createElement('div');
  hm.className='heatmap';
  hm.style.gridTemplateColumns=`120px repeat(${meses.length},1fr)`;

  // header
  const headerEq=document.createElement('div');headerEq.className='hm-cell hm-header';headerEq.textContent='Equipo';hm.appendChild(headerEq);
  meses.forEach(m=>{const c=document.createElement('div');c.className='hm-cell hm-header';c.textContent=m;hm.appendChild(c);});

  eqKeys.forEach((eq,i)=>{
    const label=document.createElement('div');
    label.className='hm-cell';label.style.color='var(--muted)';label.style.fontSize='10px';label.style.textAlign='left';
    label.textContent=eq.split(' ')[0];hm.appendChild(label);
    disponibilidadMensual[eq].forEach(v=>{
      const c=document.createElement('div');c.className='hm-cell';
      const norm=(v-70)/30;
      const r=Math.round(255-norm*255),g=Math.round(norm*229),b=Math.round(norm*100);
      c.style.background=`rgba(${r},${g},${b},0.7)`;
      c.style.color=v>85?'#000':'#fff';
      c.textContent=v;c.title=eq+' '+meses[0]+': '+v+'%';
      hm.appendChild(c);
    });
  });
  cont.appendChild(hm);
}
buildHeatmap();

// ── CONFIABILIDAD ──────────────────────────────────────────────────────────
function initConfiabilidad(){
  // Table
  const tbl=document.getElementById('reliabilityTable');
  const heads=['ID','Equipo','Fallas','T. Rep (h)','MTTR (h)','T. Op (h)','MTTF (h)','Disponibilidad','Estado'];
  tbl.innerHTML=`<thead><tr>${heads.map(h=>`<th>${h}</th>`).join('')}</tr></thead>`;
  const tbody=document.createElement('tbody');
  equipos.forEach((e,i)=>{
    const disp=(e.mttf/(e.mttf+e.mttr)*100).toFixed(1);
    const dispOk=disp>=90,dispWarn=disp>=80&&disp<90;
    const mttrOk=e.mttr<=4,mttrWarn=e.mttr<=6&&e.mttr>4;
    const tr=document.createElement('tr');
    tr.innerHTML=`
      <td><span style="font-family:var(--font-mono);color:var(--muted)">${e.id}</span></td>
      <td><b>${e.nombre}</b></td>
      <td style="font-family:var(--font-mono)">${e.fallas}</td>
      <td style="font-family:var(--font-mono)">${e.t_rep.toFixed(1)}</td>
      <td><span class="badge ${mttrOk?'badge-green':mttrWarn?'badge-yellow':'badge-red'}">${e.mttr.toFixed(1)}h</span></td>
      <td style="font-family:var(--font-mono)">${e.t_op.toFixed(1)}</td>
      <td><span class="badge badge-blue">${e.mttf.toFixed(1)}h</span></td>
      <td><span class="badge ${dispOk?'badge-green':dispWarn?'badge-yellow':'badge-red'}">${disp}%</span></td>
      <td><span class="badge ${e.estado==='Operativo'?'badge-green':e.estado==='En Mantenimiento'?'badge-yellow':'badge-red'}">${e.estado}</span></td>`;
    tbody.appendChild(tr);
  });
  tbl.appendChild(tbody);

  // MTTR chart
  new Chart(document.getElementById('mttrChart'),{
    type:'bar',
    data:{
      labels:equipos.map(e=>e.id),
      datasets:[
        {label:'MTTR (h)',data:equipos.map(e=>e.mttr),backgroundColor:equipos.map(e=>e.mttr<=4?alpha('#00e5a0',.7):e.mttr<=6?alpha('#ffd166',.7):alpha('#ff4d6d',.7)),borderColor:equipos.map(e=>e.mttr<=4?'#00e5a0':e.mttr<=6?'#ffd166':'#ff4d6d'),borderWidth:1,borderRadius:6},
        {label:'Meta (4h)',data:Array(equipos.length).fill(4),type:'line',borderColor:'#ff4d6d',borderDash:[5,5],pointRadius:0,borderWidth:1.5}
      ]
    },
    options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'h'}}}})
  });

  // MTTF chart
  new Chart(document.getElementById('mttfChart'),{
    type:'bar',
    data:{
      labels:equipos.map(e=>e.id),
      datasets:[
        {label:'MTTF (h)',data:equipos.map(e=>e.mttf),backgroundColor:equipos.map(e=>e.mttf>=40?alpha('#00e5a0',.7):e.mttf>=28?alpha('#ffd166',.7):alpha('#ff4d6d',.7)),borderColor:equipos.map(e=>e.mttf>=40?'#00e5a0':e.mttf>=28?'#ffd166':'#ff4d6d'),borderWidth:1,borderRadius:6},
        {label:'Meta (30h)',data:Array(equipos.length).fill(30),type:'line',borderColor:'#4e9cff',borderDash:[5,5],pointRadius:0,borderWidth:1.5}
      ]
    },
    options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'h'}}}})
  });

  // Disponibilidad calculada
  const dispVals=equipos.map(e=>+(e.mttf/(e.mttf+e.mttr)*100).toFixed(1));
  new Chart(document.getElementById('dispChart'),{
    type:'bar',
    data:{
      labels:equipos.map(e=>e.id),
      datasets:[
        {label:'Disponibilidad %',data:dispVals,backgroundColor:dispVals.map(v=>v>=90?alpha('#00e5a0',.7):v>=80?alpha('#ffd166',.7):alpha('#ff4d6d',.7)),borderRadius:6},
        {label:'Meta 92%',data:Array(equipos.length).fill(92),type:'line',borderColor:'#ff4d6d',borderDash:[6,4],pointRadius:0,borderWidth:1.5}
      ]
    },
    options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,min:60,max:100,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'%'}}}})
  });

  // Reliability bars
  const relCont=document.getElementById('relBarsContainer');
  equipos.forEach((e,i)=>{
    const disp=(e.mttf/(e.mttf+e.mttr)*100).toFixed(1);
    const color=disp>=90?'#00e5a0':disp>=80?'#ffd166':'#ff4d6d';
    relCont.innerHTML+=`
      <div class="rel-bar-wrap">
        <div class="rel-bar-top"><span class="rel-bar-name">${e.nombre}</span><span class="rel-bar-val">${disp}% · MTTF ${e.mttf}h · MTTR ${e.mttr}h</span></div>
        <div class="rel-bar-bg"><div class="rel-bar-fill" style="width:${disp}%;background:${color}"></div></div>
      </div>`;
  });
}

// ── ÓRDENES ───────────────────────────────────────────────────────────────
function initOrdenes(){
  // Tipo donut
  const tipos={Correctivo:0,Preventivo:0,Predictivo:0};
  OTs.forEach(o=>tipos[o.tipo]=(tipos[o.tipo]||0)+1);
  new Chart(document.getElementById('tipoOTChart'),{
    type:'doughnut',
    data:{labels:Object.keys(tipos),datasets:[{data:Object.values(tipos),backgroundColor:[alpha('#ff4d6d',.8),alpha('#00e5a0',.8),alpha('#4e9cff',.8)],borderColor:'#111318',borderWidth:3}]},
    options:{...CHART_DEFAULTS,scales:{},cutout:'65%',plugins:{...CHART_DEFAULTS.plugins}}
  });

  // Cumplimiento mensual
  const cumplData=[72,78,75,80,83,85,80,82,84,82];
  new Chart(document.getElementById('cumplOTChart'),{
    type:'line',
    data:{labels:meses,datasets:[
      {label:'% Cumplimiento',data:cumplData,borderColor:'#00e5a0',backgroundColor:alpha('#00e5a0',.1),fill:true,tension:.4,pointRadius:4},
      {label:'Meta 90%',data:Array(10).fill(90),borderColor:'#ff4d6d',borderDash:[6,4],pointRadius:0,borderWidth:1.5}
    ]},
    options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,min:60,max:100,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'%'}}}})
  });

  // Table
  const tbl=document.getElementById('otTable');
  const heads=['ID OT','Equipo','Fecha','Tipo','Falla','Actividad','Técnico','Tiempo','Estado'];
  tbl.innerHTML=`<thead><tr>${heads.map(h=>`<th>${h}</th>`).join('')}</tr></thead>`;
  const tbody=document.createElement('tbody');
  OTs.forEach(o=>{
    const sc=o.estado==='Cerrada'?'badge-green':o.estado==='En Proceso'?'badge-yellow':'badge-red';
    const tc=o.tipo==='Correctivo'?'badge-red':o.tipo==='Preventivo'?'badge-green':'badge-blue';
    const tr=document.createElement('tr');
    tr.innerHTML=`<td><b style="font-family:var(--font-mono)">${o.id}</b></td><td>${o.equipo}</td><td style="font-family:var(--font-mono)">${o.fecha}</td><td><span class="badge ${tc}">${o.tipo}</span></td><td style="font-size:11px;color:var(--muted)">${o.falla}</td><td style="font-size:11px">${o.actividad}</td><td>${o.tecnico}</td><td style="font-family:var(--font-mono)">${o.tiempo}h</td><td><span class="badge ${sc}">${o.estado}</span></td>`;
    tbody.appendChild(tr);
  });
  tbl.appendChild(tbody);
}

// ── EQUIPOS ───────────────────────────────────────────────────────────────
function initEquipos(){
  const crit={Alta:0,Crítica:0,Media:0,Baja:0};
  const est={Operativo:0,'En Mantenimiento':0,'Fuera de Servicio':0};
  equipos.forEach(e=>{crit[e.criticidad]=(crit[e.criticidad]||0)+1;est[e.estado]=(est[e.estado]||0)+1;});

  new Chart(document.getElementById('criticidadChart'),{
    type:'doughnut',
    data:{labels:Object.keys(crit),datasets:[{data:Object.values(crit),backgroundColor:[alpha('#ff6b35',.8),alpha('#ff4d6d',.8),alpha('#ffd166',.8),alpha('#00e5a0',.8)],borderColor:'#111318',borderWidth:3}]},
    options:{...CHART_DEFAULTS,scales:{},cutout:'60%',plugins:{...CHART_DEFAULTS.plugins}}
  });

  new Chart(document.getElementById('estadoChart'),{
    type:'doughnut',
    data:{labels:Object.keys(est),datasets:[{data:Object.values(est),backgroundColor:[alpha('#00e5a0',.8),alpha('#ffd166',.8),alpha('#ff4d6d',.8)],borderColor:'#111318',borderWidth:3}]},
    options:{...CHART_DEFAULTS,scales:{},cutout:'60%',plugins:{...CHART_DEFAULTS.plugins}}
  });

  const tbl=document.getElementById('equiposTable');
  const heads=['ID','Equipo','Ubicación','Estado','F. Instalación','Criticidad','MTTR','MTTF','Disp.'];
  tbl.innerHTML=`<thead><tr>${heads.map(h=>`<th>${h}</th>`).join('')}</tr></thead>`;
  const tbody=document.createElement('tbody');
  equipos.forEach(e=>{
    const disp=(e.mttf/(e.mttf+e.mttr)*100).toFixed(1);
    const sc=e.estado==='Operativo'?'badge-green':e.estado==='En Mantenimiento'?'badge-yellow':'badge-red';
    const cc=e.criticidad==='Crítica'?'badge-red':e.criticidad==='Alta'?'badge-yellow':e.criticidad==='Media'?'badge-blue':'badge-green';
    const tr=document.createElement('tr');
    tr.innerHTML=`<td><b style="font-family:var(--font-mono)">${e.id}</b></td><td><b>${e.nombre}</b></td><td style="color:var(--muted)">${e.ubicacion}</td><td><span class="badge ${sc}">${e.estado}</span></td><td style="font-family:var(--font-mono);font-size:11px">${e.instalacion}</td><td><span class="badge ${cc}">${e.criticidad}</span></td><td style="font-family:var(--font-mono)">${e.mttr}h</td><td style="font-family:var(--font-mono)">${e.mttf}h</td><td><span class="badge ${+disp>=90?'badge-green':+disp>=80?'badge-yellow':'badge-red'}">${disp}%</span></td>`;
    tbody.appendChild(tr);
  });
  tbl.appendChild(tbody);
}

// ── FASES ─────────────────────────────────────────────────────────────────
function initFases(){
  const criterios=[
    {nombre:'Diseño del Sistema',pct:20,color:'#00e5a0'},
    {nombre:'Uso de Excel',pct:20,color:'#4e9cff'},
    {nombre:'Indicadores KPI',pct:20,color:'#ffd166'},
    {nombre:'Análisis',pct:20,color:'#ff6b35'},
    {nombre:'Sustentación',pct:20,color:'#a78bfa'},
  ];
  const cont=document.getElementById('evalBars');
  criterios.forEach(c=>{
    cont.innerHTML+=`
      <div class="rel-bar-wrap">
        <div class="rel-bar-top"><span class="rel-bar-name">${c.nombre}</span><span class="rel-bar-val" style="color:${c.color}">${c.pct}%</span></div>
        <div class="rel-bar-bg"><div class="rel-bar-fill" style="width:${c.pct*5}%;background:${c.color}"></div></div>
      </div>`;
  });
}
</script>
</body>
</html>
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width,initial-scale=1.0"/>
<title>CMMS · Sistema de Información de Mantenimiento · ECCI</title>
<link rel="preconnect" href="https://fonts.googleapis.com"/>
<link href="https://fonts.googleapis.com/css2?family=Space+Mono:wght@400;700&family=Syne:wght@400;600;700;800&display=swap" rel="stylesheet"/>
<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.0/dist/chart.umd.min.js"></script>
<style>
:root{
  --bg:#0a0c10;
  --surface:#111318;
  --surface2:#181c24;
  --border:#22293a;
  --accent:#00e5a0;
  --accent2:#ff6b35;
  --accent3:#4e9cff;
  --accent4:#ffd166;
  --text:#eef2ff;
  --muted:#7b8ab8;
  --red:#ff4d6d;
  --green:#00e5a0;
  --yellow:#ffd166;
  --font-head:'Syne',sans-serif;
  --font-mono:'Space Mono',monospace;
  --radius:12px;
}
*{margin:0;padding:0;box-sizing:border-box;}
body{background:var(--bg);color:var(--text);font-family:var(--font-head);min-height:100vh;}

/* NAV */
nav{
  display:flex;align-items:center;justify-content:space-between;
  padding:18px 32px;
  border-bottom:1px solid var(--border);
  background:rgba(10,12,16,.95);
  position:sticky;top:0;z-index:100;
  backdrop-filter:blur(12px);
}
.nav-logo{display:flex;align-items:center;gap:12px;}
.nav-logo .badge{
  background:var(--accent);color:#000;
  font-family:var(--font-mono);font-size:11px;font-weight:700;
  padding:4px 10px;border-radius:4px;letter-spacing:.05em;
}
.nav-title{font-size:15px;font-weight:700;color:var(--text);}
.nav-sub{font-size:11px;color:var(--muted);font-family:var(--font-mono);}
.nav-tabs{display:flex;gap:4px;}
.tab-btn{
  background:none;border:1px solid transparent;
  color:var(--muted);font-family:var(--font-head);font-size:13px;font-weight:600;
  padding:7px 16px;border-radius:8px;cursor:pointer;transition:.2s;
}
.tab-btn.active{border-color:var(--accent);color:var(--accent);background:rgba(0,229,160,.07);}
.tab-btn:hover:not(.active){border-color:var(--border);color:var(--text);}
.nav-right{font-family:var(--font-mono);font-size:11px;color:var(--muted);}

/* MAIN */
main{padding:28px 32px;max-width:1400px;margin:0 auto;}
.page{display:none;animation:fadeIn .3s ease;}
.page.active{display:block;}
@keyframes fadeIn{from{opacity:0;transform:translateY(8px)}to{opacity:1;transform:none}}

/* SECTION HEADER */
.section-header{margin-bottom:24px;}
.section-header h2{font-size:24px;font-weight:800;letter-spacing:-.02em;}
.section-header p{color:var(--muted);font-size:13px;margin-top:4px;font-family:var(--font-mono);}

/* KPI GRID */
.kpi-grid{display:grid;grid-template-columns:repeat(auto-fill,minmax(200px,1fr));gap:16px;margin-bottom:28px;}
.kpi-card{
  background:var(--surface);border:1px solid var(--border);
  border-radius:var(--radius);padding:20px;position:relative;overflow:hidden;
  transition:.25s;
}
.kpi-card:hover{border-color:var(--accent);transform:translateY(-2px);}
.kpi-card::before{
  content:'';position:absolute;top:0;left:0;right:0;height:3px;
  background:var(--kpi-color,var(--accent));
}
.kpi-label{font-size:11px;color:var(--muted);font-family:var(--font-mono);text-transform:uppercase;letter-spacing:.08em;margin-bottom:8px;}
.kpi-value{font-size:32px;font-weight:800;line-height:1;letter-spacing:-.03em;}
.kpi-unit{font-size:13px;color:var(--muted);margin-left:4px;font-weight:400;}
.kpi-delta{display:inline-flex;align-items:center;gap:4px;margin-top:8px;font-size:11px;font-family:var(--font-mono);padding:3px 8px;border-radius:4px;}
.kpi-delta.up{background:rgba(0,229,160,.12);color:var(--green);}
.kpi-delta.down{background:rgba(255,77,109,.12);color:var(--red);}
.kpi-delta.neutral{background:rgba(255,209,102,.1);color:var(--yellow);}

/* GRID LAYOUTS */
.grid-2{display:grid;grid-template-columns:1fr 1fr;gap:20px;margin-bottom:20px;}
.grid-3{display:grid;grid-template-columns:1fr 1fr 1fr;gap:20px;margin-bottom:20px;}
.grid-1-2{display:grid;grid-template-columns:1fr 2fr;gap:20px;margin-bottom:20px;}
.grid-2-1{display:grid;grid-template-columns:2fr 1fr;gap:20px;margin-bottom:20px;}
@media(max-width:900px){.grid-2,.grid-3,.grid-1-2,.grid-2-1{grid-template-columns:1fr;}}

/* CARD */
.card{background:var(--surface);border:1px solid var(--border);border-radius:var(--radius);overflow:hidden;}
.card-header{padding:16px 20px;border-bottom:1px solid var(--border);display:flex;align-items:center;justify-content:space-between;}
.card-header h3{font-size:14px;font-weight:700;letter-spacing:-.01em;}
.card-tag{font-size:10px;font-family:var(--font-mono);color:var(--muted);background:var(--surface2);padding:3px 8px;border-radius:4px;border:1px solid var(--border);}
.card-body{padding:20px;}

/* TABLE */
.data-table{width:100%;border-collapse:collapse;font-size:13px;}
.data-table th{padding:10px 14px;text-align:left;font-size:10px;font-family:var(--font-mono);text-transform:uppercase;letter-spacing:.08em;color:var(--muted);border-bottom:1px solid var(--border);white-space:nowrap;}
.data-table td{padding:11px 14px;border-bottom:1px solid rgba(34,41,58,.5);color:var(--text);}
.data-table tr:last-child td{border:none;}
.data-table tr:hover td{background:var(--surface2);}
.badge{display:inline-block;padding:3px 9px;border-radius:4px;font-size:10px;font-family:var(--font-mono);font-weight:700;}
.badge-green{background:rgba(0,229,160,.15);color:var(--green);}
.badge-red{background:rgba(255,77,109,.15);color:var(--red);}
.badge-yellow{background:rgba(255,209,102,.12);color:var(--yellow);}
.badge-blue{background:rgba(78,156,255,.12);color:var(--accent3);}

/* RELIABILITY BARS */
.rel-bar-wrap{margin-bottom:14px;}
.rel-bar-top{display:flex;justify-content:space-between;margin-bottom:5px;font-size:12px;}
.rel-bar-name{font-weight:600;}
.rel-bar-val{font-family:var(--font-mono);color:var(--muted);}
.rel-bar-bg{height:8px;background:var(--surface2);border-radius:4px;overflow:hidden;}
.rel-bar-fill{height:100%;border-radius:4px;transition:width 1s ease;}

/* CHART CONTAINER */
.chart-wrap{position:relative;padding:20px;}
.chart-wrap canvas{max-height:280px;}

/* HEATMAP */
.heatmap{display:grid;gap:4px;font-size:10px;font-family:var(--font-mono);}
.hm-cell{
  padding:8px 4px;border-radius:6px;text-align:center;cursor:default;
  font-weight:700;transition:.2s;font-size:11px;
}
.hm-cell:hover{transform:scale(1.08);}
.hm-header{color:var(--muted);font-weight:400;background:transparent!important;}

/* INSIGHTS */
.insight{display:flex;gap:12px;padding:14px;background:var(--surface2);border-radius:10px;margin-bottom:10px;border-left:3px solid var(--insight-color,var(--accent));}
.insight-icon{font-size:18px;flex-shrink:0;}
.insight-text{font-size:12px;line-height:1.6;color:var(--text);}
.insight-text strong{color:var(--insight-color,var(--accent));}

/* GAUGE */
.gauge-wrap{display:flex;flex-direction:column;align-items:center;padding:20px;}
.gauge-svg{overflow:visible;}
.gauge-value{font-size:28px;font-weight:800;font-family:var(--font-mono);}
.gauge-label{font-size:11px;color:var(--muted);margin-top:4px;font-family:var(--font-mono);}

/* PHASE TIMELINE */
.timeline{position:relative;padding-left:28px;}
.timeline::before{content:'';position:absolute;left:10px;top:0;bottom:0;width:2px;background:var(--border);}
.tl-item{position:relative;margin-bottom:20px;}
.tl-dot{
  position:absolute;left:-22px;top:4px;
  width:12px;height:12px;border-radius:50%;
  background:var(--tl-color,var(--muted));border:2px solid var(--bg);
}
.tl-item.done .tl-dot{background:var(--green);}
.tl-item.active .tl-dot{background:var(--accent);box-shadow:0 0 0 4px rgba(0,229,160,.2);}
.tl-date{font-size:10px;font-family:var(--font-mono);color:var(--muted);margin-bottom:3px;}
.tl-title{font-size:13px;font-weight:700;}
.tl-desc{font-size:11px;color:var(--muted);margin-top:2px;line-height:1.5;}

/* RELIABILITY METRICS SECTION */
.metric-big{text-align:center;padding:24px 16px;}
.metric-big .val{font-size:48px;font-weight:800;font-family:var(--font-mono);letter-spacing:-.04em;}
.metric-big .unit{font-size:16px;color:var(--muted);}
.metric-big .lbl{font-size:11px;color:var(--muted);margin-top:6px;font-family:var(--font-mono);text-transform:uppercase;letter-spacing:.1em;}
.metric-big .sub{font-size:11px;color:var(--muted);margin-top:8px;line-height:1.5;max-width:160px;margin-inline:auto;}

.divider{height:1px;background:var(--border);margin:24px 0;}
.formula-box{
  background:var(--surface2);border:1px solid var(--border);
  border-radius:8px;padding:14px 18px;
  font-family:var(--font-mono);font-size:12px;color:var(--accent);
  margin-bottom:16px;
}
.formula-box span{color:var(--muted);}

/* RESPONSIVE */
@media(max-width:600px){
  nav{padding:12px 16px;flex-wrap:wrap;gap:8px;}
  main{padding:16px;}
  .kpi-value{font-size:24px;}
}
</style>
</head>
<body>

<nav>
  <div class="nav-logo">
    <div class="badge">CMMS</div>
    <div>
      <div class="nav-title">Sistema de Información de Mantenimiento</div>
      <div class="nav-sub">Electiva Profundización I · Universidad ECCI · 2026-1</div>
    </div>
  </div>
  <div class="nav-tabs">
    <button class="tab-btn active" onclick="showPage('dashboard')">Dashboard</button>
    <button class="tab-btn" onclick="showPage('confiabilidad')">Confiabilidad</button>
    <button class="tab-btn" onclick="showPage('ordenes')">Órdenes de Trabajo</button>
    <button class="tab-btn" onclick="showPage('equipos')">Equipos</button>
    <button class="tab-btn" onclick="showPage('fases')">Fases</button>
  </div>
  <div class="nav-right">HOY: 23-ABR-2026</div>
</nav>

<main>

<!-- ══════════════════ DASHBOARD ══════════════════ -->
<div id="page-dashboard" class="page active">
  <div class="section-header">
    <h2>Resumen Ejecutivo</h2>
    <p>Planta Hipotética · Indicadores clave de mantenimiento · Abril 2026</p>
  </div>

  <div class="kpi-grid">
    <div class="kpi-card" style="--kpi-color:#00e5a0">
      <div class="kpi-label">Disponibilidad</div>
      <div class="kpi-value">89.4<span class="kpi-unit">%</span></div>
      <div class="kpi-delta up">↑ +2.1% vs mes ant.</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#4e9cff">
      <div class="kpi-label">MTTR Promedio</div>
      <div class="kpi-value">4.2<span class="kpi-unit">h</span></div>
      <div class="kpi-delta up">↓ −0.8h mejor</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ffd166">
      <div class="kpi-label">MTTF Promedio</div>
      <div class="kpi-value">34.6<span class="kpi-unit">h</span></div>
      <div class="kpi-delta up">↑ +3.2h vs meta</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ff6b35">
      <div class="kpi-label">% Cumpl. OT</div>
      <div class="kpi-value">82.3<span class="kpi-unit">%</span></div>
      <div class="kpi-delta neutral">→ Meta: 90%</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ff4d6d">
      <div class="kpi-label">OT Abiertas</div>
      <div class="kpi-value">14<span class="kpi-unit">OT</span></div>
      <div class="kpi-delta down">↑ +3 críticas</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#a78bfa">
      <div class="kpi-label">Costo Repuestos</div>
      <div class="kpi-value">$4.7<span class="kpi-unit">M</span></div>
      <div class="kpi-delta neutral">→ Ppto: $5.0M</div>
    </div>
  </div>

  <div class="grid-2-1">
    <div class="card">
      <div class="card-header"><h3>📈 Disponibilidad Mensual por Equipo</h3><span class="card-tag">FY2025-2026</span></div>
      <div class="chart-wrap"><canvas id="trendChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>🔍 Hallazgos Automáticos</h3></div>
      <div class="card-body">
        <div class="insight" style="--insight-color:#ff4d6d">
          <span class="insight-icon">🚨</span>
          <div class="insight-text"><strong>Compresor C-101</strong> muestra MTTR de 7.1h — 69% sobre la meta. Revisar causa raíz.</div>
        </div>
        <div class="insight" style="--insight-color:#ffd166">
          <span class="insight-icon">⚠️</span>
          <div class="insight-text"><strong>Bomba P-204</strong> presenta tendencia decreciente de disponibilidad: −5.2% en 3 meses.</div>
        </div>
        <div class="insight" style="--insight-color:#00e5a0">
          <span class="insight-icon">✅</span>
          <div class="insight-text"><strong>Turbina T-01</strong> supera la meta de disponibilidad con 96.1% — mejor equipo del mes.</div>
        </div>
        <div class="insight" style="--insight-color:#4e9cff">
          <span class="insight-icon">💡</span>
          <div class="insight-text"><strong>14 OT pendientes</strong>: 3 críticas (prioridad 1). Planner debe reasignar técnicos esta semana.</div>
        </div>
        <div class="insight" style="--insight-color:#a78bfa">
          <span class="insight-icon">📦</span>
          <div class="insight-text">Stock de <strong>rodamientos SKF</strong> en nivel mínimo (2 unidades). Generar orden de compra.</div>
        </div>
      </div>
    </div>
  </div>

  <div class="grid-2">
    <div class="card">
      <div class="card-header"><h3>📊 Disponibilidad por Equipo (Promedio)</h3></div>
      <div class="chart-wrap"><canvas id="barChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>🔥 Mapa de Calor · Disponibilidad % Equipo × Mes</h3></div>
      <div class="card-body" id="heatmapContainer" style="padding:12px;"></div>
    </div>
  </div>
</div>

<!-- ══════════════════ CONFIABILIDAD ══════════════════ -->
<div id="page-confiabilidad" class="page">
  <div class="section-header">
    <h2>Indicadores de Confiabilidad</h2>
    <p>MTTR · MTTF · Disponibilidad calculada · Datos hipotéticos para actividad académica</p>
  </div>

  <div class="formula-box">
    <span>// Fórmulas base de confiabilidad</span><br>
    Disponibilidad (%) = MTTF / (MTTF + MTTR) × 100<br>
    MTTR = Tiempo Total de Reparación / N° de Fallas<br>
    MTTF = Tiempo Total de Operación / N° de Fallas
  </div>

  <div class="grid-3" style="margin-bottom:20px;">
    <div class="card" style="--kpi-color:#4e9cff">
      <div class="metric-big">
        <div class="val" style="color:var(--accent3)">4.2<span style="font-size:20px;color:var(--muted)">h</span></div>
        <div class="lbl">MTTR Global</div>
        <div class="sub">Tiempo Medio para Reparar · Promedio flota completa</div>
      </div>
    </div>
    <div class="card">
      <div class="metric-big">
        <div class="val" style="color:var(--yellow)">34.6<span style="font-size:20px;color:var(--muted)">h</span></div>
        <div class="lbl">MTTF Global</div>
        <div class="sub">Tiempo Medio Entre Fallas · Promedio flota completa</div>
      </div>
    </div>
    <div class="card">
      <div class="metric-big">
        <div class="val" style="color:var(--green)">89.4<span style="font-size:20px;color:var(--muted)">%</span></div>
        <div class="lbl">Disponibilidad</div>
        <div class="sub">MTTF/(MTTF+MTTR) · Meta: 92%</div>
      </div>
    </div>
  </div>

  <!-- Tabla detalle MTTR MTTF por equipo -->
  <div class="card" style="margin-bottom:20px;">
    <div class="card-header"><h3>📋 MTTR & MTTF por Equipo · Datos Hipotéticos</h3><span class="card-tag">ABR 2026</span></div>
    <div style="overflow-x:auto;">
      <table class="data-table" id="reliabilityTable"></table>
    </div>
  </div>

  <div class="grid-2">
    <div class="card">
      <div class="card-header"><h3>📉 MTTR por Equipo (horas)</h3><span class="card-tag">Meta ≤ 4h</span></div>
      <div class="chart-wrap"><canvas id="mttrChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>📈 MTTF por Equipo (horas)</h3><span class="card-tag">Meta ≥ 30h</span></div>
      <div class="chart-wrap"><canvas id="mttfChart"></canvas></div>
    </div>
  </div>

  <div class="card" style="margin-bottom:20px;">
    <div class="card-header"><h3>🎯 Disponibilidad Calculada por Equipo</h3><span class="card-tag">Línea roja = meta 92%</span></div>
    <div class="chart-wrap"><canvas id="dispChart"></canvas></div>
  </div>

  <div class="card">
    <div class="card-header"><h3>📊 Barras de Confiabilidad por Equipo</h3></div>
    <div class="card-body" id="relBarsContainer"></div>
  </div>
</div>

<!-- ══════════════════ ÓRDENES DE TRABAJO ══════════════════ -->
<div id="page-ordenes" class="page">
  <div class="section-header">
    <h2>Órdenes de Trabajo (OT)</h2>
    <p>Registro de actividades de mantenimiento · Módulo 2 de la actividad final</p>
  </div>

  <div class="kpi-grid" style="grid-template-columns:repeat(4,1fr);">
    <div class="kpi-card" style="--kpi-color:#00e5a0">
      <div class="kpi-label">OT Cerradas</div>
      <div class="kpi-value">47</div>
      <div class="kpi-delta up">↑ Este mes</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ffd166">
      <div class="kpi-label">OT En Proceso</div>
      <div class="kpi-value">11</div>
      <div class="kpi-delta neutral">→ Prog. esta sem.</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#ff4d6d">
      <div class="kpi-label">OT Críticas Abiertas</div>
      <div class="kpi-value">3</div>
      <div class="kpi-delta down">↑ Requiere acción</div>
    </div>
    <div class="kpi-card" style="--kpi-color:#4e9cff">
      <div class="kpi-label">% Cumplimiento OT</div>
      <div class="kpi-value">82.3<span class="kpi-unit">%</span></div>
      <div class="kpi-delta neutral">→ Meta 90%</div>
    </div>
  </div>

  <div class="grid-2" style="margin-bottom:20px;">
    <div class="card">
      <div class="card-header"><h3>🍩 Tipos de Mantenimiento</h3></div>
      <div class="chart-wrap"><canvas id="tipoOTChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>📅 OT por Mes · Cumplimiento</h3></div>
      <div class="chart-wrap"><canvas id="cumplOTChart"></canvas></div>
    </div>
  </div>

  <div class="card">
    <div class="card-header"><h3>📋 Registro de Órdenes de Trabajo</h3><span class="card-tag">Últimas 15 OT</span></div>
    <div style="overflow-x:auto;">
      <table class="data-table" id="otTable"></table>
    </div>
  </div>
</div>

<!-- ══════════════════ EQUIPOS ══════════════════ -->
<div id="page-equipos" class="page">
  <div class="section-header">
    <h2>Administración de Equipos</h2>
    <p>Inventario, criticidad y estado · Módulo 1 de la actividad final</p>
  </div>

  <div class="grid-2" style="margin-bottom:20px;">
    <div class="card">
      <div class="card-header"><h3>🏭 Equipos por Criticidad</h3></div>
      <div class="chart-wrap"><canvas id="criticidadChart"></canvas></div>
    </div>
    <div class="card">
      <div class="card-header"><h3>⚙️ Estado Operativo de la Flota</h3></div>
      <div class="chart-wrap"><canvas id="estadoChart"></canvas></div>
    </div>
  </div>

  <div class="card">
    <div class="card-header"><h3>📋 Inventario de Equipos</h3><span class="card-tag">Módulo 1</span></div>
    <div style="overflow-x:auto;">
      <table class="data-table" id="equiposTable"></table>
    </div>
  </div>
</div>

<!-- ══════════════════ FASES ══════════════════ -->
<div id="page-fases" class="page">
  <div class="section-header">
    <h2>Plan de Trabajo · Fases del Proyecto</h2>
    <p>Actividad Final · Electiva Profundización I · Prof. María Andrea Ramírez Morales</p>
  </div>

  <div class="grid-2">
    <div class="card">
      <div class="card-header"><h3>📅 Cronograma de Fases</h3></div>
      <div class="card-body">
        <div class="timeline">
          <div class="tl-item done">
            <div class="tl-dot"></div>
            <div class="tl-date">JUE 23-ABR-2026 · HOY ✓</div>
            <div class="tl-title">Fase 1 · Definición del Sistema</div>
            <div class="tl-desc">Objetivo del sistema, problemas a resolver, usuarios (técnico, planner, jefe).</div>
          </div>
          <div class="tl-item active">
            <div class="tl-dot"></div>
            <div class="tl-date">SEM 28–30 ABR 2026</div>
            <div class="tl-title">Fase 2 · Diseño de Módulos (Excel)</div>
            <div class="tl-desc">Equipos · OT · Personal · Materiales · Control de actividades.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot"></div>
            <div class="tl-date">SEM 5–7 MAY 2026</div>
            <div class="tl-title">Fase 3 · Integración del Sistema</div>
            <div class="tl-desc">Relacionar tablas: OT↔Equipos · Técnicos asignados · Consumo de repuestos.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot"></div>
            <div class="tl-date">SEM 12–14 MAY 2026</div>
            <div class="tl-title">Fase 4 · Indicadores KPI</div>
            <div class="tl-desc">% Cumplimiento OT · MTTR · Disponibilidad. Dashboard visual atractivo.</div>
          </div>
          <div class="tl-item">
            <div class="tl-dot"></div>
            <div class="tl-date">SEM 26–28 MAY 2026</div>
            <div class="tl-title">Fase 5 · Análisis</div>
            <div class="tl-desc">A) Problemas resueltos B) Decisiones posibles C) Limitaciones vs CMMS D) Mejoras propuestas.</div>
          </div>
        </div>
      </div>
    </div>

    <div>
      <div class="card" style="margin-bottom:20px;">
        <div class="card-header"><h3>🎯 Criterios de Evaluación</h3><span class="card-tag">100%</span></div>
        <div class="card-body">
          <div id="evalBars"></div>
        </div>
      </div>

      <div class="card">
        <div class="card-header"><h3>📦 Módulos del Sistema</h3></div>
        <div class="card-body" style="display:grid;gap:10px;">
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">⚙️</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 1 · Equipos</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">ID · Equipo · Ubicación · Estado · F. instalación · Criticidad</div></div>
          </div>
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">📋</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 2 · Órdenes de Trabajo</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">ID OT · Equipo · Fecha · Tipo · Falla · Técnico · Tiempo · Estado</div></div>
          </div>
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">👷</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 3 · Personal</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">ID · Nombre · Especialidad · Turno · Experiencia</div></div>
          </div>
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">🔩</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 4 · Materiales</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">Código · Repuesto · Stock · Consumo · Costo</div></div>
          </div>
          <div style="display:flex;gap:10px;align-items:center;padding:10px;background:var(--surface2);border-radius:8px;border:1px solid var(--border);">
            <span style="font-size:20px;">📊</span>
            <div><div style="font-size:13px;font-weight:700;">Módulo 5 · Control Actividades</div><div style="font-size:11px;color:var(--muted);font-family:var(--font-mono);">OT · Actividad · T. planificado · T. real · Cumplimiento</div></div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>

</main>

<script>
// ── DATA ───────────────────────────────────────────────────────────────────
const equipos = [
  {id:'EQ-001',nombre:'Compresor C-101',ubicacion:'Planta A',estado:'Operativo',instalacion:'2019-03-15',criticidad:'Alta',
   mttr:7.1,mttf:28.4,fallas:12,t_rep:85.2,t_op:340.8},
  {id:'EQ-002',nombre:'Bomba P-204',ubicacion:'Planta B',estado:'Operativo',instalacion:'2020-07-22',criticidad:'Alta',
   mttr:3.8,mttf:31.2,fallas:10,t_rep:38,t_op:312},
  {id:'EQ-003',nombre:'Turbina T-01',ubicacion:'Planta A',estado:'Operativo',instalacion:'2018-11-10',criticidad:'Crítica',
   mttr:2.1,mttf:50.3,fallas:6,t_rep:12.6,t_op:301.8},
  {id:'EQ-004',nombre:'Motor M-302',ubicacion:'Planta C',estado:'En Mantenimiento',instalacion:'2021-01-08',criticidad:'Media',
   mttr:4.5,mttf:33.6,fallas:8,t_rep:36,t_op:268.8},
  {id:'EQ-005',nombre:'Agitador AG-07',ubicacion:'Planta B',estado:'Operativo',instalacion:'2022-05-17',criticidad:'Baja',
   mttr:2.8,mttf:42.0,fallas:5,t_rep:14,t_op:210},
  {id:'EQ-006',nombre:'Caldera CA-02',ubicacion:'Planta A',estado:'Operativo',instalacion:'2017-09-30',criticidad:'Crítica',
   mttr:5.2,mttf:29.8,fallas:9,t_rep:46.8,t_op:268.2},
  {id:'EQ-007',nombre:'Banda BT-55',ubicacion:'Planta C',estado:'Fuera de Servicio',instalacion:'2020-03-12',criticidad:'Media',
   mttr:6.0,mttf:22.0,fallas:11,t_rep:66,t_op:242},
];

const meses = ['Jul','Ago','Sep','Oct','Nov','Dic','Ene','Feb','Mar','Abr'];
const disponibilidadMensual = {
  'Compresor C-101': [80,82,78,75,77,79,81,80,82,80],
  'Bomba P-204':     [88,87,86,84,83,82,85,84,83,89],
  'Turbina T-01':    [95,96,97,96,95,96,97,96,95,96],
  'Motor M-302':     [91,90,89,88,87,88,89,88,87,86],
  'Caldera CA-02':   [85,84,83,82,81,83,84,85,84,83],
};

const OTs = [
  {id:'OT-0041',equipo:'Compresor C-101',fecha:'2026-04-20',tipo:'Correctivo',falla:'Vibración excesiva',actividad:'Cambio rodamiento',tecnico:'J. Pérez',tiempo:8,estado:'Cerrada'},
  {id:'OT-0042',equipo:'Bomba P-204',fecha:'2026-04-21',tipo:'Preventivo',falla:'Mantenimiento prog.',actividad:'Cambio sellos',tecnico:'M. Torres',tiempo:3,estado:'Cerrada'},
  {id:'OT-0043',equipo:'Turbina T-01',fecha:'2026-04-22',tipo:'Predictivo',falla:'Análisis vibración',actividad:'Monitoreo',tecnico:'A. Gómez',tiempo:2,estado:'Cerrada'},
  {id:'OT-0044',equipo:'Motor M-302',fecha:'2026-04-22',tipo:'Correctivo',falla:'Sobrecalentamiento',actividad:'Revisión bobinado',tecnico:'J. Pérez',tiempo:6,estado:'En Proceso'},
  {id:'OT-0045',equipo:'Caldera CA-02',fecha:'2026-04-23',tipo:'Correctivo',falla:'Fuga vapor',actividad:'Cambio empaque',tecnico:'C. Ríos',tiempo:5,estado:'Abierta'},
  {id:'OT-0046',equipo:'Banda BT-55',fecha:'2026-04-23',tipo:'Correctivo',falla:'Banda rota',actividad:'Reemplazo banda',tecnico:'M. Torres',tiempo:7,estado:'Abierta'},
  {id:'OT-0047',equipo:'Agitador AG-07',fecha:'2026-04-19',tipo:'Preventivo',falla:'PM programado',actividad:'Lubricación general',tecnico:'A. Gómez',tiempo:2,estado:'Cerrada'},
  {id:'OT-0048',equipo:'Compresor C-101',fecha:'2026-04-18',tipo:'Correctivo',falla:'Presión baja',actividad:'Ajuste válvulas',tecnico:'C. Ríos',tiempo:4,estado:'Cerrada'},
  {id:'OT-0049',equipo:'Bomba P-204',fecha:'2026-04-17',tipo:'Correctivo',falla:'Ruido anormal',actividad:'Revisión impelente',tecnico:'J. Pérez',tiempo:5,estado:'Cerrada'},
  {id:'OT-0050',equipo:'Caldera CA-02',fecha:'2026-04-23',tipo:'Correctivo',falla:'Quemador falla',actividad:'Limpieza quemador',tecnico:'A. Gómez',tiempo:6,estado:'Abierta'},
  {id:'OT-0051',equipo:'Motor M-302',fecha:'2026-04-16',tipo:'Preventivo',falla:'PM mensual',actividad:'Limpieza y ajuste',tecnico:'M. Torres',tiempo:2,estado:'Cerrada'},
  {id:'OT-0052',equipo:'Turbina T-01',fecha:'2026-04-15',tipo:'Predictivo',falla:'Termografía',actividad:'Inspección IR',tecnico:'C. Ríos',tiempo:1,estado:'Cerrada'},
  {id:'OT-0053',equipo:'Agitador AG-07',fecha:'2026-04-14',tipo:'Correctivo',falla:'Motor sobrecarga',actividad:'Revisión protección',tecnico:'J. Pérez',tiempo:3,estado:'Cerrada'},
  {id:'OT-0054',equipo:'Banda BT-55',fecha:'2026-04-23',tipo:'Correctivo',falla:'Rodillo dañado',actividad:'Cambio rodillo',tecnico:'M. Torres',tiempo:4,estado:'En Proceso'},
  {id:'OT-0055',equipo:'Compresor C-101',fecha:'2026-04-23',tipo:'Predictivo',falla:'Análisis aceite',actividad:'Toma muestra aceite',tecnico:'A. Gómez',tiempo:1,estado:'En Proceso'},
];

// ── NAVIGATION ─────────────────────────────────────────────────────────────
function showPage(id){
  document.querySelectorAll('.page').forEach(p=>p.classList.remove('active'));
  document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
  document.getElementById('page-'+id).classList.add('active');
  event.target.classList.add('active');
  // lazy init charts
  if(id==='confiabilidad' && !window._confInit){window._confInit=true;initConfiabilidad();}
  if(id==='ordenes' && !window._otInit){window._otInit=true;initOrdenes();}
  if(id==='equipos' && !window._eqInit){window._eqInit=true;initEquipos();}
  if(id==='fases' && !window._fasesInit){window._fasesInit=true;initFases();}
}

// ── COLORS ─────────────────────────────────────────────────────────────────
const COLORS=['#00e5a0','#4e9cff','#ffd166','#ff6b35','#a78bfa','#ff4d6d','#06d6a0'];
function alpha(hex,a){const r=parseInt(hex.slice(1,3),16),g=parseInt(hex.slice(3,5),16),b=parseInt(hex.slice(5,7),16);return `rgba(${r},${g},${b},${a})`;}

const CHART_DEFAULTS={
  color:'#7b8ab8',
  plugins:{legend:{labels:{color:'#7b8ab8',font:{family:"'Space Mono',monospace",size:11}}},tooltip:{backgroundColor:'#111318',borderColor:'#22293a',borderWidth:1,titleColor:'#eef2ff',bodyColor:'#7b8ab8'}},
  scales:{x:{grid:{color:'rgba(34,41,58,.5)'},ticks:{color:'#7b8ab8',font:{family:"'Space Mono',monospace",size:10}}},y:{grid:{color:'rgba(34,41,58,.5)'},ticks:{color:'#7b8ab8',font:{family:"'Space Mono',monospace",size:10}}}}
};
function mergeOpts(extra={}){return {...CHART_DEFAULTS,...extra,plugins:{...CHART_DEFAULTS.plugins,...(extra.plugins||{})},scales:{...CHART_DEFAULTS.scales,...(extra.scales||{})}};}

// ── DASHBOARD CHARTS ───────────────────────────────────────────────────────
const equipNames=Object.keys(disponibilidadMensual);
new Chart(document.getElementById('trendChart'),{
  type:'line',
  data:{labels:meses,datasets:equipNames.map((e,i)=>({
    label:e,data:disponibilidadMensual[e],borderColor:COLORS[i],
    backgroundColor:alpha(COLORS[i],.08),tension:.4,pointRadius:3,pointHoverRadius:5,fill:false
  }))},
  options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,min:70,max:100,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'%'}}}})
});

new Chart(document.getElementById('barChart'),{
  type:'bar',
  data:{
    labels:equipos.map(e=>e.nombre.split(' ')[0]+' '+e.nombre.split(' ')[1]),
    datasets:[{
      label:'Disponibilidad %',
      data:equipos.map(e=>+(e.mttf/(e.mttf+e.mttr)*100).toFixed(1)),
      backgroundColor:equipos.map((e,i)=>alpha(COLORS[i],.7)),
      borderColor:equipos.map((_,i)=>COLORS[i]),borderWidth:1,borderRadius:6
    }]
  },
  options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,min:60,max:100,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'%'}}}})
});

// HEATMAP
function buildHeatmap(){
  const cont=document.getElementById('heatmapContainer');
  const eqKeys=Object.keys(disponibilidadMensual);
  const cols=meses.length+1;
  const hm=document.createElement('div');
  hm.className='heatmap';
  hm.style.gridTemplateColumns=`120px repeat(${meses.length},1fr)`;

  // header
  const headerEq=document.createElement('div');headerEq.className='hm-cell hm-header';headerEq.textContent='Equipo';hm.appendChild(headerEq);
  meses.forEach(m=>{const c=document.createElement('div');c.className='hm-cell hm-header';c.textContent=m;hm.appendChild(c);});

  eqKeys.forEach((eq,i)=>{
    const label=document.createElement('div');
    label.className='hm-cell';label.style.color='var(--muted)';label.style.fontSize='10px';label.style.textAlign='left';
    label.textContent=eq.split(' ')[0];hm.appendChild(label);
    disponibilidadMensual[eq].forEach(v=>{
      const c=document.createElement('div');c.className='hm-cell';
      const norm=(v-70)/30;
      const r=Math.round(255-norm*255),g=Math.round(norm*229),b=Math.round(norm*100);
      c.style.background=`rgba(${r},${g},${b},0.7)`;
      c.style.color=v>85?'#000':'#fff';
      c.textContent=v;c.title=eq+' '+meses[0]+': '+v+'%';
      hm.appendChild(c);
    });
  });
  cont.appendChild(hm);
}
buildHeatmap();

// ── CONFIABILIDAD ──────────────────────────────────────────────────────────
function initConfiabilidad(){
  // Table
  const tbl=document.getElementById('reliabilityTable');
  const heads=['ID','Equipo','Fallas','T. Rep (h)','MTTR (h)','T. Op (h)','MTTF (h)','Disponibilidad','Estado'];
  tbl.innerHTML=`<thead><tr>${heads.map(h=>`<th>${h}</th>`).join('')}</tr></thead>`;
  const tbody=document.createElement('tbody');
  equipos.forEach((e,i)=>{
    const disp=(e.mttf/(e.mttf+e.mttr)*100).toFixed(1);
    const dispOk=disp>=90,dispWarn=disp>=80&&disp<90;
    const mttrOk=e.mttr<=4,mttrWarn=e.mttr<=6&&e.mttr>4;
    const tr=document.createElement('tr');
    tr.innerHTML=`
      <td><span style="font-family:var(--font-mono);color:var(--muted)">${e.id}</span></td>
      <td><b>${e.nombre}</b></td>
      <td style="font-family:var(--font-mono)">${e.fallas}</td>
      <td style="font-family:var(--font-mono)">${e.t_rep.toFixed(1)}</td>
      <td><span class="badge ${mttrOk?'badge-green':mttrWarn?'badge-yellow':'badge-red'}">${e.mttr.toFixed(1)}h</span></td>
      <td style="font-family:var(--font-mono)">${e.t_op.toFixed(1)}</td>
      <td><span class="badge badge-blue">${e.mttf.toFixed(1)}h</span></td>
      <td><span class="badge ${dispOk?'badge-green':dispWarn?'badge-yellow':'badge-red'}">${disp}%</span></td>
      <td><span class="badge ${e.estado==='Operativo'?'badge-green':e.estado==='En Mantenimiento'?'badge-yellow':'badge-red'}">${e.estado}</span></td>`;
    tbody.appendChild(tr);
  });
  tbl.appendChild(tbody);

  // MTTR chart
  new Chart(document.getElementById('mttrChart'),{
    type:'bar',
    data:{
      labels:equipos.map(e=>e.id),
      datasets:[
        {label:'MTTR (h)',data:equipos.map(e=>e.mttr),backgroundColor:equipos.map(e=>e.mttr<=4?alpha('#00e5a0',.7):e.mttr<=6?alpha('#ffd166',.7):alpha('#ff4d6d',.7)),borderColor:equipos.map(e=>e.mttr<=4?'#00e5a0':e.mttr<=6?'#ffd166':'#ff4d6d'),borderWidth:1,borderRadius:6},
        {label:'Meta (4h)',data:Array(equipos.length).fill(4),type:'line',borderColor:'#ff4d6d',borderDash:[5,5],pointRadius:0,borderWidth:1.5}
      ]
    },
    options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'h'}}}})
  });

  // MTTF chart
  new Chart(document.getElementById('mttfChart'),{
    type:'bar',
    data:{
      labels:equipos.map(e=>e.id),
      datasets:[
        {label:'MTTF (h)',data:equipos.map(e=>e.mttf),backgroundColor:equipos.map(e=>e.mttf>=40?alpha('#00e5a0',.7):e.mttf>=28?alpha('#ffd166',.7):alpha('#ff4d6d',.7)),borderColor:equipos.map(e=>e.mttf>=40?'#00e5a0':e.mttf>=28?'#ffd166':'#ff4d6d'),borderWidth:1,borderRadius:6},
        {label:'Meta (30h)',data:Array(equipos.length).fill(30),type:'line',borderColor:'#4e9cff',borderDash:[5,5],pointRadius:0,borderWidth:1.5}
      ]
    },
    options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'h'}}}})
  });

  // Disponibilidad calculada
  const dispVals=equipos.map(e=>+(e.mttf/(e.mttf+e.mttr)*100).toFixed(1));
  new Chart(document.getElementById('dispChart'),{
    type:'bar',
    data:{
      labels:equipos.map(e=>e.id),
      datasets:[
        {label:'Disponibilidad %',data:dispVals,backgroundColor:dispVals.map(v=>v>=90?alpha('#00e5a0',.7):v>=80?alpha('#ffd166',.7):alpha('#ff4d6d',.7)),borderRadius:6},
        {label:'Meta 92%',data:Array(equipos.length).fill(92),type:'line',borderColor:'#ff4d6d',borderDash:[6,4],pointRadius:0,borderWidth:1.5}
      ]
    },
    options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,min:60,max:100,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'%'}}}})
  });

  // Reliability bars
  const relCont=document.getElementById('relBarsContainer');
  equipos.forEach((e,i)=>{
    const disp=(e.mttf/(e.mttf+e.mttr)*100).toFixed(1);
    const color=disp>=90?'#00e5a0':disp>=80?'#ffd166':'#ff4d6d';
    relCont.innerHTML+=`
      <div class="rel-bar-wrap">
        <div class="rel-bar-top"><span class="rel-bar-name">${e.nombre}</span><span class="rel-bar-val">${disp}% · MTTF ${e.mttf}h · MTTR ${e.mttr}h</span></div>
        <div class="rel-bar-bg"><div class="rel-bar-fill" style="width:${disp}%;background:${color}"></div></div>
      </div>`;
  });
}

// ── ÓRDENES ───────────────────────────────────────────────────────────────
function initOrdenes(){
  // Tipo donut
  const tipos={Correctivo:0,Preventivo:0,Predictivo:0};
  OTs.forEach(o=>tipos[o.tipo]=(tipos[o.tipo]||0)+1);
  new Chart(document.getElementById('tipoOTChart'),{
    type:'doughnut',
    data:{labels:Object.keys(tipos),datasets:[{data:Object.values(tipos),backgroundColor:[alpha('#ff4d6d',.8),alpha('#00e5a0',.8),alpha('#4e9cff',.8)],borderColor:'#111318',borderWidth:3}]},
    options:{...CHART_DEFAULTS,scales:{},cutout:'65%',plugins:{...CHART_DEFAULTS.plugins}}
  });

  // Cumplimiento mensual
  const cumplData=[72,78,75,80,83,85,80,82,84,82];
  new Chart(document.getElementById('cumplOTChart'),{
    type:'line',
    data:{labels:meses,datasets:[
      {label:'% Cumplimiento',data:cumplData,borderColor:'#00e5a0',backgroundColor:alpha('#00e5a0',.1),fill:true,tension:.4,pointRadius:4},
      {label:'Meta 90%',data:Array(10).fill(90),borderColor:'#ff4d6d',borderDash:[6,4],pointRadius:0,borderWidth:1.5}
    ]},
    options:mergeOpts({scales:{y:{...CHART_DEFAULTS.scales.y,min:60,max:100,ticks:{...CHART_DEFAULTS.scales.y.ticks,callback:v=>v+'%'}}}})
  });

  // Table
  const tbl=document.getElementById('otTable');
  const heads=['ID OT','Equipo','Fecha','Tipo','Falla','Actividad','Técnico','Tiempo','Estado'];
  tbl.innerHTML=`<thead><tr>${heads.map(h=>`<th>${h}</th>`).join('')}</tr></thead>`;
  const tbody=document.createElement('tbody');
  OTs.forEach(o=>{
    const sc=o.estado==='Cerrada'?'badge-green':o.estado==='En Proceso'?'badge-yellow':'badge-red';
    const tc=o.tipo==='Correctivo'?'badge-red':o.tipo==='Preventivo'?'badge-green':'badge-blue';
    const tr=document.createElement('tr');
    tr.innerHTML=`<td><b style="font-family:var(--font-mono)">${o.id}</b></td><td>${o.equipo}</td><td style="font-family:var(--font-mono)">${o.fecha}</td><td><span class="badge ${tc}">${o.tipo}</span></td><td style="font-size:11px;color:var(--muted)">${o.falla}</td><td style="font-size:11px">${o.actividad}</td><td>${o.tecnico}</td><td style="font-family:var(--font-mono)">${o.tiempo}h</td><td><span class="badge ${sc}">${o.estado}</span></td>`;
    tbody.appendChild(tr);
  });
  tbl.appendChild(tbody);
}

// ── EQUIPOS ───────────────────────────────────────────────────────────────
function initEquipos(){
  const crit={Alta:0,Crítica:0,Media:0,Baja:0};
  const est={Operativo:0,'En Mantenimiento':0,'Fuera de Servicio':0};
  equipos.forEach(e=>{crit[e.criticidad]=(crit[e.criticidad]||0)+1;est[e.estado]=(est[e.estado]||0)+1;});

  new Chart(document.getElementById('criticidadChart'),{
    type:'doughnut',
    data:{labels:Object.keys(crit),datasets:[{data:Object.values(crit),backgroundColor:[alpha('#ff6b35',.8),alpha('#ff4d6d',.8),alpha('#ffd166',.8),alpha('#00e5a0',.8)],borderColor:'#111318',borderWidth:3}]},
    options:{...CHART_DEFAULTS,scales:{},cutout:'60%',plugins:{...CHART_DEFAULTS.plugins}}
  });

  new Chart(document.getElementById('estadoChart'),{
    type:'doughnut',
    data:{labels:Object.keys(est),datasets:[{data:Object.values(est),backgroundColor:[alpha('#00e5a0',.8),alpha('#ffd166',.8),alpha('#ff4d6d',.8)],borderColor:'#111318',borderWidth:3}]},
    options:{...CHART_DEFAULTS,scales:{},cutout:'60%',plugins:{...CHART_DEFAULTS.plugins}}
  });

  const tbl=document.getElementById('equiposTable');
  const heads=['ID','Equipo','Ubicación','Estado','F. Instalación','Criticidad','MTTR','MTTF','Disp.'];
  tbl.innerHTML=`<thead><tr>${heads.map(h=>`<th>${h}</th>`).join('')}</tr></thead>`;
  const tbody=document.createElement('tbody');
  equipos.forEach(e=>{
    const disp=(e.mttf/(e.mttf+e.mttr)*100).toFixed(1);
    const sc=e.estado==='Operativo'?'badge-green':e.estado==='En Mantenimiento'?'badge-yellow':'badge-red';
    const cc=e.criticidad==='Crítica'?'badge-red':e.criticidad==='Alta'?'badge-yellow':e.criticidad==='Media'?'badge-blue':'badge-green';
    const tr=document.createElement('tr');
    tr.innerHTML=`<td><b style="font-family:var(--font-mono)">${e.id}</b></td><td><b>${e.nombre}</b></td><td style="color:var(--muted)">${e.ubicacion}</td><td><span class="badge ${sc}">${e.estado}</span></td><td style="font-family:var(--font-mono);font-size:11px">${e.instalacion}</td><td><span class="badge ${cc}">${e.criticidad}</span></td><td style="font-family:var(--font-mono)">${e.mttr}h</td><td style="font-family:var(--font-mono)">${e.mttf}h</td><td><span class="badge ${+disp>=90?'badge-green':+disp>=80?'badge-yellow':'badge-red'}">${disp}%</span></td>`;
    tbody.appendChild(tr);
  });
  tbl.appendChild(tbody);
}

// ── FASES ─────────────────────────────────────────────────────────────────
function initFases(){
  const criterios=[
    {nombre:'Diseño del Sistema',pct:20,color:'#00e5a0'},
    {nombre:'Uso de Excel',pct:20,color:'#4e9cff'},
    {nombre:'Indicadores KPI',pct:20,color:'#ffd166'},
    {nombre:'Análisis',pct:20,color:'#ff6b35'},
    {nombre:'Sustentación',pct:20,color:'#a78bfa'},
  ];
  const cont=document.getElementById('evalBars');
  criterios.forEach(c=>{
    cont.innerHTML+=`
      <div class="rel-bar-wrap">
        <div class="rel-bar-top"><span class="rel-bar-name">${c.nombre}</span><span class="rel-bar-val" style="color:${c.color}">${c.pct}%</span></div>
        <div class="rel-bar-bg"><div class="rel-bar-fill" style="width:${c.pct*5}%;background:${c.color}"></div></div>
      </div>`;
  });
}
</script>
</body>
</html>
