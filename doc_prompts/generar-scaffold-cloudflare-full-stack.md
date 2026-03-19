# Prompt: Generación Automática del Scaffold Cloudflare Full-Stack

**Fecha de creación**: 14 de marzo de 2026  
**Destino**: Modelo de inteligencia artificial  
**Propósito**: Generar automáticamente los 57 archivos del scaffold cloudflare-full-stack-scaffold  
**Ubicación del proyecto**: `C:\DD\UA_Pyts_EnDES\UA CF Eo\VCS_eo\.roo\skills\scaffold-cloudflare-full-stack`

---

## 1. Comprensión del Objetivo

### Objetivo Principal

**Generar automáticamente el scaffold completo del proyecto cloudflare-full-stack-scaffold** para que quede listo como base de trabajo inmediata.

### Resultado Final Esperado

Una **estructura funcional inicial** que incluya:
- ✅ Los 57 archivos completos descritos en la documentación
- ✅ Organización correcta de carpetas y subcarpetas
- ✅ Contenido funcional y probado según la documentación
- ✅ Proyecto listo para ejecutar `npm install` y comenzar a trabajar

### Alcance del Trabajo

El scaffold debe incluir **TODOS** los archivos necesarios para:
1. Frontend React 19 + Vite + Tailwind v4 + shadcn/ui
2. Backend Hono + Cloudflare Workers
3. Integración con servicios Cloudflare (D1, KV, R2, Workers AI)
4. Scripts de automatización (setup, init-services, enable-*)
5. Documentación de planificación (docs/)
6. Guías de referencia (references/)

---

## 2. Lectura Previa Obligatoria

### Archivos que DEBES leer antes de comenzar

