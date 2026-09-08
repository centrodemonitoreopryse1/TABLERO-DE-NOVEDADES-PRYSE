[index.html.html](https://github.com/user-attachments/files/31980391/index.html.html)
<!DOCTYPE html>
<html lang="es">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Tablero de Avances — Bitácora de Novedades 07–08 Sep 2026</title>
<style>
  :root{
    --bg: #0f141b;
    --panel: #161d27;
    --panel-2: #1c2530;
    --line: #2a3444;
    --text: #dde3ea;
    --text-dim: #8b98a8;
    --guinda: #9c2545;
    --guinda-soft: #c9506f;
    --ok: #3f9e6a;
    --ok-bg: rgba(63,158,106,.12);
    --warn: #d69a2d;
    --warn-bg: rgba(214,154,45,.14);
    --bad: #d1503f;
    --bad-bg: rgba(209,80,63,.14);
    --mono: "SFMono-Regular", ui-monospace, "DejaVu Sans Mono", Menlo, Consolas, monospace;
    --sans: -apple-system, "Segoe UI", ui-sans-serif, Roboto, Helvetica, Arial, sans-serif;
  }
  *{box-sizing:border-box;}
  body{
    margin:0; background:var(--bg); color:var(--text);
    font-family:var(--sans); line-height:1.5; -webkit-font-smoothing:antialiased;
  }
  .wrap{max-width:1180px; margin:0 auto; padding:32px 24px 80px;}

  header.top{
    display:flex; justify-content:space-between; align-items:flex-end; gap:24px;
    border-bottom:1px solid var(--line); padding-bottom:20px; margin-bottom:28px; flex-wrap:wrap;
  }
  header.top .id{
    font-family:var(--mono); font-size:12px; color:var(--guinda-soft); letter-spacing:.02em; margin-bottom:8px;
  }
  header.top h1{ font-size:26px; font-weight:650; margin:0 0 6px; letter-spacing:-.01em; }
  header.top p{ margin:0; color:var(--text-dim); font-size:14px; max-width:60ch; }
  header.top .window{
    font-family:var(--mono); font-size:13px; color:var(--text-dim); text-align:right;
  }
  header.top .window b{ color:var(--text); font-weight:600; }

  .kpis{
    display:grid; grid-template-columns:repeat(5,1fr); gap:1px;
    background:var(--line); border:1px solid var(--line); border-radius:10px; overflow:hidden;
    margin-bottom:32px;
  }
  .kpi{ background:var(--panel); padding:18px 16px; }
  .kpi .n{ font-family:var(--mono); font-size:28px; font-weight:600; line-height:1; }
  .kpi .l{ margin-top:8px; font-size:12.5px; color:var(--text-dim); }
  .kpi.ok .n{ color:var(--ok); }
  .kpi.warn .n{ color:var(--warn); }
  .kpi.bad .n{ color:var(--bad); }

  section{ margin-bottom:36px; }
  section h2{
    font-size:15px; font-weight:650; margin:0 0 4px; display:flex; align-items:center; gap:9px;
  }
  section h2 .dot{ width:7px; height:7px; border-radius:50%; background:var(--guinda); flex:none; }
  section .sub{ color:var(--text-dim); font-size:13px; margin:0 0 16px; max-width:80ch; }

  .grid2{ display:grid; grid-template-columns:1.15fr .85fr; gap:20px; align-items:start; }
  @media (max-width:880px){ .grid2{ grid-template-columns:1fr; } }

  .panel{
    background:var(--panel); border:1px solid var(--line); border-radius:10px; padding:18px 20px;
  }

  table{ width:100%; border-collapse:collapse; font-size:13px; }
  th{
    text-align:left; font-weight:600; color:var(--text-dim); font-size:11.5px;
    padding:0 10px 8px; border-bottom:1px solid var(--line); white-space:nowrap;
  }
  td{ padding:9px 10px; border-bottom:1px solid var(--line); vertical-align:top; }
  tr:last-child td{ border-bottom:none; }
  td.num{ font-family:var(--mono); }
  .bar-cell{ display:flex; align-items:center; gap:8px; }
  .bar-track{ flex:1; height:6px; border-radius:3px; background:var(--panel-2); overflow:hidden; }
  .bar-fill{ height:100%; border-radius:3px; }

  .pill{
    display:inline-block; padding:3px 9px; border-radius:20px; font-size:11.5px; font-weight:600;
    white-space:nowrap;
  }
  .pill.ok{ background:var(--ok-bg); color:var(--ok); }
  .pill.warn{ background:var(--warn-bg); color:var(--warn); }
  .pill.bad{ background:var(--bad-bg); color:var(--bad); }

  .stack{ display:flex; flex-direction:column; gap:10px; }
  .item{
    border:1px solid var(--line); border-left:3px solid var(--line); border-radius:6px;
    padding:11px 13px; background:var(--panel-2);
  }
  .item.bad{ border-left-color:var(--bad); }
  .item.warn{ border-left-color:var(--warn); }
  .item .head{ display:flex; justify-content:space-between; gap:10px; align-items:baseline; }
  .item .folio{ font-family:var(--mono); font-size:12px; color:var(--text-dim); }
  .item .t{ font-weight:600; font-size:13.5px; margin:3px 0 4px; }
  .item .d{ font-size:12.5px; color:var(--text-dim); }

  .milestones{ display:flex; flex-direction:column; gap:0; }
  .ms{ display:grid; grid-template-columns:74px 1fr; gap:14px; padding:12px 0; border-bottom:1px solid var(--line); }
  .ms:last-child{ border-bottom:none; }
  .ms .time{ font-family:var(--mono); font-size:12px; color:var(--guinda-soft); padding-top:2px; white-space:pre-line; }
  .ms .body b{ font-size:13.5px; font-weight:650; }
  .ms .body .m{ font-size:12px; color:var(--text-dim); margin-top:2px; }
  .ms .body .o{ font-size:12.5px; color:var(--text); margin-top:5px; }

  .reg-stats{ display:grid; grid-template-columns:repeat(3,1fr); gap:1px; background:var(--line); border:1px solid var(--line); border-radius:8px; overflow:hidden; margin-bottom:16px; }
  .reg-stats div{ background:var(--panel-2); padding:12px 14px; }
  .reg-stats .n{ font-family:var(--mono); font-size:18px; font-weight:600; }
  .reg-stats .l{ font-size:11px; color:var(--text-dim); margin-top:3px; }

  svg text{ font-family:var(--mono); }
  .axis-line{ stroke:var(--line); stroke-width:1; }
  .grid-line{ stroke:var(--line); stroke-width:1; stroke-dasharray:2 3; opacity:.6; }
  .reg-line{ stroke:var(--guinda-soft); stroke-width:1.6; }
  .pt{ stroke:var(--bg); stroke-width:1; cursor:pointer; }
  .pt.ok{ fill:var(--ok); }
  .pt.warn{ fill:var(--warn); }
  .pt.bad{ fill:var(--bad); }
  .pt.outlier{ stroke:var(--guinda-soft); stroke-width:1.5; }

  .tooltip{
    position:fixed; pointer-events:none; background:#0a0d12; border:1px solid var(--line);
    border-radius:6px; padding:8px 10px; font-family:var(--mono); font-size:11.5px; color:var(--text);
    display:none; z-index:50; max-width:260px; line-height:1.5;
  }
  .tooltip b{ color:var(--guinda-soft); }

  .legend{ display:flex; gap:16px; font-size:11.5px; color:var(--text-dim); margin-top:10px; flex-wrap:wrap; }
  .legend span{ display:inline-flex; align-items:center; gap:6px; }
  .legend i{ width:8px; height:8px; border-radius:50%; display:inline-block; }

  .foot{
    margin-top:44px; padding-top:18px; border-top:1px solid var(--line);
    font-size:11.5px; color:var(--text-dim); display:flex; justify-content:space-between; gap:20px; flex-wrap:wrap;
  }
  .assumption{
    background:var(--warn-bg); border:1px solid rgba(214,154,45,.35); border-radius:8px;
    padding:12px 14px; font-size:12.5px; color:var(--text); margin-top:12px;
  }
  .assumption b{ color:var(--warn); }

  code{ font-family:var(--mono); background:var(--panel-2); padding:1px 5px; border-radius:4px; font-size:.92em; }
</style>
</head>
<body>
<div class="tooltip" id="tooltip"></div>
<div class="wrap">

  <header class="top">
    <div>
      <div class="id">BITÁCORA DE NOVEDADES · FOLIOS 3902–3946</div>
      <h1>Tablero de avances — control de reportes</h1>
      <p>Análisis de errores de captura, faltantes de reporte, desviaciones de estatus, hitos operativos y patrón de tiempos de la bitácora del turno.</p>
    </div>
    <div class="window">
      Ventana del corte<br>
      <b>07 sep 12:31</b> → <b>08 sep 14:14</b> (2026)
    </div>
  </header>

  <div class="kpis">
    <div class="kpi"><div class="n">45</div><div class="l">Folios registrados<br>(3902–3946)</div></div>
    <div class="kpi ok"><div class="n">42</div><div class="l">Reportado completo<br>(93.3%)</div></div>
    <div class="kpi warn"><div class="n">2</div><div class="l">Fuera de tiempo<br>(4.4%)</div></div>
    <div class="kpi bad"><div class="n">1</div><div class="l">Reporte incompleto<br>(2.2%)</div></div>
    <div class="kpi"><div class="n">16</div><div class="l">OOAD / unidades<br>con al menos 1 folio</div></div>
  </div>

  <section>
    <h2><span class="dot"></span>Errores detectados en la captura</h2>
    <p class="sub">Inconsistencias en los datos de la bitácora, independientes del estatus operativo del reporte.</p>
    <div class="stack">
      <div class="item bad">
        <div class="head"><div class="t">Año de captura incorrecto</div><div class="folio">FOLIO 3916 · TAMAULIPAS</div></div>
        <div class="d">Registrado como <code>2028-09-07</code>; por su posición en la secuencia (entre los folios 3915 y 3917, ambos del 07-sep-2026) y su hora (18:59), corresponde al reporte vespertino del <b style="color:var(--text)">07-sep-2026</b>. Error de tecleo en el año.</div>
      </div>
      <div class="item warn">
        <div class="head"><div class="t">Incidencia sin describir, dato capturado en el campo SLA</div><div class="folio">FOLIO 3920 · IMSS CENTRALES</div></div>
        <div class="d">El campo INCIDENCIA quedó vacío; la descripción del evento ("fallas en suministro de energía eléctrica") se capturó en el campo SLA en su lugar. Es el único folio del corte sin incidencia registrada en su campo correspondiente.</div>
      </div>
      <div class="item warn">
        <div class="head"><div class="t">Error de dedo en el campo SLA</div><div class="folio">FOLIO 3922 · CHIHUAHUA</div></div>
        <div class="d">"SE RETIrA PERSONAL DE CFE..." — minúscula suelta en mitad de palabra; no afecta el estatus pero conviene corregir para reportes públicos.</div>
      </div>
    </div>
  </section>

  <section class="grid2">
    <div>
      <h2><span class="dot"></span>Estatus por Estado / OOAD</h2>
      <p class="sub">Los tres OOAD con desviación concentran el 100% de los reportes fuera de estándar del corte.</p>
      <div class="panel">
        <table id="tbl-ooad"></table>
      </div>
    </div>
    <div>
      <h2><span class="dot"></span>Reportes con desviación</h2>
      <p class="sub">Detalle de los 3 folios que no cerraron como "reportado completo".</p>
      <div class="stack">
        <div class="item warn">
          <div class="head"><div class="t">Fuera de tiempo</div><div class="folio">3942 · TAMAULIPAS</div></div>
          <div class="d">Reporte de cierre del 08-sep 07:07, coordinador Ronald Hernández. Sin observaciones capturadas — confirmar causa del retraso con el coordinador.</div>
        </div>
        <div class="item warn">
          <div class="head"><div class="t">Fuera de tiempo</div><div class="folio">3945 · JALISCO</div></div>
          <div class="d">08-sep 08:39, coordinador Mario Alberto Flores Aleissa. Un minuto después del folio 3944, que reportó la defunción de un derechohabiente fuera de la unidad HGZ06.</div>
        </div>
        <div class="item bad">
          <div class="head"><div class="t">Reporte incompleto</div><div class="folio">3943 · CHIHUAHUA</div></div>
          <div class="d">08-sep 07:15, coordinador Héctor Gabriel Bolly. "Sujeto llegó intoxicado a caseta de vigilancia, al ver patrullas se retiró por voluntad propia" — evento sin cierre formal de seguimiento.</div>
        </div>
      </div>
    </div>
  </section>

  <section>
    <h2><span class="dot"></span>OOAD sin reporte en el corte</h2>
    <p class="sub">Comparando contra la estructura estándar de 35 OOAD del IMSS a nivel nacional, estos 21 no registraron folio en esta ventana de 26 horas.</p>
    <div class="panel" id="missing-panel"></div>
    <div class="assumption">
      <b>Supuesto a validar:</b> esta lista compara el corte contra el listado nacional estándar de OOAD del IMSS (32 estados + CDMX Norte/Sur + México Oriente/Poniente + Veracruz Norte/Sur), ya que el archivo no incluye un catálogo maestro de OOAD esperados. Si esta bitácora solo cubre una región o turno específico, la lista de "ausentes" debe acotarse a ese universo real.
    </div>
  </section>

  <section>
    <h2><span class="dot"></span>Hitos del turno</h2>
    <p class="sub">Eventos operativamente relevantes reportados en la ventana, en orden cronológico.</p>
    <div class="panel">
      <div class="milestones" id="milestones"></div>
    </div>
  </section>

  <section>
    <h2><span class="dot"></span>Análisis de regresión — ritmo de reporte</h2>
    <p class="sub">Regresión lineal de los minutos transcurridos desde el primer folio contra el orden de llegada (índice de folio), para estimar el ritmo esperado de captura y detectar reportes que se desviaron de ese patrón.</p>
    <div class="panel">
      <div class="reg-stats">
        <div><div class="n">26.2 min</div><div class="l">Pendiente — tiempo esperado entre folios consecutivos</div></div>
        <div><div class="n">0.952</div><div class="l">R² — ajuste del modelo lineal</div></div>
        <div><div class="n">78.2 min</div><div class="l">Desviación estándar de los residuales</div></div>
      </div>
      <svg id="chart" viewBox="0 0 1000 420" style="width:100%; height:auto; display:block;"></svg>
      <div class="legend">
        <span><i style="background:var(--ok)"></i>Reportado completo</span>
        <span><i style="background:var(--warn)"></i>Fuera de tiempo</span>
        <span><i style="background:var(--bad)"></i>Reporte incompleto</span>
        <span><i style="background:transparent;border:1.5px solid var(--guinda-soft);border-radius:50%"></i>Desviación &gt; 1.5σ del patrón esperado</span>
        <span style="border-top:1.6px solid var(--guinda-soft); width:16px; align-self:center;"></span>
        <span>&nbsp;Recta de regresión</span>
      </div>
    </div>
    <p class="sub" style="margin-top:14px;">
      <b style="color:var(--text)">Lectura:</b> el ritmo de captura es muy regular durante el turno (R²=0.95): en promedio entra un folio nuevo cada ~26 minutos. Los cinco puntos marcados como desviación no coinciden con los folios de estatus "fuera de tiempo" o "incompleto" — son huecos o adelantos en el <i>ritmo de captura</i> (p. ej. el primer incidente del día, folio 3902, y el reporte tardío de la tarde, folio 3946, tras casi 5 horas sin nuevos folios). Esto sugiere que las tres desviaciones de estatus son casos aislados de calidad de reporte, no un problema generalizado de ritmo.
    </p>
  </section>

  <div class="foot">
    <div>Fuente: bitácora de novedades, archivo <code>8--09-26.xlsx</code>, 45 folios (3902–3946).</div>
    <div>Generado para revisión operativa · datos limpiados: fechas corregidas por secuencia para el análisis de regresión.</div>
  </div>

</div>

<script>
const DATA = [{"FOLIO": 3902, "OOAD": "TAMAULIPAS", "IDX": 1, "MIN_ELAPSED": 0.0, "PREDICHO_MIN": 118.3304347826087, "RESIDUAL": -118.3304347826087, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 12:31:00"}, {"FOLIO": 3903, "OOAD": "JALISCO", "IDX": 2, "MIN_ELAPSED": 234.0, "PREDICHO_MIN": 144.5457180500659, "RESIDUAL": 89.45428194993411, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 16:25:00"}, {"FOLIO": 3904, "OOAD": "BAJA CALIFORNIA", "IDX": 3, "MIN_ELAPSED": 279.0, "PREDICHO_MIN": 170.76100131752307, "RESIDUAL": 108.23899868247692, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 17:10:00"}, {"FOLIO": 3905, "OOAD": "ZACATECAS", "IDX": 4, "MIN_ELAPSED": 329.0, "PREDICHO_MIN": 196.97628458498025, "RESIDUAL": 132.02371541501975, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:00:00"}, {"FOLIO": 3906, "OOAD": "NAYARIT", "IDX": 5, "MIN_ELAPSED": 329.0, "PREDICHO_MIN": 223.19156785243743, "RESIDUAL": 105.80843214756256, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:00:00"}, {"FOLIO": 3907, "OOAD": "AGUASCALIENTES", "IDX": 6, "MIN_ELAPSED": 333.0, "PREDICHO_MIN": 249.4068511198946, "RESIDUAL": 83.59314888010539, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:04:00"}, {"FOLIO": 3908, "OOAD": "BAJA CALIFORNIA SUR", "IDX": 7, "MIN_ELAPSED": 335.0, "PREDICHO_MIN": 275.6221343873518, "RESIDUAL": 59.37786561264818, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:06:00"}, {"FOLIO": 3909, "OOAD": "COAHUILA", "IDX": 8, "MIN_ELAPSED": 336.0, "PREDICHO_MIN": 301.837417654809, "RESIDUAL": 34.162582345191026, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:07:00"}, {"FOLIO": 3910, "OOAD": "JALISCO", "IDX": 9, "MIN_ELAPSED": 339.0, "PREDICHO_MIN": 328.0527009222661, "RESIDUAL": 10.947299077733874, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:10:00"}, {"FOLIO": 3911, "OOAD": "DURANGO", "IDX": 10, "MIN_ELAPSED": 341.0, "PREDICHO_MIN": 354.26798418972334, "RESIDUAL": -13.267984189723336, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:12:00"}, {"FOLIO": 3912, "OOAD": "SINALOA", "IDX": 11, "MIN_ELAPSED": 352.0, "PREDICHO_MIN": 380.48326745718055, "RESIDUAL": -28.483267457180546, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:23:00"}, {"FOLIO": 3913, "OOAD": "SONORA", "IDX": 12, "MIN_ELAPSED": 363.0, "PREDICHO_MIN": 406.6985507246377, "RESIDUAL": -43.6985507246377, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:34:00"}, {"FOLIO": 3914, "OOAD": "BAJA CALIFORNIA", "IDX": 13, "MIN_ELAPSED": 363.0, "PREDICHO_MIN": 432.9138339920949, "RESIDUAL": -69.91383399209485, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:34:00"}, {"FOLIO": 3915, "OOAD": "SAN LUIS POTOSÍ", "IDX": 14, "MIN_ELAPSED": 370.0, "PREDICHO_MIN": 459.12911725955206, "RESIDUAL": -89.12911725955206, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:41:00"}, {"FOLIO": 3916, "OOAD": "TAMAULIPAS", "IDX": 15, "MIN_ELAPSED": 388.0, "PREDICHO_MIN": 485.34440052700927, "RESIDUAL": -97.34440052700928, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 18:59:00"}, {"FOLIO": 3917, "OOAD": "CHIHUAHUA", "IDX": 16, "MIN_ELAPSED": 416.0, "PREDICHO_MIN": 511.5596837944664, "RESIDUAL": -95.55968379446642, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 19:27:00"}, {"FOLIO": 3918, "OOAD": "NUEVO LEÓN", "IDX": 17, "MIN_ELAPSED": 418.0, "PREDICHO_MIN": 537.7749670619236, "RESIDUAL": -119.77496706192358, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 19:29:00"}, {"FOLIO": 3919, "OOAD": "MONITOREO", "IDX": 18, "MIN_ELAPSED": 569.0, "PREDICHO_MIN": 563.9902503293808, "RESIDUAL": 5.009749670619158, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 22:00:00"}, {"FOLIO": 3920, "OOAD": "IMSS CENTRALES", "IDX": 19, "MIN_ELAPSED": 572.0, "PREDICHO_MIN": 590.205533596838, "RESIDUAL": -18.205533596837995, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 22:03:00"}, {"FOLIO": 3921, "OOAD": "CHIHUAHUA", "IDX": 20, "MIN_ELAPSED": 612.0, "PREDICHO_MIN": 616.4208168642951, "RESIDUAL": -4.420816864295148, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 22:43:00"}, {"FOLIO": 3922, "OOAD": "CHIHUAHUA", "IDX": 21, "MIN_ELAPSED": 622.0, "PREDICHO_MIN": 642.6361001317523, "RESIDUAL": -20.6361001317523, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 22:53:00"}, {"FOLIO": 3923, "OOAD": "MONITOREO", "IDX": 22, "MIN_ELAPSED": 649.0, "PREDICHO_MIN": 668.8513833992096, "RESIDUAL": -19.851383399209567, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 23:20:00"}, {"FOLIO": 3924, "OOAD": "MONITOREO", "IDX": 23, "MIN_ELAPSED": 671.0, "PREDICHO_MIN": 695.0666666666667, "RESIDUAL": -24.06666666666672, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 23:42:00"}, {"FOLIO": 3925, "OOAD": "MONITOREO", "IDX": 24, "MIN_ELAPSED": 688.0, "PREDICHO_MIN": 721.2819499341239, "RESIDUAL": -33.28194993412387, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-07 23:59:00"}, {"FOLIO": 3926, "OOAD": "MONITOREO", "IDX": 25, "MIN_ELAPSED": 707.0, "PREDICHO_MIN": 747.497233201581, "RESIDUAL": -40.49723320158103, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 00:18:00"}, {"FOLIO": 3927, "OOAD": "MONITOREO", "IDX": 26, "MIN_ELAPSED": 712.0, "PREDICHO_MIN": 773.7125164690382, "RESIDUAL": -61.71251646903818, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 00:23:00"}, {"FOLIO": 3928, "OOAD": "MONITOREO", "IDX": 27, "MIN_ELAPSED": 743.0, "PREDICHO_MIN": 799.9277997364954, "RESIDUAL": -56.92779973649544, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 00:54:00"}, {"FOLIO": 3929, "OOAD": "MONITOREO", "IDX": 28, "MIN_ELAPSED": 782.0, "PREDICHO_MIN": 826.1430830039526, "RESIDUAL": -44.1430830039526, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 01:33:00"}, {"FOLIO": 3930, "OOAD": "MONITOREO", "IDX": 29, "MIN_ELAPSED": 833.0, "PREDICHO_MIN": 852.3583662714097, "RESIDUAL": -19.35836627140975, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 02:24:00"}, {"FOLIO": 3931, "OOAD": "MONITOREO", "IDX": 30, "MIN_ELAPSED": 845.0, "PREDICHO_MIN": 878.573649538867, "RESIDUAL": -33.573649538867016, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 02:36:00"}, {"FOLIO": 3932, "OOAD": "IMSS CENTRALES", "IDX": 31, "MIN_ELAPSED": 1029.0, "PREDICHO_MIN": 904.7889328063242, "RESIDUAL": 124.21106719367585, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 05:40:00"}, {"FOLIO": 3933, "OOAD": "NUEVO LEÓN", "IDX": 32, "MIN_ELAPSED": 1035.0, "PREDICHO_MIN": 931.0042160737812, "RESIDUAL": 103.99578392621868, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 05:46:00"}, {"FOLIO": 3934, "OOAD": "NAYARIT", "IDX": 33, "MIN_ELAPSED": 1050.0, "PREDICHO_MIN": 957.2194993412384, "RESIDUAL": 92.78050065876153, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 06:01:00"}, {"FOLIO": 3935, "OOAD": "MONITOREO", "IDX": 34, "MIN_ELAPSED": 1052.0, "PREDICHO_MIN": 983.4347826086956, "RESIDUAL": 68.56521739130437, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 06:03:00"}, {"FOLIO": 3936, "OOAD": "SINALOA", "IDX": 35, "MIN_ELAPSED": 993.0, "PREDICHO_MIN": 1009.6500658761528, "RESIDUAL": -16.650065876152894, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 05:04:00"}, {"FOLIO": 3937, "OOAD": "COAHUILA", "IDX": 36, "MIN_ELAPSED": 1061.0, "PREDICHO_MIN": 1035.86534914361, "RESIDUAL": 25.134650856389957, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 06:12:00"}, {"FOLIO": 3938, "OOAD": "CHIHUAHUA", "IDX": 37, "MIN_ELAPSED": 1064.0, "PREDICHO_MIN": 1062.0806324110672, "RESIDUAL": 1.9193675889328008, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 06:15:00"}, {"FOLIO": 3939, "OOAD": "JALISCO", "IDX": 38, "MIN_ELAPSED": 1067.0, "PREDICHO_MIN": 1088.2959156785246, "RESIDUAL": -21.29591567852458, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 06:18:00"}, {"FOLIO": 3940, "OOAD": "BAJA CALIFORNIA SUR", "IDX": 39, "MIN_ELAPSED": 1099.0, "PREDICHO_MIN": 1114.5111989459815, "RESIDUAL": -15.511198945981503, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 06:50:00"}, {"FOLIO": 3941, "OOAD": "ZACATECAS", "IDX": 40, "MIN_ELAPSED": 1100.0, "PREDICHO_MIN": 1140.7264822134389, "RESIDUAL": -40.726482213438885, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 06:51:00"}, {"FOLIO": 3942, "OOAD": "TAMAULIPAS", "IDX": 41, "MIN_ELAPSED": 1116.0, "PREDICHO_MIN": 1166.9417654808958, "RESIDUAL": -50.94176548089581, "ESTATUS": "FUERA DE TIEMPO", "DATETIME": "2026-09-08 07:07:00"}, {"FOLIO": 3943, "OOAD": "CHIHUAHUA", "IDX": 42, "MIN_ELAPSED": 1124.0, "PREDICHO_MIN": 1193.1570487483532, "RESIDUAL": -69.15704874835319, "ESTATUS": "REPORTE INCOMPLETO", "DATETIME": "2026-09-08 07:15:00"}, {"FOLIO": 3944, "OOAD": "JALISCO", "IDX": 43, "MIN_ELAPSED": 1207.0, "PREDICHO_MIN": 1219.37233201581, "RESIDUAL": -12.372332015810116, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 08:38:00"}, {"FOLIO": 3945, "OOAD": "JALISCO", "IDX": 44, "MIN_ELAPSED": 1208.0, "PREDICHO_MIN": 1245.5876152832675, "RESIDUAL": -37.587615283267496, "ESTATUS": "FUERA DE TIEMPO", "DATETIME": "2026-09-08 08:39:00"}, {"FOLIO": 3946, "OOAD": "BAJA CALIFORNIA", "IDX": 45, "MIN_ELAPSED": 1543.0, "PREDICHO_MIN": 1271.8028985507249, "RESIDUAL": 271.1971014492751, "ESTATUS": "REPORTADO COMPLETO", "DATETIME": "2026-09-08 14:14:00"}];
const OOAD_SUMMARY = [{"OOAD": "CHIHUAHUA", "total": 5, "completos": 4, "fuera_tiempo": 0, "incompletos": 1, "con_desviacion": 1, "pct_completo": 80.0}, {"OOAD": "JALISCO", "total": 5, "completos": 4, "fuera_tiempo": 1, "incompletos": 0, "con_desviacion": 1, "pct_completo": 80.0}, {"OOAD": "TAMAULIPAS", "total": 3, "completos": 2, "fuera_tiempo": 1, "incompletos": 0, "con_desviacion": 1, "pct_completo": 66.7}, {"OOAD": "MONITOREO", "total": 11, "completos": 11, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "BAJA CALIFORNIA", "total": 3, "completos": 3, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "BAJA CALIFORNIA SUR", "total": 2, "completos": 2, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "COAHUILA", "total": 2, "completos": 2, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "IMSS CENTRALES", "total": 2, "completos": 2, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "NAYARIT", "total": 2, "completos": 2, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "NUEVO LEÓN", "total": 2, "completos": 2, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "SINALOA", "total": 2, "completos": 2, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "ZACATECAS", "total": 2, "completos": 2, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "AGUASCALIENTES", "total": 1, "completos": 1, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "DURANGO", "total": 1, "completos": 1, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "SAN LUIS POTOSÍ", "total": 1, "completos": 1, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}, {"OOAD": "SONORA", "total": 1, "completos": 1, "fuera_tiempo": 0, "incompletos": 0, "con_desviacion": 0, "pct_completo": 100.0}];
const MISSING = ["CAMPECHE", "CHIAPAS", "CIUDAD DE MÉXICO NORTE", "CIUDAD DE MÉXICO SUR", "COLIMA", "MÉXICO ORIENTE", "MÉXICO PONIENTE", "GUANAJUATO", "GUERRERO", "HIDALGO", "MICHOACÁN", "MORELOS", "OAXACA", "PUEBLA", "QUERÉTARO", "QUINTANA ROO", "TABASCO", "TLAXCALA", "VERACRUZ NORTE", "VERACRUZ SUR", "YUCATÁN"];
const MILESTONES = [{"hora": "07-sep\n12:31", "folio": 3902, "ooad": "TAMAULIPAS", "titulo": "Publicación en redes sobre condición de atención", "obs": "Se ubica publicación en Facebook donde se evidencia la condición de atención en la unidad (La Bandera, Nvo Laredo)."}, {"hora": "07-sep\n16:25", "folio": 3903, "ooad": "JALISCO", "titulo": "Defunción de paciente sin signos vitales", "obs": "Paciente trasladada por Guardia Nacional a UMF59, arriba sin signos vitales."}, {"hora": "07-sep\n17:10", "folio": 3904, "ooad": "BAJA CALIFORNIA", "titulo": "Código plata", "obs": "Ingresa código plata en ambulancia de Cruz Roja, UMF 38 San Luis Río Colorado."}, {"hora": "07-sep\n22:03", "folio": 3920, "ooad": "IMSS CENTRALES", "titulo": "Falla de suministro eléctrico — alerta inicial", "obs": "IMSS Centrales solicita información al coordinador de Chihuahua (HGR66, Cd. Juárez)."}, {"hora": "07-sep\n22:43", "folio": 3921, "ooad": "CHIHUAHUA", "titulo": "Falla en suministro de energía — HGR 66", "obs": "Personal de CFE atendiendo la falla en la zona."}, {"hora": "07-sep\n22:53", "folio": 3922, "ooad": "CHIHUAHUA", "titulo": "Suministro eléctrico restablecido", "obs": "Se retira personal de CFE, queda restablecido el suministro en HGR 66."}, {"hora": "08-sep\n07:15", "folio": 3943, "ooad": "CHIHUAHUA", "titulo": "Sujeto intoxicado en caseta de vigilancia", "obs": "Se retira por voluntad propia al ver patrullas; reporte quedó incompleto."}, {"hora": "08-sep\n08:38", "folio": 3944, "ooad": "JALISCO", "titulo": "Defunción tras desmayo fuera de unidad", "obs": "Muere sujeto que se desmayó fuera de la unidad HGZ06."}, {"hora": "08-sep\n14:14", "folio": 3946, "ooad": "BAJA CALIFORNIA", "titulo": "Código negro — amenaza de evacuación en guardería", "obs": "Llamada de amenaza; Fiscalía autoriza reanudar actividades a las 13:15 (Ensenada)."}];

// ---- Tabla por OOAD ----
const tbl = document.getElementById('tbl-ooad');
let thead = '<thead><tr><th>OOAD</th><th style="text-align:right">Folios</th><th>% completo</th><th style="text-align:right">Desviación</th></tr></thead>';
let rows = '';
OOAD_SUMMARY.forEach(r=>{
  const pillClass = r.con_desviacion>0 ? (r.incompletos>0 ? 'bad':'warn') : 'ok';
  const pillText = r.con_desviacion>0 ? `${r.con_desviacion} folio${r.con_desviacion>1?'s':''}` : 'sin desviación';
  const barColor = r.pct_completo>=100 ? 'var(--ok)' : (r.pct_completo>=80 ? 'var(--warn)' : 'var(--bad)');
  rows += `<tr>
    <td>${r.OOAD}</td>
    <td class="num" style="text-align:right">${r.total}</td>
    <td><div class="bar-cell"><div class="bar-track"><div class="bar-fill" style="width:${r.pct_completo}%; background:${barColor}"></div></div><span class="num" style="font-size:12px;color:var(--text-dim)">${r.pct_completo}%</span></div></td>
    <td style="text-align:right"><span class="pill ${pillClass}">${pillText}</span></td>
  </tr>`;
});
tbl.innerHTML = thead + '<tbody>' + rows + '</tbody>';

// ---- OOAD ausentes ----
const mp = document.getElementById('missing-panel');
mp.innerHTML = MISSING.map(m=>`<span class="pill bad" style="margin:3px 5px 3px 0;">${m}</span>`).join('');

// ---- Hitos ----
const ms = document.getElementById('milestones');
ms.innerHTML = MILESTONES.map(m=>`
  <div class="ms">
    <div class="time">${m.hora}</div>
    <div class="body">
      <b>${m.titulo}</b>
      <div class="m">Folio ${m.folio} · ${m.ooad}</div>
      <div class="o">${m.obs}</div>
    </div>
  </div>
`).join('');

// ---- Gráfico de regresión (SVG) ----
const svg = document.getElementById('chart');
const W=1000,H=420,ML=60,MR=20,MT=20,MB=44;
const plotW = W-ML-MR, plotH = H-MT-MB;
const xs = DATA.map(d=>d.IDX), ys = DATA.map(d=>d.MIN_ELAPSED);
const xMax = Math.max(...xs), yMax = Math.max(...ys);
const xScale = v => ML + (v/xMax)*plotW;
const yScale = v => MT + plotH - (v/yMax)*plotH;

let svgEls = '';
// grid + axes
for(let i=0;i<=5;i++){
  const yv = yMax/5*i;
  const yy = yScale(yv);
  svgEls += `<line class="grid-line" x1="${ML}" y1="${yy}" x2="${W-MR}" y2="${yy}"/>`;
  svgEls += `<text x="${ML-10}" y="${yy+4}" font-size="10" fill="var(--text-dim,#8b98a8)" text-anchor="end">${Math.round(yv/60)}h</text>`;
}
for(let i=0;i<=9;i++){
  const xv = xMax/9*i;
  const xx = xScale(xv);
  svgEls += `<text x="${xx}" y="${H-MB+18}" font-size="10" fill="var(--text-dim,#8b98a8)" text-anchor="middle">#${Math.round(xv)}</text>`;
}
svgEls += `<line class="axis-line" x1="${ML}" y1="${MT}" x2="${ML}" y2="${MT+plotH}"/>`;
svgEls += `<line class="axis-line" x1="${ML}" y1="${MT+plotH}" x2="${W-MR}" y2="${MT+plotH}"/>`;
svgEls += `<text x="${ML}" y="${H-6}" font-size="10.5" fill="var(--text-dim,#8b98a8)">Orden de llegada del folio (índice)</text>`;
svgEls += `<text x="${ML-45}" y="${MT-6}" font-size="10.5" fill="var(--text-dim,#8b98a8)">Horas desde el 1er folio</text>`;

// regression line
const x1=1, x2=xMax;
const y1 = DATA[0].PREDICHO_MIN, y2 = DATA[DATA.length-1].PREDICHO_MIN;
svgEls += `<line class="reg-line" x1="${xScale(x1)}" y1="${yScale(y1)}" x2="${xScale(x2)}" y2="${yScale(y2)}"/>`;

// points
DATA.forEach(d=>{
  const cls = d.ESTATUS==='REPORTADO COMPLETO' ? 'ok' : (d.ESTATUS==='FUERA DE TIEMPO' ? 'warn' : 'bad');
  const isOutlier = Math.abs(d.RESIDUAL) > 1.5*78.24;
  const r = isOutlier ? 6.5 : 4.5;
  svgEls += `<circle class="pt ${cls}${isOutlier?' outlier':''}" cx="${xScale(d.IDX)}" cy="${yScale(d.MIN_ELAPSED)}" r="${r}"
    data-folio="${d.FOLIO}" data-ooad="${d.OOAD}" data-fecha="${d.DATETIME}" data-estatus="${d.ESTATUS}" data-resid="${d.RESIDUAL.toFixed(1)}"/>`;
});

svg.innerHTML = svgEls;

// tooltip
const tip = document.getElementById('tooltip');
svg.querySelectorAll('.pt').forEach(el=>{
  el.addEventListener('mousemove', (e)=>{
    tip.style.display='block';
    tip.style.left = (e.clientX+14)+'px';
    tip.style.top = (e.clientY+14)+'px';
    tip.innerHTML = `<b>Folio ${el.dataset.folio}</b> · ${el.dataset.ooad}<br>${el.dataset.fecha}<br>${el.dataset.estatus}<br>Residual: ${el.dataset.resid} min`;
  });
  el.addEventListener('mouseleave', ()=>{ tip.style.display='none'; });
});
</script>
</body>
</html>
