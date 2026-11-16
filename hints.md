# Hints — Fase 0: Entorno, Git y Fundamentos

**Proyecto:** Facturación y conciliación de pagos
**Revisión:** 2026-11-16 · alcance exclusivo Fase 0
**Estado:** 0% — sin implementación verificable

---

## Avances resaltados

- Existe un plan de proyecto completo y bien delimitado (`proyecto.txt`): pitch,
  alcance, stack, arquitectura, modelo de datos y roadmap.
- La Fase 0 tiene objetivo, entregable, temas, criterios de aceptación y horas
  definidas, lo que permite medir el avance sin ambigüedad.
- Se realizó el barrido de la carpeta y se documentó el estado inicial.

> No hay avances de implementación que destacar: la carpeta no contiene código,
> infraestructura, pruebas ni documentación operativa.

---

## Qué falta exactamente para cerrar la Fase 0

### 1. Repositorio y toolchain
- [ ] `git init`, rama `main` y primer commit significativo.
- [ ] `.gitignore` con `node_modules/`, `dist/`, `coverage/`, `.env`, `*.log`.
- [ ] `.editorconfig` y `.nvmrc` con `22`.
- [ ] `package.json` con `packageManager: "pnpm@..."`, `engines.node: ">=22"`.
- [ ] Scripts: `dev`, `build`, `start`, `lint`, `typecheck`, `test`.
- [ ] Configuración de VS Code (opcional pero recomendada).

### 2. Infraestructura local
- [ ] `docker-compose.yml` con:
  - [ ] PostgreSQL 16 + volumen persistente + healthcheck (`pg_isready`).
  - [ ] Redis 7 + healthcheck (`redis-cli ping`).
  - [ ] Mailpit + puertos SMTP y UI.
- [ ] Red interna y `depends_on` con `condition: service_healthy`.
- [ ] `.env.example` con todas las variables (sin valores reales).

### 3. API mínima
- [ ] Fastify + TypeScript.
- [ ] `GET /health` → `{ status: "ok", version: "<package.json version>", uptime?, timestamp? }`.
- [ ] Validación de configuración al arranque (Zod).
- [ ] Logs básicos y manejo de errores sin exponer stack traces.

### 4. Pruebas
- [ ] Vitest configurado.
- [ ] Test unitario del contrato de `/health`.
- [ ] Test de integración con la app levantada.
- [ ] Prueba negativa: al romper `/health`, `pnpm test` falla.
- [ ] `pnpm test` en verde desde una clonación limpia.

### 5. Documentación
- [ ] `README.md`: requisitos, instalación, `.env`, `docker compose up`,
  migración/seed, tests, troubleshooting y tiempo esperado (<15 min).
- [ ] `AI_LOG.md` con el registro de uso de IA nivel 0.
- [ ] Notas o quizzes del ejercicio sin IA.
- [ ] Demo de 30–60 s o capturas.

---

## Orden sugerido (2–3 semanas, 10–12 h)

1. **Día 1:** repo, `.gitignore`, Node/pnpm fijados, commit inicial.
2. **Día 2:** `docker-compose.yml` + `.env.example`; validar servicios healthy.
3. **Día 3:** esqueleto Fastify + TypeScript + `/health`.
4. **Día 4:** Vitest, test unitario, integración y prueba negativa.
5. **Día 5:** README, `AI_LOG.md`, prueba de arranque limpio y demo.

---

## Señales de que la fase está realmente lista

- Una persona distinta clona el repo y, siguiendo solo el README, tiene
  Postgres, Redis y Mailpit arriba y `/health` respondiendo en <15 minutos.
- `pnpm test` falla inmediatamente si se elimina o se rompe `/health`.
- `git grep -i "password\|secret\|token"` no revela credenciales reales.
- El commit inicial contiene `.env.example`, no `.env`.
- Puedes explicar en 5 minutos qué hace `/health`, cómo se configura la app y
  cómo se levanta el entorno.

---

## Riesgos si se avanza sin cerrar la Fase 0

- Migraciones y tests de integración de la Fase 1 dependerán de un entorno no
  reproducible.
- La numeración atómica y los webhooks idempotentes de fases posteriores
  necesitan una base de datos real y estable desde el inicio.
- Sin CI ni tests base, la deuda de calidad se acumula y el criterio de
  "CI verde" de la Fase 6 se vuelve muy costoso.
