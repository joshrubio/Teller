---
type: bundle
task: dashboard
updated: 2026-06-18
---

# Bundle: Dashboard

Session-start widget. Agent reads all project state.md files, fills the slots below, then calls show_widget with the HTML template.

## Data slots to fill before rendering

| Slot | Source |
|---|---|
| `[PROJECT_NAME]` | state.md → project title |
| `[LIBRO_TAG]` | state.md → active-libro + cap count |
| `[STATUS_CLASS]` | Derive from state.md — see rules below |
| `[STATUS_LABEL]` | Derive from state.md — see rules below |
| `[NOTICE_HTML]` | Only if next-book-initialized: false — see below |
| `[ACTIVE_TITLE]` | state.md → project title + "— activo" |
| `[ACTIVE_STATUS]` | state.md → 1 sentence: libro + caps + phase |
| `[ACTIVE_NEXT]` | state.md → open threads, 1 sentence |
| `[NEXT_CAP]` | state.md → next chapter number |

## Status class rules

| Condition | STATUS_CLASS | STATUS_LABEL |
|---|---|---|
| In progress, chapters written | `s-progress` | `En progreso` |
| Complete, next-book-initialized: true | `s-complete` | `Completo` |
| Complete, next-book-initialized: false | `s-complete` | `Completo` |
| Concept phase, 0 chapters | `s-concept` | `Concepto` |

## Notice block

Only render if `next-book-initialized: false`. Replace `[NOTICE_HTML]` with:

```html
<div class="notice">
  <i class="ti ti-alert-circle" aria-hidden="true" style="font-size:14px;flex-shrink:0"></i>
  <span><strong>[PROJECT_NAME]</strong> — Libro [N] no iniciado · <span class="lnk" onclick="sendPrompt('/new-book [N+1]')">continuar en el mismo universo</span> o <span class="lnk" onclick="sendPrompt('/new-project nueva-obra')">nueva obra</span></span>
</div>
```

If `next-book-initialized: true` or libro is in progress → `[NOTICE_HTML]` = empty string.

## Multiple projects

For each project folder found in `projects/`, add one `.project-row` div. Active project gets class `active`. Rows are sorted: active first, then alphabetical.

---

## HTML template