**Ubicación**: `C:\DD\UA_Pyts_EnDES\UA CF Eo\VCS_eo\.roo\skills\scaffold-cloudflare-full-stack\`

| Archivo | Propósito de lectura |
|---------|---------------------|
| `SKILL.md` | Contiene la definición completa del skill, dependencias, estructura del proyecto, patrones de código, y ejemplos de todos los servicios |
| `IMPLEMENTATION_STATUS.md` | Contiene el inventario completo de los 57 archivos, estado de implementación, patrones verificados, y fixes aplicados |
| `documentacion_Cloudflare Full-Stack Scaffold.md` | Contiene la documentación consolidada del scaffold, guías de uso, ejemplos de integración, y referencias de arquitectura |

### Qué debes extraer de cada documento

**De SKILL.md**:
- Lista completa de dependencias (package.json)
- Estructura de directorios del scaffold
- Patrones de código para cada servicio
- Configuración de wrangler.jsonc y vite.config.ts
- Ejemplos de rutas backend (api.ts, d1.ts, kv.ts, r2.ts, ai.ts, ai-sdk.ts)
- Configuración de TypeScript y Vite

**De IMPLEMENTATION_STATUS.md**:
- Inventario exacto de los 57 archivos (File Inventory section)
- Estado de cada archivo (completado ✅)
- Patrones de comment markers para características opcionales
- Fixes aplicados (AI SDK v5, binding names, etc.)
- Grupos de implementación (Helper Scripts, Backend Middleware, Backend Routes, etc.)
- Verification results de cada grupo

**De documentacion_Cloudflare Full-Stack Scaffold.md**:
- Estructura completa del scaffold (Scaffold Structure section)
- Contenido de cada archivo del scaffold
- Ejemplos de código para frontend y backend
- Configuración de servicios Cloudflare
- Patrones de integración (AI SDK, Forms, Auth)
- Guías de personalización

---

## 3. Comprensión de la Estructura

### Estructura Completa del Scaffold (57 archivos)

Debes generar **exactamente** esta estructura:

```
scaffold-cloudflare-full-stack/
├── SKILL.md                          ← YA EXISTE (leer para referencia)
├── README.md                         ← YA EXISTE (leer para referencia)
├── IMPLEMENTATION_STATUS.md          ← YA EXISTE (leer para referencia)
├── documentacion_Cloudflare Full-Stack Scaffold.md ← YA EXISTE (leer para referencia)
│
├── scaffold/                         ← GENERAR (44 archivos)
│   ├── package.json                  ← Frontend + Backend dependencies
│   ├── tsconfig.json                 ← TypeScript root config
│   ├── vite.config.ts                ← Vite + Cloudflare plugin
│   ├── wrangler.jsonc                ← Cloudflare Workers config
│   ├── .gitignore                    ← Node/Cloudflare ignores
│   ├── .dev.vars.example             ← Environment variables template
│   ├── index.html                    ← Vite entry HTML
│   ├── README.md                     ← Project readme
│   ├── CLAUDE.md                     ← Claude project instructions
│   ├── SCRATCHPAD.md                 ← Session handoff protocol
│   ├── CHANGELOG.md                  ← Version history
│   ├── schema.sql                    ← D1 database schema
│   ├── components.json               ← shadcn/ui config
│   ├── .env.example                  ← Frontend env template
│   │
│   ├── docs/                         ← Planning docs (6 archivos)
│   │   ├── ARCHITECTURE.md           ← System design
│   │   ├── DATABASE_SCHEMA.md        ← D1 schema documentation
│   │   ├── API_ENDPOINTS.md          ← All routes documented
│   │   ├── IMPLEMENTATION_PHASES.md  ← Phased implementation approach
│   │   ├── UI_COMPONENTS.md          ← Component hierarchy
│   │   └── TESTING.md                ← Test strategy
│   │
│   ├── migrations/                   ← D1 migrations (1 archivo)
│   │   └── 0001_initial.sql          ← Initial migration
│   │
│   ├── src/                          ← Frontend React (11 archivos)
│   │   ├── main.tsx                  ← React 19 entry point
│   │   ├── App.tsx                   ← React Router v7 setup
│   │   ├── index.css                 ← Tailwind v4 theming
│   │   ├── vite-env.d.ts             ← Vite type definitions
│   │   │
│   │   ├── lib/                      ← Frontend utilities (2 archivos)
│   │   │   ├── utils.ts              ← cn() utility function
│   │   │   └── api-client.ts         ← Fetch wrapper with types
│   │   │
│   │   ├── components/               ← React components (4 archivos)
│   │   │   ├── ui/.gitkeep           ← Placeholder for shadcn
│   │   │   ├── ThemeProvider.tsx     ← Dark/light/system theme
│   │   │   ├── ProtectedRoute.tsx    ← Auth gate (COMMENTED)
│   │   │   └── ChatInterface.tsx     ← AI chat UI (COMMENTED)
│   │   │
│   │   └── pages/                    ← React pages (3 archivos)
│   │       ├── Home.tsx              ← Landing page
│   │       ├── Dashboard.tsx         ← D1/KV demo page
│   │       └── Chat.tsx              ← Chat page (COMMENTED)
│   │
│   └── backend/                      ← Backend Hono (19 archivos)
│       ├── src/
│       │   └── index.ts              ← Worker entry point
│       │
│       ├── tsconfig.json             ← Backend TypeScript config
│       │
│       ├── middleware/               ← Hono middleware (2 archivos)
│       │   ├── cors.ts               ← CORS handling
│       │   └── auth.ts               ← JWT auth (COMMENTED)
│       │
│       ├── routes/                   ← API routes (8 archivos)
│       │   ├── api.ts                ← Basic routes (echo, status, data, search)
│       │   ├── d1.ts                 ← D1 CRUD operations
│       │   ├── kv.ts                 ← KV storage operations
│       │   ├── r2.ts                 ← R2 object storage
│       │   ├── ai.ts                 ← Workers AI direct binding
│       │   ├── ai-sdk.ts             ← AI SDK multiple providers
│       │   ├── vectorize.ts          ← Vectorize RAG (COMMENTED)
│       │   └── queues.ts             ← Queues async (COMMENTED)
│       │
│       └── db/
│           └── queries.ts            ← Typed D1 query helpers
│
├── scripts/                          ← GENERAR (6 archivos)
│   ├── setup-project.sh              ← Copy scaffold, rename, init git
│   ├── init-services.sh              ← Create D1/KV/R2 via wrangler
│   ├── enable-auth.sh                ← Uncomment Clerk auth patterns
│   ├── enable-ai-chat.sh             ← Uncomment AI chat UI patterns
│   ├── enable-queues.sh              ← Uncomment Queues patterns
│   └── enable-vectorize.sh           ← Uncomment Vectorize patterns
│
└── references/                       ← GENERAR (5 archivos)
    ├── quick-start-guide.md          ← 5-minute setup walkthrough
    ├── service-configuration.md      ← Details on each Cloudflare service
    ├── ai-sdk-guide.md               ← AI SDK Core vs UI patterns
    ├── customization-guide.md        ← Removing services, adding features
    └── enabling-auth.md              ← Clerk setup walkthrough
