# Progress — Proyecto 1: Facturación y conciliación de pagos

**Alcance de esta revisión:** únicamente **FASE 0 — ENTORNO, GIT Y FUNDAMENTOS**
**Fecha de revisión:** 2026-11-16
**Rol:** supervisor (revisión de solo lectura sobre los archivos existentes)
**Carpeta revisada:** `E:\facturacion\`

---

## 1. Evidencia del barrido

| Elemento encontrado | Tipo | Tamaño | Estado |
|---|---|---|---|
| `E:\facturacion\proyecto.txt` | Documento de plan | 20.052 bytes | Presente |

**No se encontró ningún otro archivo ni carpeta**, incluyendo archivos ocultos:

- Sin `.git/` → el proyecto no está inicializado como repositorio Git.
- Sin `package.json`, `pnpm-lock.yaml`, `tsconfig.json`.
- Sin `docker-compose.yml` ni `Dockerfile`.
- Sin `src/` (API, dominio, infraestructura).
- Sin `tests/` ni configuración de Vitest.
- Sin `README.md`, `.env.example`, `.gitignore`, `.nvmrc`.
- Sin `Progress.md` previo (se crea este archivo).
- Sin `AI_LOG.md` ni ADRs.

**Conclusión del barrido:** la carpeta solo contiene el documento de definición del proyecto. No existe código, entorno ni documentación operativa de la Fase 0.

---

## 2. Métricas de éxito definidas para la Fase 0

Las métricas se derivan del entregable, los temas y los criterios de aceptación de la Fase 0 del `proyecto.txt`.

| ID | Métrica | Peso | Estado | Puntos |
|---|---|---|---|---|
| M1 | Repositorio Git inicializado, rama principal y `.gitignore` correcto | 10% | ❌ No existe | 0 |
| M2 | Toolchain reproducible: Node 22 (fnm/`.nvmrc`), pnpm, versión fijada, VS Code | 10% | ❌ No existe | 0 |
| M3 | `docker-compose.yml` operativo con Postgres 16, Redis 7 y Mailpit (healthchecks, volúmenes, puertos) | 20% | ❌ No existe | 0 |
| M4 | API mínima que responde `GET /health` con estado y versión | 20% | ❌ No existe | 0 |
| M5 | Vitest: primer test unitario, primer test de integración y prueba que falla si se rompe `/health` | 20% | ❌ No existe | 0 |
| M6 | `README.md` con instrucciones para levantar el proyecto en menos de 15 minutos + scripts de `pnpm` | 10% | ❌ No existe | 0 |
| M7 | Higiene 12-factor: `.env.example`, sin secretos, configuración validada y logs | 5% | ❌ No existe | 0 |
| M8 | Fundamentos documentados: migración/seed (concepto), notas o quizzes y `AI_LOG.md` | 5% | ❌ No existe | 0 |
| | **TOTAL FASE 0** | **100%** | | **0%** |

> El `proyecto.txt` es el insumo de la revisión, no un entregable de la fase; por eso no suma porcentaje.

---

## 3. Checklist de aceptación de la Fase 0

| Criterio del plan | Resultado | Evidencia |
|---|---|---|
| Otra persona clona el repo y lo levanta en menos de 15 minutos | ❌ Pendiente | No hay repositorio ni README |
| `/health` devuelve estado y versión | ❌ Pendiente | No hay API |
| El test falla si rompes el endpoint | ❌ Pendiente | No hay tests |
| No hay secretos en el repositorio y existe `.env.example` | ❌ Pendiente | No hay repositorio ni `.env.example` |
| `docker compose up` levanta Postgres, Redis y Mailpit | ❌ Pendiente | No hay `docker-compose.yml` |
| `pnpm test` pasa | ❌ Pendiente | No hay `package.json` ni tests |
| README con instrucciones | ❌ Pendiente | No hay `README.md` |
| Ejercicio sin IA: `/health` y su test escritos desde cero | ❌ Pendiente | No hay código |

---

## 4. Qué se necesitaba tener listo exactamente en la Fase 0

### 4.1 Entorno de desarrollo
- WSL2 + Docker Desktop funcionando.
- Node 22 instalado y versionado con `fnm` (idealmente `.nvmrc` con `22`).
- pnpm instalado y fijado con `packageManager` en `package.json`.
- Git configurado y VS Code con extensiones básicas (ESLint, Prettier, Vitest, Docker).
- `.editorconfig`, `.gitignore` y `.nvmrc`.

### 4.2 Repositorio y fundamentos
- Repositorio Git con commit inicial y rama `main`.
- Comprensión aplicada de HTTP, REST, JSON, variables de entorno, logs y 12-factor.
- Configuración separada del código y validada al arranque (por ejemplo con Zod).
- Apuntes, quizzes o notas del ejercicio sin IA.

### 4.3 Infraestructura local reproducible
- `docker-compose.yml` con:
  - PostgreSQL 16 (puerto, volumen persistente, credenciales por entorno, healthcheck).
  - Redis 7 (volumen/persistencia y healthcheck).
  - Mailpit (SMTP y UI web).
- Red interna y nombres de servicio estables.
- `.env.example` con todas las variables requeridas y sin valores reales.
- Concepto de migraciones y un seed mínimo demostrado o documentado.

### 4.4 API mínima
- Proyecto TypeScript + Fastify con scripts `dev`, `build`, `start`, `lint`, `typecheck`, `test`.
- Endpoint `GET /health` que devuelva, como mínimo:
  - estado (`ok`),
  - versión de la aplicación,
  - idealmente timestamp y estado de dependencias.
- Manejo de errores y logs estructurados básicos.
- Sin stack traces expuestos al cliente.

### 4.5 Pruebas
- Vitest configurado.
- Primer test unitario (por ejemplo, forma de la respuesta de `/health`).
- Primer test de integración (levantar la app y llamar a `/health`).
- Un test que **falle deliberadamente** si se rompe el endpoint (demostración del criterio de aceptación).
- `pnpm test` en verde desde una clonación limpia.

### 4.6 Documentación y cierre
- `README.md` con requisitos, instalación, variables, `docker compose up`, migraciones/seed, tests y troubleshooting.
- `AI_LOG.md` con el registro del uso de IA (nivel 0: explicaciones, quizzes, revisión).
- Demo de 30–60 segundos o capturas.
- Backlog actualizado y sin TODOs sueltos.

---

## 5. Resultado

**Fase 0: 0% completada (0 de 100 puntos).**

No hay avance verificable de implementación. El único activo es la definición del proyecto, que permite planificar pero no satisface ningún criterio de aceptación de la fase.

**Siguiente paso recomendado:** ejecutar el orden M1 → M2 → M3 → M4 → M5 → M6 → M7 → M8, validando cada métrica con evidencia antes de pasar a la Fase 1.

---

## 6. Historial

| Fecha | Acción | Resultado |
|---|---|---|
| 2026-11-16 | Barrido inicial y verificación de Fase 0 | 0% — solo existe `proyecto.txt` |
