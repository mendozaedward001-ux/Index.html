# Index.html<!doctype html>
<html lang="es">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Reylub - Propuesta de Automatización</title>
  <style>
    :root{
      --bg:#0f172a; --card:#111827; --muted:#94a3b8; --text:#e5e7eb;
      --brand:#2563eb; --brand2:#14b8a6; --warn:#f59e0b; --danger:#ef4444;
      --ok:#22c55e; --line:#1f2937;
    }
    *{box-sizing:border-box}
    body{
      margin:0; font-family:system-ui,-apple-system,Segoe UI,Roboto,Arial,sans-serif;
      background:linear-gradient(135deg,#0f172a 0%,#111827 100%); color:var(--text);
    }
    .wrap{max-width:1200px; margin:0 auto; padding:24px}
    .hero{
      background:linear-gradient(135deg,rgba(37,99,235,.24),rgba(20,184,166,.18));
      border:1px solid rgba(148,163,184,.2); border-radius:20px; padding:28px; margin-bottom:20px;
      box-shadow:0 20px 50px rgba(0,0,0,.25);
    }
    h1{margin:0 0 8px; font-size:34px}
    .sub{color:var(--muted); margin:0 0 18px; line-height:1.5}
    .grid{display:grid; gap:16px}
    .grid-4{grid-template-columns:repeat(4,minmax(0,1fr))}
    .grid-2{grid-template-columns:repeat(2,minmax(0,1fr))}
    .card{
      background:rgba(17,24,39,.95); border:1px solid rgba(148,163,184,.14);
      border-radius:16px; padding:18px;
    }
    .kpi .label{color:var(--muted); font-size:13px; margin-bottom:8px}
    .kpi .value{font-size:28px; font-weight:700}
    .kpi .small{color:var(--muted); font-size:13px; margin-top:6px}
    .section{margin-top:18px}
    .section h2{font-size:22px; margin:0 0 12px}
    .row{display:flex; gap:12px; flex-wrap:wrap}
    .pill{
      display:inline-block; padding:8px 12px; border-radius:999px; font-size:13px;
      background:#0b1220; border:1px solid rgba(148,163,184,.18); color:var(--text)
    }
    .pill.brand{background:rgba(37,99,235,.16)}
    .pill.ok{background:rgba(34,197,94,.15)}
    .pill.warn{background:rgba(245,158,11,.14)}
    .pill.danger{background:rgba(239,68,68,.14)}
    .table{
      width:100%; border-collapse:collapse; overflow:hidden; border-radius:14px; margin-top:10px
    }
    .table th,.table td{
      border-bottom:1px solid var(--line); padding:12px 10px; text-align:left; vertical-align:top;
      font-size:14px
    }
    .table th{color:#cbd5e1; font-weight:600; background:rgba(15,23,42,.6)}
    .muted{color:var(--muted)}
    .big{
      font-size:18px; font-weight:700; margin:0 0 8px
    }
    .proposal{
      background:linear-gradient(180deg,rgba(17,24,39,.98),rgba(15,23,42,.98));
      border:1px solid rgba(148,163,184,.14); border-radius:16px; padding:18px
    }
    .inputline{
      display:grid; grid-template-columns:repeat(3,minmax(0,1fr)); gap:12px; margin-top:10px
    }
    .field{display:flex; flex-direction:column; gap:6px}
    .field label{font-size:13px; color:var(--muted)}
    .field input{
      width:100%; background:#0b1220; color:var(--text); border:1px solid var(--line);
      border-radius:10px; padding:11px 12px; font-size:14px
    }
    .btns{display:flex; gap:10px; flex-wrap:wrap; margin-top:14px}
    button{
      border:0; border-radius:10px; padding:11px 14px; font-weight:700; cursor:pointer
    }
    .btn-brand{background:var(--brand); color:white}
    .btn-ghost{background:#0b1220; color:var(--text); border:1px solid var(--line)}
    .footer{color:var(--muted); font-size:13px; margin:18px 0 8px; line-height:1.5}
    .note{
      padding:12px 14px; background:rgba(20,184,166,.10); border:1px solid rgba(20,184,166,.18);
      border-radius:12px; color:#d1fae5
    }
    @media (max-width:900px){
      .grid-4,.grid-2,.inputline{grid-template-columns:1fr}
      h1{font-size:28px}
      .kpi .value{font-size:24px}
    }
    @media print{
      body{background:white; color:black}
      .hero,.card,.proposal{background:white; color:black; box-shadow:none}
      .pill,.btns, .no-print{display:none !important}
      .table th{background:#f3f4f6; color:black}
      .muted,.footer{color:#444}
    }
  </style>
</head>
<body>
  <div class="wrap">
    <div class="hero">
      <h1>🔧 Reylub</h1>
      <p class="sub">
        Propuesta de automatización de cobranza para distribuidora de lubricantes y filtros.
        Pensado para presentar al jefe, mostrar en navegador y luego imprimir a PDF.
      </p>

      <div class="row">
        <span class="pill brand">📍 Mérida - El Vigía</span>
        <span class="pill">👥 200+ clientes</span>
        <span class="pill">💵 Créditos: $20 a $500</span>
        <span class="pill">📊 BCV + Binance P2P</span>
        <span class="pill">📱 WhatsApp Business</span>
      </div>
    </div>

    <div class="grid grid-4">
      <div class="card kpi">
        <div class="label">📈 Tasa BCV</div>
        <div class="value" id="bcvView">587.41 Bs/$</div>
        <div class="small">Editable según el día</div>
      </div>
      <div class="card kpi">
        <div class="label">📊 Tasa Binance P2P</div>
        <div class="value" id="binanceView">- Bs/$</div>
        <div class="small">Colócala manualmente</div>
      </div>
      <div class="card kpi">
        <div class="label">💰 Cartera simulada</div>
        <div class="value">$8,450</div>
        <div class="small">Lubricantes y filtros</div>
      </div>
      <div class="card kpi">
        <div class="label">⏱️ Cobranza mejorada</div>
        <div class="value">7-15 días</div>
        <div class="small">En vez de 2-3 meses</div>
      </div>
    </div>

    <div class="section grid grid-2">
      <div class="card">
        <div class="big">❌ Problema actual</div>
        <ul class="muted">
          <li>Registro manual en cuaderno y Excel.</li>
          <li>Seguimiento de clientes vencidos consume tiempo.</li>
          <li>El jefe cobra manualmente y olvida casos pequeños.</li>
          <li>Conversión BCV / Binance se hace a mano.</li>
          <li>No hay alertas automáticas ni recordatorios.</li>
          <li>Clientes tardan 2-3 meses para pagar.</li>
          <li>Capital congelado en deudas vencidas.</li>
        </ul>
      </div>

      <div class="card">
        <div class="big">✅ Solución propuesta</div>
        <ul class="muted">
          <li>Leer Excel exportado desde A2 automáticamente.</li>
          <li>Buscar cliente por nombre, RIF o teléfono.</li>
          <li>Mostrar productos, montos, vencimiento y estado.</li>
          <li>Enviar recordatorios por WhatsApp Business.</li>
          <li>Dashboard en tiempo real para ver cartera.</li>
          <li>Conversión automática BCV + Binance P2P.</li>
          <li>Recuperación en 7-15 días (no 2-3 meses).</li>
        </ul>
      </div>
    </div>

    <div class="section proposal">
      <h2>📊 Demo visual del dashboard</h2>
      <p class="muted">Esto es lo que el jefe vería al entrar al navegador. Edita las tasas y presiona "Actualizar".</p>

      <div class="inputline no-print">
        <div class="field">
          <label>💵 Tasa BCV (editable)</label>
          <input id="bcv" type="number" step="0.01" value="587.41">
        </div>
        <div class="field">
          <label>📊 Tasa Binance P2P</label>
          <input id="binance" type="number" step="0.01" value="570.00">
        </div>
        <div class="field">
          <label>🎁 Demo por encargo ($)</label>
          <input id="demoUsd" type="number" step="1" value="50">
        </div>
      </div>

      <div class="btns no-print">
        <button class="btn-brand" onclick="updateRates()">🔄 Actualizar tasas</button>
        <button class="btn-ghost" onclick="window.print()">📄 Imprimir / PDF</button>
      </div>

      <table class="table" aria-label="dashboard">
        <thead>
          <tr>
            <th>Cliente / Taller</th>
            <th>Producto</th>
            <th>Deuda (USD / Bs)</th>
            <th>Vence</th>
            <th>Estado</th>
            <th>Acción</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>Transportes El Vigía</td>
            <td>Mobil 15W-40 (4L) x2 + Filtro Wix</td>
            <td>$320 / <span class="bs1"></span></td>
            <td>7 días</td>
            <td><span class="pill warn">⏰ Por vencer</span></td>
            <td>📱 WhatsApp</td>
          </tr>
          <tr>
            <td>Taller La Ruta</td>
            <td>Castrol GTX (1L) x3 + Filtro Tectfil</td>
            <td>$180 / <span class="bs2"></span></td>
            <td>15 días</td>
            <td><span class="pill brand">📊 Seguimiento</span></td>
            <td>📱 WhatsApp</td>
          </tr>
          <tr>
            <td>Servicio Diesel Rey</td>
            <td>Shell Helix (1L) x5 + Filtro Millar</td>
            <td>$500 / <span class="bs3"></span></td>
            <td>32 días</td>
            <td><span class="pill danger">🔴 Vencido</span></td>
            <td>☎️ Llamada</td>
          </tr>
          <tr>
            <td>Vulcanizadora La Rápida</td>
            <td>Mobil 1 Synthetic (1L) x2</td>
            <td>$280 / <span class="bs4"></span></td>
            <td>3 días</td>
            <td><span class="pill warn">⚠️ Crítico</span></td>
            <td>📱 WhatsApp</td>
          </tr>
        </tbody>
      </table>
    </div>

    <div class="section grid grid-2">
      <div class="card">
        <div class="big">💰 Paquetes de venta</div>
        <p class="muted">
          <strong>🎯 Demo:</strong><br/>
          $50 único para mostrar el sistema con datos reales de Reylub.
        </p>
        <p class="muted">
          <strong>📋 Implementación Básica:</strong><br/>
          $250 - $350. Incluye dashboard, alertas WhatsApp, conversión de tasas.
        </p>
        <p class="muted">
          <strong>⭐ Implementación Completa:</strong><br/>
          $500 - $800. Todo lo anterior + reportes, análisis, soporte 3 meses.
        </p>
        <p class="muted">
          <strong>🔧 Mantenimiento mensual:</strong><br/>
          $25 - $50 según el plan.
        </p>
      </div>

      <div class="card">
        <div class="big">💡 Recomendación para Reylub</div>
        <p class="muted">
          <strong>Fase 1:</strong> Cobrar una demo de <span id="demoShow">$50</span> para validar interés.
          Usar ese ingreso para comprar Claude Pro, hosting y herramientas.
        </p>
        <p class="muted">
          <strong>Fase 2:</strong> Hacer la implementación real con datos de Reylub.
          Cobrar $250 - $500 según complejidad.
        </p>
        <p class="muted">
          <strong>Fase 3:</strong> Ofrecer soporte mensual ($25-$50).
          La propuesta queda lista para escalar a automatización total.
        </p>
        <div class="note">
          Con la demo validada y datos reales, el jefe verá el ROI en 1-2 meses. Luego es puro ingreso pasivo.
        </div>
      </div>
    </div>

    <div class="section card">
      <h2>📈 Proyección de ROI (6 meses)</h2>
      <div class="grid grid-2">
        <div>
          <p class="muted"><strong>Situación actual:</strong></p>
          <ul class="muted">
            <li>Cartera: $8,450</li>
            <li>Tiempo de cobro: 60 días</li>
            <li>Deudas vencidas: $3,200 (37.9%)</li>
            <li>Recuperación/mes: ~$800</li>
          </ul>
        </div>
        <div>
          <p class="muted"><strong>Con sistema:</strong></p>
          <ul class="muted">
            <li>Cartera: $8,450</li>
            <li>Tiempo de cobro: 15-20 días</li>
            <li>Deudas vencidas: ~5% (controladas)</li>
            <li>Recuperación/mes: ~$2,100</li>
          </ul>
        </div>
      </div>
      <p class="muted" style="margin-top: 16px; padding-top: 16px; border-top: 1px solid var(--line);">
        <strong>Incremento: +$1,300/mes × 6 meses = +$7,800 USD</strong><br/>
        Inversión: $500. Retorno: 1,560% en 6 meses.
      </p>
    </div>

    <p class="footer">
      📌 Nota: La tasa BCV cambia diariamente. La tasa Binance P2P también varía según P2P. 
      Este documento está diseñado para presentarse en navegador y exportarse a PDF sin instalar nada.
      <br/>
      👉 Para imprimir a PDF: Presiona Ctrl+P o click derecho → Imprimir.
    </p>
  </div>

  <script>
    function money(v){
      return new Intl.NumberFormat('es-VE', {maximumFractionDigits:0}).format(v) + ' Bs';
    }
    function updateRates(){
      const bcv = parseFloat(document.getElementById('bcv').value || '587.41');
      const binance = parseFloat(document.getElementById('binance').value || '570');
      const demo = parseFloat(document.getElementById('demoUsd').value || '50');
      
      document.getElementById('bcvView').textContent = bcv.toFixed(2) + ' Bs/$';
      document.getElementById('binanceView').textContent = binance.toFixed(2) + ' Bs/$';
      document.getElementById('demoShow').textContent = '$' + demo;
      
      document.querySelector('.bs1').textContent = money(320 * bcv);
      document.querySelector('.bs2').textContent = money(180 * bcv);
      document.querySelector('.bs3').textContent = money(500 * bcv);
      document.querySelector('.bs4').textContent = money(280 * bcv);
    }
    updateRates();
  </script>
</body>
</html>