```

### Conteo de Archivos por Generar

| Categoría | Archivos a generar |
|-----------|-------------------|
| **scaffold/** | 44 archivos |
| ├── Config files | 13 archivos |
| ├── docs/ | 6 archivos |
| ├── migrations/ | 1 archivo |
| ├── src/ | 11 archivos |
| └── backend/ | 13 archivos |
| **scripts/** | 6 archivos |
| **references/** | 5 archivos |
| **TOTAL** | **55 archivos nuevos** |

---

## 4. Inicio del Proceso de Generación

### Reglas de Generación

1. **Leer primero, generar después**: No generar ningún archivo hasta haber leído los 3 documentos fuente.

2. **Seguir exactamente la documentación**: Usar los patrones de código, estructuras y configuraciones descritas en los documentos.

3. **Mantener consistencia**: 
   - Mismos nombres de archivos que en `IMPLEMENTATION_STATUS.md`
   - Mismas rutas que en `SKILL.md`
   - Mismos patrones de código que en `documentacion_Cloudflare Full-Stack Scaffold.md`

4. **Comment markers correctos**: Para características opcionales (Auth, AI Chat, Queues, Vectorize), usar los comment markers especificados:
   ```typescript
   /* CLERK AUTH START
   ... código ...
   CLERK AUTH END */
   
   /* AI CHAT START
   ... código ...
   AI CHAT END */
   
   /* QUEUES START
   ... código ...
   QUEUES END */
   
   /* VECTORIZE START
   ... código ...
   VECTORIZE END */
   ```

5. **Binding names consistentes**: Usar el prefijo `MY_` para todos los bindings de Cloudflare:
   - `MY_KV` (no `KV`)
   - `MY_BUCKET` (no `BUCKET`)
   - `MY_VECTORIZE` (no `VECTORIZE_INDEX`)
   - `MY_QUEUE` (no `QUEUE`)

6. **Versiones actualizadas**: Usar las versiones de paquetes verificadas en `IMPLEMENTATION_STATUS.md`:
   - react: ^19.2.0
   - react-router-dom: ^7.9.4
   - hono: ^4.10.2
   - ai: ^5.0.76
   - @ai-sdk/react: ^2.0.76
   - tailwindcss: ^4.1.15
   - wrangler: ^4.44.0

### Orden de Generación Recomendado

**Fase 1: Archivos de Configuración (13 archivos)**
1. `scaffold/package.json`
2. `scaffold/tsconfig.json`
3. `scaffold/vite.config.ts`
4. `scaffold/wrangler.jsonc`
5. `scaffold/.gitignore`
6. `scaffold/.dev.vars.example`
7. `scaffold/index.html`
8. `scaffold/README.md`
9. `scaffold/CLAUDE.md`
10. `scaffold/SCRATCHPAD.md`
11. `scaffold/CHANGELOG.md`
12. `scaffold/schema.sql`
13. `scaffold/components.json`
14. `scaffold/.env.example`

**Fase 2: Backend (13 archivos)**
1. `scaffold/backend/src/index.ts`
2. `scaffold/backend/tsconfig.json`
3. `scaffold/backend/middleware/cors.ts`
4. `scaffold/backend/middleware/auth.ts`
5. `scaffold/backend/routes/api.ts`
6. `scaffold/backend/routes/d1.ts`
7. `scaffold/backend/routes/kv.ts`
8. `scaffold/backend/routes/r2.ts`
9. `scaffold/backend/routes/ai.ts`
10. `scaffold/backend/routes/ai-sdk.ts`
11. `scaffold/backend/routes/vectorize.ts`
12. `scaffold/backend/routes/queues.ts`
13. `scaffold/backend/db/queries.ts`

**Fase 3: Frontend (11 archivos)**
1. `scaffold/src/main.tsx`
2. `scaffold/src/App.tsx`
3. `scaffold/src/index.css`
4. `scaffold/src/vite-env.d.ts`
5. `scaffold/src/lib/utils.ts`
6. `scaffold/src/lib/api-client.ts`
7. `scaffold/src/components/ui/.gitkeep`
8. `scaffold/src/components/ThemeProvider.tsx`
9. `scaffold/src/components/ProtectedRoute.tsx`
10. `scaffold/src/components/ChatInterface.tsx`
11. `scaffold/src/pages/Home.tsx`
12. `scaffold/src/pages/Dashboard.tsx`
13. `scaffold/src/pages/Chat.tsx`

**Fase 4: Documentación de Planificación (6 archivos)**
1. `scaffold/docs/ARCHITECTURE.md`
2. `scaffold/docs/DATABASE_SCHEMA.md`
3. `scaffold/docs/API_ENDPOINTS.md`
4. `scaffold/docs/IMPLEMENTATION_PHASES.md`
5. `scaffold/docs/UI_COMPONENTS.md`
6. `scaffold/docs/TESTING.md`

**Fase 5: Migraciones (1 archivo)**
1. `scaffold/migrations/0001_initial.sql`

**Fase 6: Scripts (6 archivos)**
1. `scripts/setup-project.sh`
2. `scripts/init-services.sh`
3. `scripts/enable-auth.sh`
4. `scripts/enable-ai-chat.sh`
5. `scripts/enable-queues.sh`
6. `scripts/enable-vectorize.sh`

**Fase 7: Referencias (5 archivos)**
1. `references/quick-start-guide.md`
2. `references/service-configuration.md`
3. `references/ai-sdk-guide.md`
4. `references/customization-guide.md`
5. `references/enabling-auth.md`

---

## 5. Resultado Esperado

### Criterios de Éxito

El scaffold generado debe cumplir:

1. ✅ **57 archivos totales** (4 existentes + 55 generados)
2. ✅ **Estructura idéntica** a la descrita en `IMPLEMENTATION_STATUS.md`
3. ✅ **Contenido funcional** basado en los patrones de `SKILL.md`
4. ✅ **Documentación completa** en `scaffold/docs/`
5. ✅ **Scripts ejecutables** con permisos chmod +x
6. ✅ **Comment markers correctos** para características opcionales
7. ✅ **Binding names consistentes** con prefijo `MY_`
8. ✅ **Versiones actualizadas** en package.json

### Verificación Post-Generación

Después de generar todos los archivos, ejecutar:

```bash
# Contar archivos totales
find scaffold-cloudflare-full-stack -type f | wc -l
# Debe devolver: 57 (o más si hay archivos adicionales)

