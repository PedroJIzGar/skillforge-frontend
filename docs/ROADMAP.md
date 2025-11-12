# Roadmap — SkillForge

**Stack:** Angular 17 (standalone) • PrimeNG + PrimeFlex + PrimeIcons • @angular/fire (Firebase Auth)  
**API base:** `http://localhost:8080/api` (dev)  
**Objetivo general:** UI de labs (catálogo, detalle, envío en sprints posteriores), autenticación Firebase y UX fluida con feedback claro.

---

## Convenciones
- **Ramas:** `feature/<issue>-slug`, `fix/<issue>-slug`, `chore/<issue>-slug`, `spike/<issue>-slug`.
- **Commits:** conventional commits (`feat:`, `fix:`, `chore:`…).
- **Issues:** usa plantillas (Feature/Task/Spike/Bug) y labels `type:*`, `Sprint: X`, `area: frontend`.
- **PRs:** incluye `Closes #<issue>` y screenshot/gif cuando sea UI.

---

## Sprint 1 — Fundaciones + Firebase Auth
**Meta:** App usable: login básico, catálogo de labs, detalle de lab, tema dark y CI de build.

### Entregables
- [ ] **Home + Navbar**
- [ ] **Listar labs (UI + llamada a API)**
- [ ] **Detalle de lab (`/labs/:slug`)**
- [ ] **Setup Firebase Auth + Interceptor**
- [ ] **CI build (GitHub Actions)**

### Criterios de aceptación
- [ ] Navbar con enlaces Home (`/`) y Labs (`/labs`).
- [ ] Pantalla Home con CTA “Ver labs”.
- [ ] Listado `/labs` consume `GET /api/labs` y muestra títulos + enlace.
- [ ] Detalle `/labs/:slug` consume `GET /api/labs/{slug}` y lista pasos en orden.
- [ ] Interceptor añade `Authorization: Bearer <idToken>` solo si `url.startsWith(apiBaseUrl)`.
- [ ] Toggle **dark/light** persistido en `localStorage`.
- [ ] Pipeline de build verde en PR/push.

### Notas técnicas
- `styles.scss`: importa `primeicons`, `primeng` theme `lara-light-blue`, `primeng.min.css`, `primeflex`.
- `@angular/fire`: `provideFirebaseApp` + `provideAuth` en `main.ts`.
- **Toast** de errores con `MessageService` (PrimeNG).

---

## Sprint 2 — Envíos + Tiempo real (SSE/WebSocket)
**Meta:** Subir ZIP con la solución y ver progreso de validación en vivo.

### Entregables
- [ ] Pantalla “Enviar solución” con `p-fileUpload`.
- [ ] Consola de logs y barra de progreso (SSE o WebSocket).
- [ ] Estados: `RUNNING / PASSED / FAILED`.

### Criterios de aceptación
- [ ] `POST /api/submissions` devuelve `submissionId`.
- [ ] Suscripción a `/api/submissions/{id}/stream` y render de eventos.
- [ ] UI no bloqueante, toasts claros y reintentos controlados.

---

## Sprint 3 — Admin + Métricas
**Meta:** CMS mínimo para crear/editar labs y visualizar métricas básicas.

### Entregables
- [ ] Vista Admin labs: tabla + `p-dialog` para CRUD.
- [ ] Drag & drop para reordenar `step_index`.
- [ ] Charts (`p-chart`) con completados y tasa de error.

### Criterios de aceptación
- [ ] Permisos de vista basados en rol (guard básico).
- [ ] CRUD funcional (contra endpoints admin del backend).
- [ ] Charts con datos reales.

---

## Sprint 4 — Docs UX + “How it’s built”
**Meta:** Página interna que explique la arquitectura y decisiones.

### Entregables
- [ ] `/how-its-built`: diagrama C4 simple, ADRs, enlaces a Swagger/Compodoc.
- [ ] Captura Lighthouse (>90 performance/SEO en Home).

---

## Checklist de instalación (dev)
- [ ] `npm i primeng primeicons primeflex @angular/fire firebase`
- [ ] `environment.ts` con claves de Firebase y `apiBaseUrl`.
- [ ] Interceptor JWT operativo (solo para llamadas al backend).
- [ ] Scripts: `"start"`, `"build"`, `"lint"`, `"test"`.

---

## CI / Calidad
- [ ] `.github/workflows/ci.yml`: Node 20, `npm ci`, cache, `npm run build`.
- [ ] Lint + formateo (ESLint/Prettier) opcionales.

---

## Enlaces
- **Backend Swagger:** `/swagger-ui/index.html`
- **Project board:** <añade URL si usas GitHub Projects>
