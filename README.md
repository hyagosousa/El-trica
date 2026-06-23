
<!DOCTYPE html><html lang="en"><head><meta charSet="utf-8"/><meta name="viewport" content="width=device-width, initial-scale=1"/><link rel="stylesheet" href="/assets/styles-CYIZIhWe.css" data-precedence="default"/><title>Dashboard Fase Elétrica - Globe</title><meta name="author" content="Lovable"/><meta property="og:title" content="Lovable App"/><meta property="og:description" content="Lovable Generated Project"/><meta property="og:type" content="website"/><meta name="twitter:card" content="summary"/><meta name="twitter:site" content="@Lovable"/><meta name="description" content="Controle de tarefas e manutenções da fase elétrica."/><link rel="modulepreload" href="/assets/index-BylCRYgt.js"/><link rel="modulepreload" href="/assets/routes-Wb7xjRfm.js"/>
<style>
	@font-face {
		font-family: 'CameraPlainVariable';
		src: url('https://cdn.gpteng.co/mcp-widgets/v1/fonts/CameraPlainVariable.woff2') format('woff2');
		font-weight: 100 900;
		font-style: normal;
		font-display: swap;
	}

	#lovable-badge {
		--badge-bg: #1b1b1b;
		--badge-text: #c5c1b9;
		--badge-text-hover: #dcdad5;
		--badge-radius: 6px;
		--badge-padding: 8px;
		--badge-gap: 6px;
		--badge-shadow: 
			0 0 0 1px rgba(0, 0, 0, 0.88),
			0 1px 0 0 rgba(0, 0, 0, 0.04),
			0 2px 2px -1px rgba(0, 0, 0, 0.08),
			0 4px 4px -2px rgba(0, 0, 0, 0.08),
			0 8px 8px -4px rgba(0, 0, 0, 0.08),
			0 16px 16px -8px rgba(0, 0, 0, 0.08);
		--badge-transition-duration: 0.2s;
		--badge-transition-easing: cubic-bezier(0.16, 1, 0.32, 1);
		--focus-color: #575ECF;
		--focus-offset: 2px;
		--focus-width: 2px;
		
		position: fixed;
		bottom: 12px;
		right: 12px;
		height: 24px;
		display: flex;
		align-items: center;
		z-index: 1000000;
		background-color: var(--badge-bg) !important;
		color: var(--badge-text) !important;
		border-radius: var(--badge-radius);
		box-shadow: var(--badge-shadow) !important;
		font-size: 12px;
		font-family: CameraPlainVariable, "CameraPlainVariable Fallback", -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
		font-weight: 400 !important;
		text-transform: none !important;
		font-feature-settings: normal !important;
		transform: translateZ(0);
		will-change: transform, opacity;
	}

	#lovable-badge-cta {
		display: flex;
		align-items: center;
		gap: var(--badge-gap);
		padding: 0 var(--badge-padding);
		height: 100%;
		color: inherit;
		text-decoration: none;
		white-space: nowrap;
		border-radius: var(--badge-radius) 0 0 var(--badge-radius);
		transition: 
			background-color var(--badge-transition-duration) ease,
			color var(--badge-transition-duration) ease,
			transform 0.1s ease;
	}

	#lovable-badge-cta:hover {
		background: rgba(255, 255, 255, 0.04);
		color: var(--badge-text-hover);
	}

	#lovable-badge-cta:active {
		transform: scale(0.98);
	}

	#lovable-badge-cta:focus {
		outline: none;
	}

	#lovable-badge-cta:focus-visible {
		outline: var(--focus-width) solid var(--focus-color);
		outline-offset: var(--focus-offset);
		z-index: 1;
	}

	#lovable-badge-text {
		line-height: 1;
	}

	#lovable-badge-divider {
		width: 1px;
		height: 24px;
		background-color: rgba(255, 255, 255, 0.04);
		flex-shrink: 0;
	}

	#lovable-badge-close {
		width: 24px;
		height: 24px;
		min-width: 24px;
		min-height: 24px;
		cursor: pointer;
		background: none;
		border: none;
		padding: 0;
		display: flex;
		align-items: center;
		justify-content: center;
		border-radius: 0 var(--badge-radius) var(--badge-radius) 0;
		flex-shrink: 0;
		transition: 
			background-color var(--badge-transition-duration) ease,
			transform 0.1s ease;
	}

	#lovable-badge-close:hover {
		background: rgba(255, 255, 255, 0.04);
	}

	#lovable-badge-close:active {
		transform: scale(0.92);
	}

	#lovable-badge-close:focus {
		outline: none;
	}

	#lovable-badge-close:focus-visible {
		outline: var(--focus-width) solid var(--focus-color);
		outline-offset: calc(var(--focus-offset) * -1);
		z-index: 1;
	}

	#lovable-badge-close svg path {
		fill: var(--badge-text);
		transition: fill var(--badge-transition-duration) ease;
	}

	#lovable-badge-close:hover svg path {
		fill: var(--badge-text-hover);
	}

	@media (prefers-reduced-motion: reduce) {
		#lovable-badge-cta,
		#lovable-badge-close,
		#lovable-badge-close svg path {
			transition: none;
		}
		
		#lovable-badge-cta:active,
		#lovable-badge-close:active {
			transform: none;
		}
	}

	@media (prefers-contrast: high) {
		#lovable-badge {
			--badge-bg: #000;
			--badge-text: #fff;
			--badge-text-hover: #fff;
			border: 2px solid currentColor;
		}
		
		#lovable-badge-cta:focus-visible,
		#lovable-badge-close:focus-visible {
			outline-width: 3px;
		}
	}