# Verificar estructura de directorios
tree scaffold-cloudflare-full-stack

# Verificar scripts ejecutables
ls -la scaffold-cloudflare-full-stack/scripts/
```

### Próximos Pasos Después de la Generación

Una vez completado el scaffold:

1. **Copiar a proyecto destino**:
   ```bash
   cp -r scaffold-cloudflare-full-stack/scaffold/ mi-nuevo-proyecto/
   cd mi-nuevo-proyecto/
   ```

2. **Instalar dependencias**:
   ```bash
   npm install
   ```

3. **Inicializar servicios Cloudflare**:
   ```bash
   ./scripts/init-services.sh
   ```

4. **Iniciar desarrollo**:
   ```bash
   npm run dev
   ```

---

## 6. Instrucciones Finales para el Modelo de IA

### Antes de Comenzar

1. [ ] Confirmar que has leído `SKILL.md` completo
2. [ ] Confirmar que has leído `IMPLEMENTATION_STATUS.md` completo
3. [ ] Confirmar que has leído `documentacion_Cloudflare Full-Stack Scaffold.md` completo
4. [ ] Confirmar que entiendes la estructura de los 57 archivos
5. [ ] Confirmar que conoces los patrones de código requeridos

### Durante la Generación

1. Generar archivos en el orden especificado (Fases 1-7)
2. Verificar cada archivo antes de pasar al siguiente
3. Mantener consistencia en nombres, rutas y patrones
4. Usar comment markers para características opcionales
5. Incluir toda la documentación de planificación

### Después de Cada Fase

1. Verificar que todos los archivos de la fase se crearon correctamente
2. Confirmar que el contenido coincide con la documentación
3. Reportar cualquier discrepancia o duda antes de continuar

### Al Finalizar

1. Ejecutar verificación de conteo de archivos (debe ser 57)
2. Generar resumen de archivos creados
3. Proporcionar instrucciones de siguientes pasos al usuario

---

## 7. Notas Adicionales

### Características Opcionales (COMMENTED)

Los siguientes archivos deben incluir código comentado con markers:

| Archivo | Característica | Script de activación |
|---------|---------------|---------------------|
| `scaffold/src/components/ProtectedRoute.tsx` | Clerk Auth | `npm run enable-auth` |
| `scaffold/src/components/ChatInterface.tsx` | AI Chat UI | `npm run enable-ai-chat` |
| `scaffold/src/pages/Chat.tsx` | AI Chat Page | `npm run enable-ai-chat` |
| `scaffold/backend/middleware/auth.ts` | JWT Auth | `npm run enable-auth` |
| `scaffold/backend/routes/vectorize.ts` | Vectorize | `npm run enable-vectorize` |
| `scaffold/backend/routes/queues.ts` | Queues | `npm run enable-queues` |

### Servicios Cloudflare Requeridos

El scaffold asume que el usuario configurará:

**Core Services** (siempre):
- D1 Database
- KV Storage
- R2 Object Storage
- Workers AI

**Optional Services** (con enable scripts):
- Clerk Authentication
- AI Chat Interface
- Vectorize Index
- Queues

### Dependencias Críticas

Las siguientes dependencias deben estar en `package.json`:

```json
{
  "dependencies": {
    "react": "^19.2.0",
    "react-dom": "^19.2.0",
    "hono": "^4.10.2",
    "@cloudflare/vite-plugin": "^1.13.14",
    "ai": "^5.0.76",
    "@ai-sdk/react": "^2.0.76",
    "workers-ai-provider": "^2.0.0",
    "tailwindcss": "^4.1.15",
    "@tailwindcss/vite": "^4.1.15",
    "zod": "^4.1.12",
    "react-hook-form": "^7.65.0",
    "@tanstack/react-query": "^5.90.5"
  },
  "devDependencies": {
    "@cloudflare/workers-types": "^4.20251014.0",
    "wrangler": "^4.44.0",
    "vite": "^7.1.11",
    "typescript": "^5.7.2"
  }
}
```

---

**Fin del Prompt**

---

## Metadatos del Prompt

| Campo | Valor |
|-------|-------|
| **Nombre del archivo** | `generar-scaffold-cloudflare-full-stack.md` |
| **Fecha de creación** | 14 de marzo de 2026 |
| **Ubicación** | `doc_prompts/generar-scaffold-cloudflare-full-stack.md` |
| **Propósito** | Generar automáticamente los 57 archivos del scaffold |
| **Documentación fuente** | SKILL.md, IMPLEMENTATION_STATUS.md, documentacion_Cloudflare Full-Stack Scaffold.md |
| **Archivos a generar** | 55 archivos nuevos (más 4 existentes) |
| **Estructura** | 7 fases de generación |
| **Criterio de éxito** | 57 archivos totales, estructura verificada, contenido funcional |