```html
<style>
*{box-sizing:border-box;margin:0;padding:0}
.root{padding:1.5rem 0 1rem;font-family:var(--font-sans)}
.header{display:flex;align-items:baseline;gap:10px;margin-bottom:1.5rem}
.logo{font-size:16px;font-weight:500;color:var(--color-text-primary);letter-spacing:-0.3px}
.path{font-size:11px;color:var(--color-text-tertiary);font-family:var(--font-mono)}
.section-label{font-size:11px;font-weight:500;color:var(--color-text-tertiary);letter-spacing:.06em;text-transform:uppercase;margin-bottom:.6rem}
.projects{display:flex;flex-direction:column;gap:6px;margin-bottom:1.25rem}
.project-row{display:flex;align-items:center;padding:.75rem 1rem;background:var(--color-background-primary);border:0.5px solid var(--color-border-tertiary);border-radius:var(--border-radius-lg);gap:12px}
.project-row.active{border-color:#1D9E75;border-width:1px}
.project-row.new{border-style:dashed;cursor:pointer}
.project-row.new:hover{border-color:var(--color-border-secondary)}
.project-dot{width:6px;height:6px;border-radius:50%;background:var(--color-border-secondary);flex-shrink:0}
.project-dot.active{background:#1D9E75}
.project-name{font-size:13px;font-weight:500;color:var(--color-text-primary);flex:1}
.libro-tag{font-size:11px;color:var(--color-text-tertiary);white-space:nowrap}
.status-pill{font-size:11px;font-weight:500;padding:3px 9px;border-radius:20px;white-space:nowrap;flex-shrink:0}
.s-complete{background:#E1F5EE;color:#085041}
.s-progress{background:#FAEEDA;color:#633806}
.s-concept{background:var(--color-background-secondary);color:var(--color-text-secondary)}
.notice{font-size:11px;color:#854F0B;background:#FAEEDA;border-radius:var(--border-radius-md);padding:6px 10px;margin-bottom:1.5rem;display:flex;align-items:center;gap:6px}
.notice strong{font-weight:500;color:#633806}
.notice .lnk{cursor:pointer;text-decoration:underline;color:#854F0B}
.active-block{background:var(--color-background-secondary);border-radius:var(--border-radius-lg);padding:1rem 1.25rem;margin-bottom:1.5rem}
.active-title{font-size:13px;font-weight:500;color:var(--color-text-primary);margin-bottom:4px}
.active-status{font-size:12px;color:var(--color-text-secondary);margin-bottom:2px}
.active-next{font-size:12px;color:var(--color-text-tertiary)}
.ctas{display:grid;grid-template-columns:1fr 1fr;gap:8px;margin-bottom:1.5rem}
.btn{font-size:13px;padding:10px 16px;border-radius:var(--border-radius-lg);border:0.5px solid var(--color-border-secondary);background:var(--color-background-primary);color:var(--color-text-primary);cursor:pointer;font-family:var(--font-sans);transition:background .12s;text-align:left;display:flex;flex-direction:column;gap:3px}
.btn:hover{background:var(--color-background-secondary)}
.btn.primary{border-color:#1D9E75}
.btn.primary:hover{background:#E1F5EE}
.btn-label{font-weight:500;font-size:13px}
.btn-sub{font-size:11px;color:var(--color-text-tertiary);font-weight:400}
.btn.primary .btn-sub{color:#1D9E75}
.divider{border:none;border-top:0.5px solid var(--color-border-tertiary);margin:1.25rem 0}
.ref{display:grid;grid-template-columns:1fr 1fr;gap:4px 24px}
.ref-row{display:flex;align-items:baseline;gap:8px;padding:3px 0}
.ref-cmd{font-size:11px;font-family:var(--font-mono);color:var(--color-text-secondary);white-space:nowrap;flex-shrink:0}
.ref-desc{font-size:11px;color:var(--color-text-tertiary)}
</style>

<div class="root">
  <h2 class="sr-only">Teller dashboard — active projects and session commands</h2>
  <div class="header">
    <span class="logo">Teller</span>
    <span class="path">D:\Writting\Teller\</span>
  </div>
  <p class="section-label">Proyectos</p>
  <div class="projects">
    <!-- one .project-row per project, active first -->
    <div class="project-row active">
      <span class="project-dot active"></span>
      <span class="project-name">[PROJECT_NAME]</span>
      <span class="libro-tag">[LIBRO_TAG]</span>
      <span class="status-pill [STATUS_CLASS]">[STATUS_LABEL]</span>
    </div>
    <div class="project-row new" onclick="sendPrompt('/new-project nueva-obra')">
      <span class="project-dot"></span>
      <span class="project-name" style="color:var(--color-text-tertiary);font-weight:400">Nueva obra</span>
      <span class="status-pill s-concept">/new-project ↗</span>
    </div>
  </div>
  [NOTICE_HTML]
  <div class="active-block">
    <p class="active-title">[ACTIVE_TITLE]</p>
    <p class="active-status">[ACTIVE_STATUS]</p>
    <p class="active-next">[ACTIVE_NEXT]</p>
  </div>
  <div class="ctas">
    <button class="btn primary" onclick="sendPrompt('continúa con lo que sigue en [PROJECT_NAME]')">
      <span class="btn-label">Continuar ↗</span>
      <span class="btn-sub">El agente retoma desde donde lo dejamos</span>
    </button>
    <button class="btn" onclick="sendPrompt('quiero editar algo en [PROJECT_NAME]')">
      <span class="btn-label">Editar ↗</span>
      <span class="btn-sub">Revisar o reescribir capítulos existentes</span>
    </button>
    <button class="btn" onclick="sendPrompt('/new-book 2')">
      <span class="btn-label">Iniciar Libro 2 ↗</span>
      <span class="btn-sub">Mismo universo, nueva voz y temas</span>
    </button>
    <button class="btn" onclick="sendPrompt('/new-project nueva-obra')">
      <span class="btn-label">Nueva obra ↗</span>
      <span class="btn-sub">Proyecto independiente</span>
    </button>
  </div>
  <hr class="divider">
  <p class="section-label">Referencia de comandos</p>
  <div class="ref">
    <div class="ref-row"><span class="ref-cmd">escribe el cap X</span><span class="ref-desc">Redactar capítulo</span></div>
    <div class="ref-row"><span class="ref-cmd">planifiquemos el cap X</span><span class="ref-desc">Planificar capítulo</span></div>
    <div class="ref-row"><span class="ref-cmd">edita el cap X</span><span class="ref-desc">Editar capítulo existente</span></div>
    <div class="ref-row"><span class="ref-cmd">verifica continuidad del cap X</span><span class="ref-desc">Revisar continuidad</span></div>
    <div class="ref-row"><span class="ref-cmd">/session-close X</span><span class="ref-desc">Cerrar sesión tras cap</span></div>
    <div class="ref-row"><span class="ref-cmd">/new-book N</span><span class="ref-desc">Nuevo libro, mismo universo</span></div>
    <div class="ref-row"><span class="ref-cmd">/new-project [nombre]</span><span class="ref-desc">Nueva obra independiente</span></div>
  </div>
</div>
```