</style>
<script defer src="/__l5e/events.js" data-artifact-kind="static_preview" data-artifact-id="e08e17b4d4010f96b4e600e8c7b08781633ab557" data-commit-sha="e08e17b4d4010f96b4e600e8c7b08781633ab557" data-context-token="v1.eyJwcm9qZWN0X2lkIjoiNzQxNmZmOTQtZDY5ZC00OTdhLWFkMDItMzJhYzViNjM1ZTE5IiwiYXJ0aWZhY3Rfa2luZCI6InN0YXRpY19wcmV2aWV3IiwiYXJ0aWZhY3RfaWQiOiJlMDhlMTdiNGQ0MDEwZjk2YjRlNjAwZThjN2IwODc4MTYzM2FiNTU3IiwiY29tbWl0X3NoYSI6ImUwOGUxN2I0ZDQwMTBmOTZiNGU2MDBlOGM3YjA4NzgxNjMzYWI1NTciLCJleHAiOjE3ODIxNzgyNzV9.qq58qToqdpHVujRTUHs2TuquRsCoxcR11SVace3OZYw" data-track-url="/__l5e/trackevents?__lovable_sha=e08e17b4d4010f96b4e600e8c7b08781633ab557" data-replay="rrweb" data-replay-sample-rate="1" data-replay-crash-sample-rate="1" data-replay-url="/__l5e/replay?__lovable_sha=e08e17b4d4010f96b4e600e8c7b08781633ab557" data-replay-script-url="/__l5e/rrweb-record.js?__lovable_sha=e08e17b4d4010f96b4e600e8c7b08781633ab557&amp;__l5e_v=0.1.2-error-event-hardening"></script><meta name="twitter:title" content="Lovable App"><meta name="twitter:description" content="Lovable Generated Project"><meta property="og:image" content="https://pub-bb2e103a32db4e198524a2e9ed8f35b4.r2.dev/ba59a421-1130-4520-97ee-2a6393d3819f/id-preview-e08e17b4--7416ff94-d69d-497a-ad02-32ac5b635e19.lovable.app-1782173829854.png"><meta name="twitter:image" content="https://pub-bb2e103a32db4e198524a2e9ed8f35b4.r2.dev/ba59a421-1130-4520-97ee-2a6393d3819f/id-preview-e08e17b4--7416ff94-d69d-497a-ad02-32ac5b635e19.lovable.app-1782173829854.png"></head><body><!--$--><iframe title="Dashboard" srcDoc="&lt;!DOCTYPE html&gt;
&lt;html lang=&quot;pt-BR&quot;&gt;
&lt;head&gt;
&lt;meta charset=&quot;UTF-8&quot;&gt;
&lt;title&gt;Dashboard Fase Elétrica - Globe&lt;/title&gt;
&lt;meta name=&quot;viewport&quot; content=&quot;width=device-width,initial-scale=1&quot;&gt;
&lt;script src=&quot;https://cdn.jsdelivr.net/npm/chart.js@4.4.1/dist/chart.umd.min.js&quot;&gt;&lt;/script&gt;
&lt;script src=&quot;https://cdn.jsdelivr.net/npm/chartjs-adapter-date-fns/dist/chartjs-adapter-date-fns.bundle.min.js&quot;&gt;&lt;/script&gt;
&lt;style&gt;
:root{--bg:#0b1220;--panel:#121a2e;--panel2:#172142;--border:#243056;--text:#e6ecff;--muted:#8da0c7;
--accent:#3b82f6;--ok:#22c55e;--warn:#f59e0b;--bad:#ef4444;--info:#06b6d4;--purple:#a855f7;}
*{box-sizing:border-box}
body{margin:0;font-family:-apple-system,BlinkMacSystemFont,&quot;Segoe UI&quot;,Roboto,sans-serif;background:var(--bg);color:var(--text);font-size:14px}
header{padding:18px 28px;background:linear-gradient(135deg,#0f1a35,#1e1148);border-bottom:1px solid var(--border);display:flex;justify-content:space-between;align-items:center;flex-wrap:wrap;gap:12px}
header h1{margin:0;font-size:20px}
header .sub{color:var(--muted);font-size:12px;margin-top:4px}
.btn{background:var(--accent);color:#fff;border:0;padding:9px 14px;border-radius:8px;font-weight:600;cursor:pointer;font-size:13px}
.btn:hover{background:#2563eb}
.btn.ghost{background:var(--panel2);border:1px solid var(--border)}
.btn.danger{background:var(--bad)}
.btn.ok{background:var(--ok)}
.tabs{display:flex;gap:6px;padding:0 28px;background:var(--panel);border-bottom:1px solid var(--border);flex-wrap:wrap}
.tab{padding:14px 18px;cursor:pointer;color:var(--muted);font-weight:600;border-bottom:3px solid transparent;font-size:13px}
.tab.active{color:var(--text);border-color:var(--accent)}
.container{padding:20px 28px;max-width:1600px;margin:0 auto}
.view{display:none}.view.active{display:block}
.filters,.formgrid{background:var(--panel);border:1px solid var(--border);border-radius:12px;padding:16px;margin-bottom:20px;display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:12px}
label{display:flex;flex-direction:column;gap:6px;font-size:11px;color:var(--muted);text-transform:uppercase;letter-spacing:.5px}
select,input,textarea{background:var(--panel2);border:1px solid var(--border);color:var(--text);padding:8px 10px;border-radius:8px;font-size:13px;outline:none;font-family:inherit}
select:focus,input:focus,textarea:focus{border-color:var(--accent)}
.formgrid .full{grid-column:1/-1}
.formgrid .actions{display:flex;gap:10px;align-items:end;flex-wrap:wrap}
.kpis{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:14px;margin-bottom:20px}
.kpi{background:var(--panel);border:1px solid var(--border);border-radius:12px;padding:16px;position:relative;overflow:hidden}
.kpi::before{content:&quot;&quot;;position:absolute;left:0;top:0;bottom:0;width:4px;background:var(--accent)}
.kpi.ok::before{background:var(--ok)}.kpi.warn::before{background:var(--warn)}
.kpi.bad::before{background:var(--bad)}.kpi.info::before{background:var(--info)}.kpi.purple::before{background:var(--purple)}
.kpi .label{font-size:11px;color:var(--muted);text-transform:uppercase;margin-bottom:8px}
.kpi .value{font-size:26px;font-weight:700}
.kpi .hint{font-size:11px;color:var(--muted);margin-top:4px}
.grid{display:grid;grid-template-columns:repeat(12,1fr);gap:16px}
.card{background:var(--panel);border:1px solid var(--border);border-radius:12px;padding:16px}
.card h3{margin:0 0 12px 0;font-size:14px;font-weight:600}
.c-12{grid-column:span 12}.c-8{grid-column:span 8}.c-6{grid-column:span 6}.c-4{grid-column:span 4}
@media(max-width:1100px){.c-8,.c-6,.c-4{grid-column:span 12}}
.chart-wrap{position:relative;height:280px}
table{width:100%;border-collapse:collapse;font-size:12px}
th,td{padding:8px 10px;text-align:left;border-bottom:1px solid var(--border)}
th{color:var(--muted);text-transform:uppercase;font-size:10px;background:var(--panel)}
.scroll{max-height:480px;overflow:auto}
.badge{padding:2px 8px;border-radius:10px;font-size:11px;font-weight:600;white-space:nowrap}
.b-ok{background:rgba(34,197,94,.15);color:#4ade80}
.b-warn{background:rgba(245,158,11,.15);color:#fbbf24}
.b-bad{background:rgba(239,68,68,.15);color:#f87171}
.b-info{background:rgba(6,182,212,.15);color:#22d3ee}
.b-muted{background:rgba(100,116,139,.2);color:#94a3b8}
.b-purple{background:rgba(168,85,247,.18);color:#c084fc}
.empty{text-align:center;padding:40px;color:var(--muted)}
.toolbar{display:flex;gap:10px;margin-bottom:14px;flex-wrap:wrap}
.row-actions button{background:transparent;border:0;color:var(--muted);cursor:pointer;font-size:14px;padding:2px 6px}
.row-actions button:hover{color:var(--text)}
.toast{position:fixed;bottom:24px;right:24px;background:var(--ok);color:#fff;padding:12px 18px;border-radius:8px;font-weight:600;opacity:0;transform:translateY(10px);transition:.25s;z-index:1000}
.toast.show{opacity:1;transform:translateY(0)}
.toast.err{background:var(--bad)}
footer{text-align:center;padding:24px;color:var(--muted);font-size:11px}
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;

&lt;header&gt;
  &lt;div&gt;
    &lt;h1&gt;⚡ Dashboard Fase Elétrica - Globe&lt;/h1&gt;
    &lt;div class=&quot;sub&quot;&gt;Entrada manual · Persistência local · Tarefas + Manutenções de veículos&lt;/div&gt;
  &lt;/div&gt;
  &lt;div style=&quot;display:flex;gap:8px;flex-wrap:wrap&quot;&gt;
    &lt;button class=&quot;btn ghost&quot; onclick=&quot;exportJSON()&quot;&gt;⬇ Exportar JSON&lt;/button&gt;
    &lt;button class=&quot;btn ghost&quot; onclick=&quot;document.getElementById(&#x27;imp&#x27;).click()&quot;&gt;⬆ Importar&lt;/button&gt;
    &lt;input id=&quot;imp&quot; type=&quot;file&quot; accept=&quot;.json&quot; style=&quot;display:none&quot; onchange=&quot;importJSON(event)&quot;&gt;
    &lt;button class=&quot;btn ok&quot; onclick=&quot;seed()&quot;&gt;🎲 Dados de exemplo&lt;/button&gt;
    &lt;button class=&quot;btn danger&quot; onclick=&quot;clearAll()&quot;&gt;🗑 Limpar tudo&lt;/button&gt;
  &lt;/div&gt;
&lt;/header&gt;

&lt;div class=&quot;tabs&quot;&gt;
  &lt;div class=&quot;tab active&quot; data-tab=&quot;entry&quot;&gt;📝 Tarefas&lt;/div&gt;
  &lt;div class=&quot;tab&quot; data-tab=&quot;maint&quot;&gt;🔧 Manutenções&lt;/div&gt;
  &lt;div class=&quot;tab&quot; data-tab=&quot;dash&quot;&gt;📊 Dashboard&lt;/div&gt;
&lt;/div&gt;

&lt;div class=&quot;container&quot;&gt;

&lt;!-- ============ TAREFAS ============ --&gt;
&lt;div class=&quot;view active&quot; id=&quot;view-entry&quot;&gt;
  &lt;div class=&quot;formgrid&quot;&gt;
    &lt;label&gt;Veículo (chassi/código)&lt;input id=&quot;t_vehicle&quot; placeholder=&quot;ex: GLB-001&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Fase&lt;select id=&quot;t_phase&quot;&gt;&lt;option&gt;Fase 1&lt;/option&gt;&lt;option&gt;Fase 2&lt;/option&gt;&lt;option&gt;Fase 3&lt;/option&gt;&lt;/select&gt;&lt;/label&gt;
    &lt;label&gt;Tarefa&lt;input id=&quot;t_task&quot; placeholder=&quot;ex: Montagem chicote&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Responsável&lt;input id=&quot;t_resp&quot; placeholder=&quot;ex: João&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Previsto - início&lt;input type=&quot;date&quot; id=&quot;t_pi&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Previsto - fim&lt;input type=&quot;date&quot; id=&quot;t_pf&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Real - início&lt;input type=&quot;date&quot; id=&quot;t_ri&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Real - fim&lt;input type=&quot;date&quot; id=&quot;t_rf&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Status&lt;select id=&quot;t_status&quot;&gt;&lt;option&gt;Não iniciado&lt;/option&gt;&lt;option&gt;Em andamento&lt;/option&gt;&lt;option&gt;Concluído&lt;/option&gt;&lt;option&gt;Atrasado&lt;/option&gt;&lt;/select&gt;&lt;/label&gt;
    &lt;label&gt;Rubrica&lt;select id=&quot;t_rub&quot;&gt;&lt;option&gt;Não&lt;/option&gt;&lt;option&gt;Sim&lt;/option&gt;&lt;/select&gt;&lt;/label&gt;
    &lt;label class=&quot;full&quot;&gt;Observação&lt;textarea id=&quot;t_obs&quot; rows=&quot;2&quot;&gt;&lt;/textarea&gt;&lt;/label&gt;
    &lt;div class=&quot;full actions&quot;&gt;
      &lt;button class=&quot;btn&quot; onclick=&quot;saveTask()&quot;&gt;💾 Salvar tarefa&lt;/button&gt;
      &lt;button class=&quot;btn ghost&quot; onclick=&quot;resetTaskForm()&quot;&gt;Limpar&lt;/button&gt;
      &lt;input type=&quot;hidden&quot; id=&quot;t_id&quot;&gt;
    &lt;/div&gt;
  &lt;/div&gt;

  &lt;div class=&quot;card&quot;&gt;
    &lt;div class=&quot;toolbar&quot;&gt;
      &lt;input id=&quot;t_search&quot; placeholder=&quot;🔎 buscar...&quot; oninput=&quot;renderTasks()&quot; style=&quot;flex:1;min-width:200px&quot;&gt;
    &lt;/div&gt;
    &lt;div class=&quot;scroll&quot;&gt;
      &lt;table id=&quot;tbl_tasks&quot;&gt;
        &lt;thead&gt;&lt;tr&gt;&lt;th&gt;Veículo&lt;/th&gt;&lt;th&gt;Fase&lt;/th&gt;&lt;th&gt;Tarefa&lt;/th&gt;&lt;th&gt;Resp.&lt;/th&gt;&lt;th&gt;Prev. fim&lt;/th&gt;&lt;th&gt;Real fim&lt;/th&gt;&lt;th&gt;Status&lt;/th&gt;&lt;th&gt;Atraso&lt;/th&gt;&lt;th&gt;&lt;/th&gt;&lt;/tr&gt;&lt;/thead&gt;
        &lt;tbody&gt;&lt;/tbody&gt;
      &lt;/table&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;

&lt;!-- ============ MANUTENÇÕES ============ --&gt;
&lt;div class=&quot;view&quot; id=&quot;view-maint&quot;&gt;
  &lt;div class=&quot;kpis&quot; id=&quot;kpis_maint&quot;&gt;&lt;/div&gt;

  &lt;div class=&quot;formgrid&quot;&gt;
    &lt;label&gt;Veículo&lt;input id=&quot;m_vehicle&quot; placeholder=&quot;ex: GLB-001&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Tipo de manutenção&lt;select id=&quot;m_type&quot;&gt;
      &lt;option&gt;Preventiva&lt;/option&gt;&lt;option&gt;Corretiva&lt;/option&gt;&lt;option&gt;Preditiva&lt;/option&gt;&lt;option&gt;Revisão&lt;/option&gt;&lt;option&gt;Outro&lt;/option&gt;
    &lt;/select&gt;&lt;/label&gt;
    &lt;label&gt;Data de entrada&lt;input type=&quot;date&quot; id=&quot;m_in&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Data de saída prevista&lt;input type=&quot;date&quot; id=&quot;m_outp&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Data de saída real&lt;input type=&quot;date&quot; id=&quot;m_outr&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Responsável&lt;input id=&quot;m_resp&quot; placeholder=&quot;ex: Oficina A / Carlos&quot;&gt;&lt;/label&gt;
    &lt;label&gt;Status&lt;select id=&quot;m_status&quot;&gt;
      &lt;option&gt;Aguardando&lt;/option&gt;&lt;option&gt;Em manutenção&lt;/option&gt;&lt;option&gt;Aguardando peça&lt;/option&gt;&lt;option&gt;Concluída&lt;/option&gt;&lt;option&gt;Cancelada&lt;/option&gt;
    &lt;/select&gt;&lt;/label&gt;
    &lt;label&gt;Prioridade&lt;select id=&quot;m_prio&quot;&gt;&lt;option&gt;Baixa&lt;/option&gt;&lt;option&gt;Média&lt;/option&gt;&lt;option&gt;Alta&lt;/option&gt;&lt;option&gt;Crítica&lt;/option&gt;&lt;/select&gt;&lt;/label&gt;
    &lt;label class=&quot;full&quot;&gt;Descrição / serviço&lt;textarea id=&quot;m_desc&quot; rows=&quot;2&quot; placeholder=&quot;ex: troca de cabo de bateria, revisão chicote...&quot;&gt;&lt;/textarea&gt;&lt;/label&gt;
    &lt;div class=&quot;full actions&quot;&gt;
      &lt;button class=&quot;btn&quot; onclick=&quot;saveMaint()&quot;&gt;💾 Salvar manutenção&lt;/button&gt;
      &lt;button class=&quot;btn ghost&quot; onclick=&quot;resetMaintForm()&quot;&gt;Limpar&lt;/button&gt;
      &lt;input type=&quot;hidden&quot; id=&quot;m_id&quot;&gt;
    &lt;/div&gt;
  &lt;/div&gt;

  &lt;div class=&quot;card&quot;&gt;
    &lt;div class=&quot;toolbar&quot;&gt;
      &lt;input id=&quot;m_search&quot; placeholder=&quot;🔎 buscar...&quot; oninput=&quot;renderMaints()&quot; style=&quot;flex:1;min-width:200px&quot;&gt;
      &lt;select id=&quot;m_fstatus&quot; onchange=&quot;renderMaints()&quot;&gt;
        &lt;option value=&quot;&quot;&gt;Todos status&lt;/option&gt;
        &lt;option&gt;Aguardando&lt;/option&gt;&lt;option&gt;Em manutenção&lt;/option&gt;&lt;option&gt;Aguardando peça&lt;/option&gt;&lt;option&gt;Concluída&lt;/option&gt;&lt;option&gt;Cancelada&lt;/option&gt;
      &lt;/select&gt;
    &lt;/div&gt;
    &lt;div class=&quot;scroll&quot;&gt;
      &lt;table id=&quot;tbl_maints&quot;&gt;
        &lt;thead&gt;&lt;tr&gt;
          &lt;th&gt;Veículo&lt;/th&gt;&lt;th&gt;Tipo&lt;/th&gt;&lt;th&gt;Entrada&lt;/th&gt;&lt;th&gt;Saída prev.&lt;/th&gt;&lt;th&gt;Saída real&lt;/th&gt;
          &lt;th&gt;Resp.&lt;/th&gt;&lt;th&gt;Prio.&lt;/th&gt;&lt;th&gt;Status&lt;/th&gt;&lt;th&gt;Dias parado&lt;/th&gt;&lt;th&gt;Atraso&lt;/th&gt;&lt;th&gt;&lt;/th&gt;
        &lt;/tr&gt;&lt;/thead&gt;
        &lt;tbody&gt;&lt;/tbody&gt;
      &lt;/table&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;

&lt;!-- ============ DASHBOARD ============ --&gt;
&lt;div class=&quot;view&quot; id=&quot;view-dash&quot;&gt;
  &lt;div class=&quot;kpis&quot; id=&quot;kpis_dash&quot;&gt;&lt;/div&gt;
  &lt;div class=&quot;grid&quot;&gt;
    &lt;div class=&quot;card c-6&quot;&gt;&lt;h3&gt;🎯 % por Fase&lt;/h3&gt;&lt;div class=&quot;chart-wrap&quot;&gt;&lt;canvas id=&quot;chPhase&quot;&gt;&lt;/canvas&gt;&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;card c-6&quot;&gt;&lt;h3&gt;🚦 Status Geral (tarefas)&lt;/h3&gt;&lt;div class=&quot;chart-wrap&quot;&gt;&lt;canvas id=&quot;chStatus&quot;&gt;&lt;/canvas&gt;&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;card c-6&quot;&gt;&lt;h3&gt;🔧 Status das Manutenções&lt;/h3&gt;&lt;div class=&quot;chart-wrap&quot;&gt;&lt;canvas id=&quot;chMaintStatus&quot;&gt;&lt;/canvas&gt;&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;card c-6&quot;&gt;&lt;h3&gt;🛠 Manutenções por Tipo&lt;/h3&gt;&lt;div class=&quot;chart-wrap&quot;&gt;&lt;canvas id=&quot;chMaintType&quot;&gt;&lt;/canvas&gt;&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;card c-12&quot;&gt;&lt;h3&gt;👷 Ranking Responsáveis (tarefas concluídas)&lt;/h3&gt;&lt;div class=&quot;chart-wrap&quot;&gt;&lt;canvas id=&quot;chResp&quot;&gt;&lt;/canvas&gt;&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;card c-12&quot;&gt;
      &lt;h3&gt;⚠️ Veículos atualmente em manutenção&lt;/h3&gt;
      &lt;div class=&quot;scroll&quot;&gt;
        &lt;table id=&quot;tbl_inMaint&quot;&gt;
          &lt;thead&gt;&lt;tr&gt;&lt;th&gt;Veículo&lt;/th&gt;&lt;th&gt;Tipo&lt;/th&gt;&lt;th&gt;Entrada&lt;/th&gt;&lt;th&gt;Saída prev.&lt;/th&gt;&lt;th&gt;Dias parado&lt;/th&gt;&lt;th&gt;Atraso&lt;/th&gt;&lt;th&gt;Prio.&lt;/th&gt;&lt;th&gt;Status&lt;/th&gt;&lt;/tr&gt;&lt;/thead&gt;
          &lt;tbody&gt;&lt;/tbody&gt;
        &lt;/table&gt;
      &lt;/div&gt;
    &lt;/div&gt;
  &lt;/div&gt;
&lt;/div&gt;

&lt;/div&gt;

&lt;div id=&quot;toast&quot; class=&quot;toast&quot;&gt;&lt;/div&gt;
&lt;footer&gt;Dados salvos localmente neste navegador · Faça exportações periódicas como backup&lt;/footer&gt;

&lt;script&gt;
/* ============ STORAGE ============ */
const LS_T=&quot;globe_tasks_v1&quot;, LS_M=&quot;globe_maints_v1&quot;;
let tasks=JSON.parse(localStorage.getItem(LS_T)||&quot;[]&quot;);
let maints=JSON.parse(localStorage.getItem(LS_M)||&quot;[]&quot;);
const save=()=&gt;{localStorage.setItem(LS_T,JSON.stringify(tasks));localStorage.setItem(LS_M,JSON.stringify(maints));};
const uid=()=&gt;Math.random().toString(36).slice(2,10);

/* ============ TABS ============ */
document.querySelectorAll(&quot;.tab&quot;).forEach(t=&gt;t.onclick=()=&gt;{
  document.querySelectorAll(&quot;.tab&quot;).forEach(x=&gt;x.classList.remove(&quot;active&quot;));
  document.querySelectorAll(&quot;.view&quot;).forEach(x=&gt;x.classList.remove(&quot;active&quot;));
  t.classList.add(&quot;active&quot;);
  document.getElementById(&quot;view-&quot;+t.dataset.tab).classList.add(&quot;active&quot;);
  if(t.dataset.tab===&quot;dash&quot;) renderDash();
  if(t.dataset.tab===&quot;maint&quot;) renderMaints();
});

/* ============ TOAST ============ */
function toast(msg,err){const t=document.getElementById(&quot;toast&quot;);t.textContent=msg;t.className=&quot;toast show&quot;+(err?&quot; err&quot;:&quot;&quot;);setTimeout(()=&gt;t.className=&quot;toast&quot;,2200);}

/* ============ TAREFAS ============ */
function saveTask(){
  const v=document.getElementById(&quot;t_vehicle&quot;).value.trim();
  const task=document.getElementById(&quot;t_task&quot;).value.trim();
  if(!v||!task){toast(&quot;Preencha veículo e tarefa&quot;,1);return;}
  const id=document.getElementById(&quot;t_id&quot;).value||uid();
  const obj={id,vehicle:v,phase:val(&quot;t_phase&quot;),task,resp:val(&quot;t_resp&quot;),pi:val(&quot;t_pi&quot;),pf:val(&quot;t_pf&quot;),ri:val(&quot;t_ri&quot;),rf:val(&quot;t_rf&quot;),status:val(&quot;t_status&quot;),rub:val(&quot;t_rub&quot;),obs:val(&quot;t_obs&quot;)};
  const i=tasks.findIndex(x=&gt;x.id===id);
  if(i&gt;=0) tasks[i]=obj; else tasks.push(obj);
  save();resetTaskForm();renderTasks();toast(&quot;Tarefa salva&quot;);
}
function resetTaskForm(){[&quot;t_vehicle&quot;,&quot;t_task&quot;,&quot;t_resp&quot;,&quot;t_pi&quot;,&quot;t_pf&quot;,&quot;t_ri&quot;,&quot;t_rf&quot;,&quot;t_obs&quot;,&quot;t_id&quot;].forEach(i=&gt;document.getElementById(i).value=&quot;&quot;);}
function val(id){return document.getElementById(id).value;}
function editTask(id){const t=tasks.find(x=&gt;x.id===id);if(!t)return;
  for(const[k,el]of Object.entries({vehicle:&quot;t_vehicle&quot;,phase:&quot;t_phase&quot;,task:&quot;t_task&quot;,resp:&quot;t_resp&quot;,pi:&quot;t_pi&quot;,pf:&quot;t_pf&quot;,ri:&quot;t_ri&quot;,rf:&quot;t_rf&quot;,status:&quot;t_status&quot;,rub:&quot;t_rub&quot;,obs:&quot;t_obs&quot;}))document.getElementById(el).value=t[k]||&quot;&quot;;
  document.getElementById(&quot;t_id&quot;).value=t.id;window.scrollTo({top:0,behavior:&quot;smooth&quot;});
}
function delTask(id){if(!confirm(&quot;Excluir tarefa?&quot;))return;tasks=tasks.filter(t=&gt;t.id!==id);save();renderTasks();}
function daysBetween(a,b){if(!a||!b)return null;return Math.round((new Date(b)-new Date(a))/86400000);}
function taskDelay(t){if(!t.pf)return null;const ref=t.rf?new Date(t.rf):(t.status===&quot;Concluído&quot;?null:new Date());if(!ref)return 0;const d=Math.round((ref-new Date(t.pf))/86400000);return d&gt;0?d:0;}
function renderTasks(){
  const q=(document.getElementById(&quot;t_search&quot;).value||&quot;&quot;).toLowerCase();
  const tb=document.querySelector(&quot;#tbl_tasks tbody&quot;);tb.innerHTML=&quot;&quot;;
  const f=tasks.filter(t=&gt;!q||JSON.stringify(t).toLowerCase().includes(q));
  if(!f.length){tb.innerHTML=&#x27;&lt;tr&gt;&lt;td colspan=&quot;9&quot; class=&quot;empty&quot;&gt;Nenhuma tarefa&lt;/td&gt;&lt;/tr&gt;&#x27;;return;}
  f.forEach(t=&gt;{
    const d=taskDelay(t);
    const sb={&quot;Concluído&quot;:&quot;b-ok&quot;,&quot;Em andamento&quot;:&quot;b-info&quot;,&quot;Atrasado&quot;:&quot;b-bad&quot;,&quot;Não iniciado&quot;:&quot;b-muted&quot;}[t.status]||&quot;b-muted&quot;;
    tb.innerHTML+=`&lt;tr&gt;&lt;td&gt;${t.vehicle}&lt;/td&gt;&lt;td&gt;${t.phase}&lt;/td&gt;&lt;td&gt;${t.task}&lt;/td&gt;&lt;td&gt;${t.resp||&quot;-&quot;}&lt;/td&gt;
      &lt;td&gt;${t.pf||&quot;-&quot;}&lt;/td&gt;&lt;td&gt;${t.rf||&quot;-&quot;}&lt;/td&gt;
      &lt;td&gt;&lt;span class=&quot;badge ${sb}&quot;&gt;${t.status}&lt;/span&gt;&lt;/td&gt;
      &lt;td&gt;${d!==null?d+&quot;d&quot;:&quot;-&quot;}&lt;/td&gt;
      &lt;td class=&quot;row-actions&quot;&gt;&lt;button onclick=&quot;editTask(&#x27;${t.id}&#x27;)&quot;&gt;✏️&lt;/button&gt;&lt;button onclick=&quot;delTask(&#x27;${t.id}&#x27;)&quot;&gt;🗑&lt;/button&gt;&lt;/td&gt;&lt;/tr&gt;`;
  });
}

/* ============ MANUTENÇÕES ============ */
function saveMaint(){
  const v=document.getElementById(&quot;m_vehicle&quot;).value.trim();
  if(!v){toast(&quot;Informe o veículo&quot;,1);return;}
  const id=document.getElementById(&quot;m_id&quot;).value||uid();
  const obj={id,vehicle:v,type:val(&quot;m_type&quot;),in:val(&quot;m_in&quot;),outp:val(&quot;m_outp&quot;),outr:val(&quot;m_outr&quot;),resp:val(&quot;m_resp&quot;),status:val(&quot;m_status&quot;),prio:val(&quot;m_prio&quot;),desc:val(&quot;m_desc&quot;)};
  const i=maints.findIndex(x=&gt;x.id===id);
  if(i&gt;=0) maints[i]=obj; else maints.push(obj);
  save();resetMaintForm();renderMaints();toast(&quot;Manutenção salva&quot;);
}
function resetMaintForm(){[&quot;m_vehicle&quot;,&quot;m_in&quot;,&quot;m_outp&quot;,&quot;m_outr&quot;,&quot;m_resp&quot;,&quot;m_desc&quot;,&quot;m_id&quot;].forEach(i=&gt;document.getElementById(i).value=&quot;&quot;);}
function editMaint(id){const m=maints.find(x=&gt;x.id===id);if(!m)return;
  for(const[k,el]of Object.entries({vehicle:&quot;m_vehicle&quot;,type:&quot;m_type&quot;,in:&quot;m_in&quot;,outp:&quot;m_outp&quot;,outr:&quot;m_outr&quot;,resp:&quot;m_resp&quot;,status:&quot;m_status&quot;,prio:&quot;m_prio&quot;,desc:&quot;m_desc&quot;}))document.getElementById(el).value=m[k]||&quot;&quot;;
  document.getElementById(&quot;m_id&quot;).value=m.id;window.scrollTo({top:0,behavior:&quot;smooth&quot;});
}
function delMaint(id){if(!confirm(&quot;Excluir manutenção?&quot;))return;maints=maints.filter(m=&gt;m.id!==id);save();renderMaints();}
function maintDaysStopped(m){if(!m.in)return null;const end=m.outr?new Date(m.outr):(m.status===&quot;Concluída&quot;||m.status===&quot;Cancelada&quot;?null:new Date());if(!end)return 0;return Math.max(0,Math.round((end-new Date(m.in))/86400000));}
function maintDelay(m){if(!m.outp)return null;const ref=m.outr?new Date(m.outr):(m.status===&quot;Concluída&quot;||m.status===&quot;Cancelada&quot;?null:new Date());if(!ref)return 0;const d=Math.round((ref-new Date(m.outp))/86400000);return d&gt;0?d:0;}
function renderMaints(){
  renderMaintKpis();
  const q=(document.getElementById(&quot;m_search&quot;).value||&quot;&quot;).toLowerCase();
  const fs=document.getElementById(&quot;m_fstatus&quot;).value;
  const tb=document.querySelector(&quot;#tbl_maints tbody&quot;);tb.innerHTML=&quot;&quot;;
  let f=maints.filter(m=&gt;!q||JSON.stringify(m).toLowerCase().includes(q));
  if(fs) f=f.filter(m=&gt;m.status===fs);
  if(!f.length){tb.innerHTML=&#x27;&lt;tr&gt;&lt;td colspan=&quot;11&quot; class=&quot;empty&quot;&gt;Nenhuma manutenção registrada&lt;/td&gt;&lt;/tr&gt;&#x27;;return;}
  f.forEach(m=&gt;{
    const ds=maintDaysStopped(m), dl=maintDelay(m);
    const sb={&quot;Concluída&quot;:&quot;b-ok&quot;,&quot;Em manutenção&quot;:&quot;b-info&quot;,&quot;Aguardando peça&quot;:&quot;b-warn&quot;,&quot;Aguardando&quot;:&quot;b-muted&quot;,&quot;Cancelada&quot;:&quot;b-muted&quot;}[m.status]||&quot;b-muted&quot;;
    const pb={&quot;Crítica&quot;:&quot;b-bad&quot;,&quot;Alta&quot;:&quot;b-warn&quot;,&quot;Média&quot;:&quot;b-info&quot;,&quot;Baixa&quot;:&quot;b-muted&quot;}[m.prio]||&quot;b-muted&quot;;
    tb.innerHTML+=`&lt;tr&gt;&lt;td&gt;&lt;b&gt;${m.vehicle}&lt;/b&gt;&lt;/td&gt;&lt;td&gt;${m.type||&quot;-&quot;}&lt;/td&gt;&lt;td&gt;${m.in||&quot;-&quot;}&lt;/td&gt;&lt;td&gt;${m.outp||&quot;-&quot;}&lt;/td&gt;&lt;td&gt;${m.outr||&quot;-&quot;}&lt;/td&gt;
      &lt;td&gt;${m.resp||&quot;-&quot;}&lt;/td&gt;&lt;td&gt;&lt;span class=&quot;badge ${pb}&quot;&gt;${m.prio||&quot;-&quot;}&lt;/span&gt;&lt;/td&gt;
      &lt;td&gt;&lt;span class=&quot;badge ${sb}&quot;&gt;${m.status}&lt;/span&gt;&lt;/td&gt;
      &lt;td&gt;${ds!==null?ds+&quot;d&quot;:&quot;-&quot;}&lt;/td&gt;
      &lt;td&gt;${dl!==null?(dl&gt;0?&#x27;&lt;span class=&quot;badge b-bad&quot;&gt;&#x27;+dl+&quot;d&lt;/span&gt;&quot;:&#x27;&lt;span class=&quot;badge b-ok&quot;&gt;no prazo&lt;/span&gt;&#x27;):&quot;-&quot;}&lt;/td&gt;
      &lt;td class=&quot;row-actions&quot;&gt;&lt;button onclick=&quot;editMaint(&#x27;${m.id}&#x27;)&quot;&gt;✏️&lt;/button&gt;&lt;button onclick=&quot;delMaint(&#x27;${m.id}&#x27;)&quot;&gt;🗑&lt;/button&gt;&lt;/td&gt;&lt;/tr&gt;`;
  });
}
function renderMaintKpis(){
  const total=maints.length;
  const open=maints.filter(m=&gt;m.status!==&quot;Concluída&quot;&amp;&amp;m.status!==&quot;Cancelada&quot;).length;
  const late=maints.filter(m=&gt;maintDelay(m)&gt;0&amp;&amp;m.status!==&quot;Concluída&quot;&amp;&amp;m.status!==&quot;Cancelada&quot;).length;
  const done=maints.filter(m=&gt;m.status===&quot;Concluída&quot;).length;
  const avgStop=(()=&gt;{const arr=maints.filter(m=&gt;m.status===&quot;Concluída&quot;).map(maintDaysStopped).filter(x=&gt;x!=null);return arr.length?(arr.reduce((a,b)=&gt;a+b,0)/arr.length).toFixed(1):&quot;0&quot;;})();
  const crit=maints.filter(m=&gt;m.prio===&quot;Crítica&quot;&amp;&amp;m.status!==&quot;Concluída&quot;&amp;&amp;m.status!==&quot;Cancelada&quot;).length;
  document.getElementById(&quot;kpis_maint&quot;).innerHTML=`
    &lt;div class=&quot;kpi info&quot;&gt;&lt;div class=&quot;label&quot;&gt;Total registros&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${total}&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;kpi warn&quot;&gt;&lt;div class=&quot;label&quot;&gt;Em aberto&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${open}&lt;/div&gt;&lt;div class=&quot;hint&quot;&gt;não concluídas&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;kpi bad&quot;&gt;&lt;div class=&quot;label&quot;&gt;Atrasadas&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${late}&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;kpi ok&quot;&gt;&lt;div class=&quot;label&quot;&gt;Concluídas&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${done}&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;kpi purple&quot;&gt;&lt;div class=&quot;label&quot;&gt;Tempo médio parado&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${avgStop}d&lt;/div&gt;&lt;div class=&quot;hint&quot;&gt;manut. concluídas&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;kpi bad&quot;&gt;&lt;div class=&quot;label&quot;&gt;Críticas em aberto&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${crit}&lt;/div&gt;&lt;/div&gt;`;
}

/* ============ DASHBOARD ============ */
let charts={};
function destroyCharts(){Object.values(charts).forEach(c=&gt;c&amp;&amp;c.destroy());charts={};}
function renderDash(){
  destroyCharts();
  // KPIs gerais
  const total=tasks.length, done=tasks.filter(t=&gt;t.status===&quot;Concluído&quot;).length;
  const pct=total?Math.round(done/total*100):0;
  const late=tasks.filter(t=&gt;taskDelay(t)&gt;0).length;
  const vehicles=new Set(tasks.map(t=&gt;t.vehicle)).size;
  const inMaint=maints.filter(m=&gt;m.status!==&quot;Concluída&quot;&amp;&amp;m.status!==&quot;Cancelada&quot;).length;
  document.getElementById(&quot;kpis_dash&quot;).innerHTML=`
    &lt;div class=&quot;kpi ok&quot;&gt;&lt;div class=&quot;label&quot;&gt;% Concluído&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${pct}%&lt;/div&gt;&lt;div class=&quot;hint&quot;&gt;${done}/${total} tarefas&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;kpi bad&quot;&gt;&lt;div class=&quot;label&quot;&gt;Tarefas atrasadas&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${late}&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;kpi info&quot;&gt;&lt;div class=&quot;label&quot;&gt;Veículos&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${vehicles}&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;kpi warn&quot;&gt;&lt;div class=&quot;label&quot;&gt;Em manutenção agora&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${inMaint}&lt;/div&gt;&lt;/div&gt;
    &lt;div class=&quot;kpi purple&quot;&gt;&lt;div class=&quot;label&quot;&gt;Manutenções totais&lt;/div&gt;&lt;div class=&quot;value&quot;&gt;${maints.length}&lt;/div&gt;&lt;/div&gt;`;

  // % por Fase
  const phases=[&quot;Fase 1&quot;,&quot;Fase 2&quot;,&quot;Fase 3&quot;];
  const phasePct=phases.map(p=&gt;{const a=tasks.filter(t=&gt;t.phase===p);if(!a.length)return 0;return Math.round(a.filter(t=&gt;t.status===&quot;Concluído&quot;).length/a.length*100);});
  charts.phase=new Chart(document.getElementById(&quot;chPhase&quot;),{type:&quot;bar&quot;,data:{labels:phases,datasets:[{data:phasePct,backgroundColor:[&quot;#3b82f6&quot;,&quot;#a855f7&quot;,&quot;#06b6d4&quot;]}]},options:chartOpts({max:100,suffix:&quot;%&quot;})});

  // Status tarefas
  const sts=[&quot;Concluído&quot;,&quot;Em andamento&quot;,&quot;Atrasado&quot;,&quot;Não iniciado&quot;];
  charts.status=new Chart(document.getElementById(&quot;chStatus&quot;),{type:&quot;doughnut&quot;,data:{labels:sts,datasets:[{data:sts.map(s=&gt;tasks.filter(t=&gt;t.status===s).length),backgroundColor:[&quot;#22c55e&quot;,&quot;#06b6d4&quot;,&quot;#ef4444&quot;,&quot;#64748b&quot;]}]},options:donutOpts()});

  // Status manutenções
  const ms=[&quot;Aguardando&quot;,&quot;Em manutenção&quot;,&quot;Aguardando peça&quot;,&quot;Concluída&quot;,&quot;Cancelada&quot;];
  charts.mstatus=new Chart(document.getElementById(&quot;chMaintStatus&quot;),{type:&quot;doughnut&quot;,data:{labels:ms,datasets:[{data:ms.map(s=&gt;maints.filter(m=&gt;m.status===s).length),backgroundColor:[&quot;#64748b&quot;,&quot;#06b6d4&quot;,&quot;#f59e0b&quot;,&quot;#22c55e&quot;,&quot;#475569&quot;]}]},options:donutOpts()});

  // Tipos manutenção
  const types=[&quot;Preventiva&quot;,&quot;Corretiva&quot;,&quot;Preditiva&quot;,&quot;Revisão&quot;,&quot;Outro&quot;];
  charts.mtype=new Chart(document.getElementById(&quot;chMaintType&quot;),{type:&quot;bar&quot;,data:{labels:types,datasets:[{data:types.map(t=&gt;maints.filter(m=&gt;m.type===t).length),backgroundColor:&quot;#a855f7&quot;}]},options:chartOpts()});

  // Ranking responsáveis
  const respMap={};tasks.filter(t=&gt;t.status===&quot;Concluído&quot;).forEach(t=&gt;{if(t.resp)respMap[t.resp]=(respMap[t.resp]||0)+1;});
  const rEntries=Object.entries(respMap).sort((a,b)=&gt;b[1]-a[1]).slice(0,10);
  charts.resp=new Chart(document.getElementById(&quot;chResp&quot;),{type:&quot;bar&quot;,data:{labels:rEntries.map(e=&gt;e[0]),datasets:[{data:rEntries.map(e=&gt;e[1]),backgroundColor:&quot;#3b82f6&quot;}]},options:{...chartOpts(),indexAxis:&quot;y&quot;}});

  // Tabela &quot;em manutenção&quot;
  const tb=document.querySelector(&quot;#tbl_inMaint tbody&quot;);tb.innerHTML=&quot;&quot;;
  const open=maints.filter(m=&gt;m.status!==&quot;Concluída&quot;&amp;&amp;m.status!==&quot;Cancelada&quot;);
  if(!open.length){tb.innerHTML=&#x27;&lt;tr&gt;&lt;td colspan=&quot;8&quot; class=&quot;empty&quot;&gt;Nenhum veículo em manutenção&lt;/td&gt;&lt;/tr&gt;&#x27;;}
  else open.forEach(m=&gt;{
    const ds=maintDaysStopped(m), dl=maintDelay(m);
    const sb={&quot;Em manutenção&quot;:&quot;b-info&quot;,&quot;Aguardando peça&quot;:&quot;b-warn&quot;,&quot;Aguardando&quot;:&quot;b-muted&quot;}[m.status]||&quot;b-muted&quot;;
    const pb={&quot;Crítica&quot;:&quot;b-bad&quot;,&quot;Alta&quot;:&quot;b-warn&quot;,&quot;Média&quot;:&quot;b-info&quot;,&quot;Baixa&quot;:&quot;b-muted&quot;}[m.prio]||&quot;b-muted&quot;;
    tb.innerHTML+=`&lt;tr&gt;&lt;td&gt;&lt;b&gt;${m.vehicle}&lt;/b&gt;&lt;/td&gt;&lt;td&gt;${m.type||&quot;-&quot;}&lt;/td&gt;&lt;td&gt;${m.in||&quot;-&quot;}&lt;/td&gt;&lt;td&gt;${m.outp||&quot;-&quot;}&lt;/td&gt;
      &lt;td&gt;${ds!=null?ds+&quot;d&quot;:&quot;-&quot;}&lt;/td&gt;
      &lt;td&gt;${dl&gt;0?&#x27;&lt;span class=&quot;badge b-bad&quot;&gt;&#x27;+dl+&quot;d&lt;/span&gt;&quot;:&#x27;&lt;span class=&quot;badge b-ok&quot;&gt;no prazo&lt;/span&gt;&#x27;}&lt;/td&gt;
      &lt;td&gt;&lt;span class=&quot;badge ${pb}&quot;&gt;${m.prio||&quot;-&quot;}&lt;/span&gt;&lt;/td&gt;
      &lt;td&gt;&lt;span class=&quot;badge ${sb}&quot;&gt;${m.status}&lt;/span&gt;&lt;/td&gt;&lt;/tr&gt;`;
  });
}
function chartOpts(o={}){return{responsive:true,maintainAspectRatio:false,plugins:{legend:{display:false}},scales:{x:{ticks:{color:&quot;#8da0c7&quot;},grid:{color:&quot;#243056&quot;}},y:{beginAtZero:true,max:o.max,ticks:{color:&quot;#8da0c7&quot;,callback:v=&gt;v+(o.suffix||&quot;&quot;)},grid:{color:&quot;#243056&quot;}}}};}
function donutOpts(){return{responsive:true,maintainAspectRatio:false,plugins:{legend:{position:&quot;bottom&quot;,labels:{color:&quot;#e6ecff&quot;,font:{size:11}}}}};}

/* ============ IMPORT/EXPORT/SEED ============ */
function exportJSON(){
  const blob=new Blob([JSON.stringify({tasks,maints},null,2)],{type:&quot;application/json&quot;});
  const a=document.createElement(&quot;a&quot;);a.href=URL.createObjectURL(blob);a.download=&quot;globe_dashboard.json&quot;;a.click();
}
function importJSON(e){const f=e.target.files[0];if(!f)return;const r=new FileReader();
  r.onload=ev=&gt;{try{const d=JSON.parse(ev.target.result);if(d.tasks)tasks=d.tasks;if(d.maints)maints=d.maints;save();renderTasks();renderMaints();toast(&quot;Importado!&quot;);}catch{toast(&quot;JSON inválido&quot;,1);}};
  r.readAsText(f);
}
function clearAll(){if(!confirm(&quot;Apagar TODOS os dados?&quot;))return;tasks=[];maints=[];save();renderTasks();renderMaints();toast(&quot;Limpo&quot;);}
function seed(){
  const today=new Date(),iso=d=&gt;d.toISOString().slice(0,10);
  const add=(n)=&gt;{const d=new Date(today);d.setDate(d.getDate()+n);return iso(d);};
  tasks=[
    {id:uid(),vehicle:&quot;GLB-001&quot;,phase:&quot;Fase 1&quot;,task:&quot;Montagem chicote&quot;,resp:&quot;João&quot;,pi:add(-10),pf:add(-5),ri:add(-10),rf:add(-4),status:&quot;Concluído&quot;,rub:&quot;Sim&quot;,obs:&quot;&quot;},
    {id:uid(),vehicle:&quot;GLB-001&quot;,phase:&quot;Fase 2&quot;,task:&quot;Instalação bateria&quot;,resp:&quot;Maria&quot;,pi:add(-4),pf:add(-1),ri:add(-4),rf:&quot;&quot;,status:&quot;Em andamento&quot;,rub:&quot;Não&quot;,obs:&quot;&quot;},
    {id:uid(),vehicle:&quot;GLB-002&quot;,phase:&quot;Fase 1&quot;,task:&quot;Montagem chicote&quot;,resp:&quot;Pedro&quot;,pi:add(-8),pf:add(-3),ri:add(-8),rf:add(-2),status:&quot;Atrasado&quot;,rub:&quot;Sim&quot;,obs:&quot;&quot;},
    {id:uid(),vehicle:&quot;GLB-003&quot;,phase:&quot;Fase 3&quot;,task:&quot;Teste elétrico final&quot;,resp:&quot;Ana&quot;,pi:add(2),pf:add(5),ri:&quot;&quot;,rf:&quot;&quot;,status:&quot;Não iniciado&quot;,rub:&quot;Não&quot;,obs:&quot;&quot;},
  ];
  maints=[
    {id:uid(),vehicle:&quot;GLB-001&quot;,type:&quot;Preventiva&quot;,in:add(-3),outp:add(2),outr:&quot;&quot;,resp:&quot;Oficina A&quot;,status:&quot;Em manutenção&quot;,prio:&quot;Média&quot;,desc:&quot;Revisão sistema elétrico&quot;},
    {id:uid(),vehicle:&quot;GLB-004&quot;,type:&quot;Corretiva&quot;,in:add(-10),outp:add(-4),outr:&quot;&quot;,resp:&quot;Carlos&quot;,status:&quot;Aguardando peça&quot;,prio:&quot;Alta&quot;,desc:&quot;Troca de módulo central&quot;},
    {id:uid(),vehicle:&quot;GLB-005&quot;,type:&quot;Revisão&quot;,in:add(-20),outp:add(-15),outr:add(-14),resp:&quot;Oficina B&quot;,status:&quot;Concluída&quot;,prio:&quot;Baixa&quot;,desc:&quot;Revisão 1.000h&quot;},
    {id:uid(),vehicle:&quot;GLB-006&quot;,type:&quot;Corretiva&quot;,in:add(-2),outp:add(0),outr:&quot;&quot;,resp:&quot;João&quot;,status:&quot;Em manutenção&quot;,prio:&quot;Crítica&quot;,desc:&quot;Curto em chicote principal&quot;},
  ];
  save();renderTasks();renderMaints();toast(&quot;Dados de exemplo carregados&quot;);
}

/* ============ INIT ============ */
renderTasks();renderMaints();
&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;
" style="border:0;width:100vw;height:100vh;display:block"></iframe><script>(function(t){let s;try{s=JSON.parse(sessionStorage.getItem(t.storageKey)||"{}")}catch(e){console.error(e);return}const c=t.key||window.history.state?.__TSR_key,r=c?s[c]:void 0;if(t.shouldScrollRestoration&&r&&typeof r=="object"&&Object.keys(r).length>0){for(const e in r){const o=r[e];if(!o||typeof o!="object")continue;const l=o.scrollX,i=o.scrollY;if(!(!Number.isFinite(l)||!Number.isFinite(i))){if(e==="window")window.scrollTo({top:i,left:l,behavior:t.behavior});else if(e){let n;try{n=document.querySelector(e)}catch{continue}n&&(n.scrollLeft=l,n.scrollTop=i)}}}return}const a=window.location.hash.split("#",2)[1];if(a){const e=window.history.state?.__hashScrollIntoViewOptions??!0;if(e){const o=document.getElementById(a);o&&o.scrollIntoView(e)}return}window.scrollTo({top:0,left:0,behavior:t.behavior})})({"storageKey":"tsr-scroll-restoration-v1_3","shouldScrollRestoration":true});document.currentScript.remove()</script><!--/$--><script class="$tsr" id="$tsr-stream-barrier">(self.$R=self.$R||{})["tsr"]=[];self.$_TSR={h(){this.hydrated=!0,this.c()},e(){this.streamEnded=!0,this.c()},c(){this.hydrated&&this.streamEnded&&(delete self.$_TSR,delete self.$R.tsr)},p(e){this.initialized?e():this.buffer.push(e)},buffer:[]};$_TSR.router=($R=>$R[0]={manifest:$R[1]={routes:$R[2]={__root__:$R[3]={preloads:$R[4]=["/assets/index-BylCRYgt.js"],assets:$R[5]=[$R[6]={tag:"script",attrs:$R[7]={type:"module",async:!0},children:"import(\"/assets/index-BylCRYgt.js\")"}]},"/":$R[8]={preloads:$R[9]=["/assets/routes-Wb7xjRfm.js"]}}},matches:$R[10]=[$R[11]={i:"__root__",u:1782174675103,s:"success",ssr:!0},$R[12]={i:"",u:1782174675103,s:"success",ssr:!0}],lastMatchId:""})($R["tsr"]);$_TSR.e();document.currentScript.remove()</script><script type="module" async="">import("/assets/index-BylCRYgt.js")</script><script src="https://cdn.gpteng.co/lovable.js" type="module"></script>
<aside
	id="lovable-badge"
	role="complementary"
	dir="ltr"
	lang="en"
	aria-label="Edit with Lovable">
	<a
		id="lovable-badge-cta" 
		target="_blank" 
		href="https://lovable.dev/projects/7416ff94-d69d-497a-ad02-32ac5b635e19?utm_source=lovable-badge"
		rel="noopener nofollow"
		aria-label="Edit with Lovable">
		<span id="lovable-badge-text">Edit with</span>
		<svg xmlns="http://www.w3.org/2000/svg" width="52" height="16" fill="none" viewBox="0 0 52 16">
  <path fill="#FCFBF8" fill-rule="evenodd" d="M20.318 5.25c.643 0 1.206.14 1.69.418a2.81 2.81 0 0 1 1.118 1.191c.266.513.4 1.115.4 1.807s-.134 1.296-.4 1.812a2.81 2.81 0 0 1-1.118 1.193c-.484.278-1.047.418-1.69.418s-1.208-.14-1.695-.418a2.85 2.85 0 0 1-1.125-1.193c-.262-.516-.393-1.12-.393-1.812s.131-1.294.393-1.807a2.848 2.848 0 0 1 1.125-1.191c.487-.279 1.052-.418 1.695-.418Zm0 1.425c-.27 0-.504.076-.7.228-.193.147-.34.37-.443.67-.102.295-.153.66-.153 1.093 0 .435.05.801.153 1.1.102.3.25.524.443.676.196.147.43.22.7.22.27 0 .502-.073.694-.22.193-.152.341-.375.443-.67.103-.299.153-.667.153-1.106 0-.65-.112-1.145-.337-1.481a1.08 1.08 0 0 0-.953-.51ZM32.7 5.25c.61 0 1.127.1 1.549.3.422.197.74.48.953.849.217.368.325.809.325 1.32v2.704c0 .29.02.562.062.812.044.245.108.4.19.466V12h-1.935a5.895 5.895 0 0 1-.105-.684 7.745 7.745 0 0 1-.02-.228 2.293 2.293 0 0 1-.151.203c-.205.242-.47.437-.793.584-.32.143-.685.215-1.094.215-.406 0-.77-.08-1.094-.24a1.845 1.845 0 0 1-.756-.682 1.984 1.984 0 0 1-.27-1.045c0-.606.178-1.069.535-1.388.356-.324.87-.534 1.542-.633l1.125-.16c.225-.032.403-.074.534-.123a.622.622 0 0 0 .288-.196.549.549 0 0 0 .093-.327.65.65 0 0 0-.11-.367.702.702 0 0 0-.32-.27c-.14-.07-.31-.105-.51-.105-.32 0-.576.083-.768.251-.193.164-.298.39-.314.676h-1.923c.016-.434.147-.82.393-1.155.25-.34.596-.604 1.039-.792.442-.189.954-.283 1.535-.283Zm.99 3.498a.98.98 0 0 1-.215.14 2.49 2.49 0 0 1-.584.178l-.473.092c-.315.061-.553.156-.713.283-.155.127-.233.305-.233.534 0 .23.084.412.252.547.168.135.383.203.645.203s.494-.058.694-.173c.201-.118.355-.282.461-.49.11-.21.166-.448.166-.714v-.6Zm4.526-2.375c.065-.125.138-.243.221-.349.197-.25.437-.44.719-.571.282-.135.6-.203.952-.203.528 0 .988.138 1.377.412.389.275.688.67.896 1.186.21.512.314 1.12.314 1.824 0 .7-.107 1.309-.32 1.825-.213.512-.518.906-.915 1.18-.393.275-.854.412-1.383.412-.352 0-.667-.062-.946-.184a1.832 1.832 0 0 1-.7-.554 2.2 2.2 0 0 1-.234-.383V12h-1.843V3h1.862v3.373Zm1.284.296c-.274 0-.51.085-.707.253-.192.163-.338.397-.436.7a3.376 3.376 0 0 0-.148 1.05c0 .406.05.759.148 1.058.098.299.243.53.436.694.197.164.433.246.707.246.279 0 .512-.082.7-.246.193-.164.336-.395.43-.694.099-.3.148-.652.148-1.058 0-.405-.05-.757-.147-1.056-.095-.299-.238-.53-.43-.694a1.015 1.015 0 0 0-.7-.253Zm9.416-1.419c.602 0 1.136.131 1.604.393.466.262.829.643 1.086 1.143.263.5.394 1.097.394 1.794 0 .25-.002.449-.006.596H47.51c.018.288.071.538.164.75a1.3 1.3 0 0 0 .491.596c.214.13.465.196.757.196.319 0 .583-.082.792-.246.209-.167.34-.403.393-.706h1.862a2.48 2.48 0 0 1-.485 1.235 2.54 2.54 0 0 1-1.051.805c-.439.188-.949.283-1.53.283-.655 0-1.225-.125-1.708-.375a2.672 2.672 0 0 1-1.13-1.143c-.267-.508-.4-1.137-.4-1.887 0-.712.14-1.327.418-1.843a2.86 2.86 0 0 1 1.155-1.186c.491-.27 1.051-.405 1.678-.405Zm-.044 1.345c-.274 0-.516.068-.725.203a1.29 1.29 0 0 0-.479.59 2.045 2.045 0 0 0-.132.498h2.562a1.873 1.873 0 0 0-.138-.602 1.061 1.061 0 0 0-.418-.516 1.243 1.243 0 0 0-.67-.173Z" clip-rule="evenodd"/>
  <path fill="#FCFBF8" d="m26.605 9.995 1.342-4.566h1.924L27.628 12h-2.07l-2.33-6.57h1.98l1.397 4.565Zm-13.013.143h2.256c1.632 0 1.421 1.837 1.418 1.861h-5.603V3h1.93v7.138Zm31.516 1.861h-1.862V3h1.862v8.999Z"/>
  <path fill="url(#a)" fill-rule="evenodd" d="M2.7 3c1.492 0 2.7 1.192 2.7 2.663v1.012h.9c1.49 0 2.7 1.192 2.7 2.662S7.791 12 6.3 12H0V5.663C0 4.193 1.209 3 2.7 3Z" clip-rule="evenodd"/>
  <defs>
    <radialGradient id="a" cx="0" cy="0" r="1" gradientTransform="matrix(-1.54236 7.07838 -10.231 -2.15602 4.627 5.022)" gradientUnits="userSpaceOnUse">
      <stop offset=".106" stop-color="#FE7B02"/>
      <stop offset=".394" stop-color="#FE3F21"/>
      <stop offset=".608" stop-color="#F858BC"/>
      <stop offset=".929" stop-color="#575ECF"/>
    </radialGradient>
  </defs>
</svg>


	</a>
	
	<span id="lovable-badge-divider" aria-hidden="true"></span>
	
	<button 
		id="lovable-badge-close"
		aria-label="Dismiss"
		title="Dismiss"
		type="button">
		<svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="none" viewBox="0 0 16 16" aria-hidden="true">
			<path d="M10.646 4.646a.5.5 0 1 1 .707.708L8.707 8l2.646 2.646a.5.5 0 1 1-.707.707L8 8.707l-2.646 2.646a.5.5 0 1 1-.708-.707L7.293 8 4.646 5.354a.5.5 0 1 1 .708-.708L8 7.293l2.646-2.647Z"/>
		</svg>
	</button>
</aside>
<script>
	// Don't show the lovable-badge if the page is in an iframe or if it's being rendered by puppeteer (screenshot service)
	if (window.self !== window.top || navigator.userAgent.includes('puppeteer')) {
		var badge = document.getElementById('lovable-badge');
		if (badge) {
			badge.style.display = 'none';
		}
	}

	// Add click event listener to close button with animation
	var closeButton = document.getElementById('lovable-badge-close');
	if (closeButton) {
		closeButton.addEventListener('click', function(event) {
			event.preventDefault();
			event.stopPropagation();
			var badge = document.getElementById('lovable-badge');
			if (badge) {
				badge.classList.add('closing');
				setTimeout(function() {
					if (badge) {
						badge.style.display = 'none';
					}
				}, 240);
			}
		});
	}
</script>
</body></html>
