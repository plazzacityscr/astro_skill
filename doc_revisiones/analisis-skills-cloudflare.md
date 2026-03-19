# Análisis de Skills de Cloudflare Workers

Comparativa exhaustiva de los cuatro recursos disponibles para desarrollo en Cloudflare Workers.

**Fecha de análisis**: 14 de marzo de 2026
**Fuentes analizadas**:
- `/workspaces/astro_skill/.agents/skills/cloudflare-workers/SKILL.md`
- `/workspaces/astro_skill/.agents/skills/cloudflare-full-stack-scaffold/` (todos los archivos)
- `/workspaces/astro_skill/.agents/skills/cloudflare-worker-dev/SKILL.md`
- `/workspaces/astro_skill/.agents/skills/bun-cloudflare-workers/SKILL.md`

---

## 1. Explicación Individual de Cada Skill

| ID | Skill | Qué es | Qué hace | Funciones que ofrece | Ventajas | Público objetivo | Cómo se usa | Cómo se dan órdenes/instrucciones |
|----|-------|--------|----------|---------------------|----------|------------------|-------------|-----------------------------------|
| 1 | **cloudflare-workers** | Skill de despliegue básico para Cloudflare Workers | Permite crear, configurar y desplegar workers serverless en la red edge de Cloudflare | - Creación de proyectos con C3 (create-cloudflare-cli)<br>- Configuración de Wrangler<br>- Implementación de fetch handler<br>- Gestión de rutas y métodos HTTP<br>- Configuración de tokens API<br>- Despliegue con wrangler deploy<br>- Uso de KV Storage<br>- Variables de entorno y secretos | - Enfoque minimalista y directo<br>- Documentación clara de prerequisitos<br>- Incluye patrones comunes (CORS, métodos HTTP, parámetros de ruta)<br>- Sección de troubleshooting con soluciones específicas<br>- No requiere framework adicional | - Desarrolladores que necesitan APIs serverless simples<br>- Proyectos de proxy o transformación de peticiones<br>- Casos de uso en edge computing básico<br>- Usuarios que prefieren configuración manual sin scaffolding | 1. Crear token API en Cloudflare<br>2. Registrar subdominio workers.dev<br>3. Ejecutar `npm create cloudflare@latest`<br>4. Configurar wrangler.jsonc<br>5. Implementar handler en src/index.js<br>6. Probar con `npx wrangler dev`<br>7. Desplegar con `npx wrangler deploy` | Mediante comandos de terminal (wrangler) y edición directa del archivo src/index.js con el patrón fetch handler. Las instrucciones se dan modificando el código del worker y la configuración en wrangler.jsonc |
| 2 | **cloudflare-full-stack-scaffold** | Andamio (scaffold) completo para aplicaciones full-stack en Cloudflare | Proporciona un proyecto starter production-ready con React, Hono, AI SDK y todos los servicios de Cloudflare preconfigurados | - Proyecto scaffold completo copiable<br>- Scripts helper (setup-project.sh, init-services.sh, enable-auth.sh, enable-ai-chat.sh, enable-queues.sh, enable-vectorize.sh)<br>- Integración AI SDK con múltiples proveedores<br>- Servicios Cloudflare preconfigurados (D1, KV, R2, Workers AI, Vectorize, Queues)<br>- Autenticación opcional con Clerk<br>- Documentación de planificación (docs/)<br>- Protocolo de handoff de sesión (SCRATCHPAD.md)<br>- Tailwind v4 + shadcn/ui<br>- React Hook Form + Zod + TanStack Query | - Ahorro de 3-4 horas en configuración inicial<br>- Previene 12+ errores de configuración<br>- Ahorro de ~90% tokens (~44-58k → ~3-6k tokens)<br>- Todos los servicios preconfigurados y probados<br>- Características opcionales activables con scripts<br>- Incluye documentación de planificación desde el inicio<br>- Patrones de integración frontend-backend ya resueltos | - Equipos que inician proyectos full-stack nuevos<br>- Aplicaciones con IA (chat, RAG, tool calling)<br>- Proyectos que requieren múltiples servicios Cloudflare<br>- Desarrollo production-ready con mejores prácticas<br>- Evitar tiempo de configuración inicial | 1. Copiar directorio scaffold/<br>2. Ejecutar `npm install`<br>3. Inicializar servicios con scripts<br>4. Ejecutar `npm run dev`<br>5. Habilitar características opcionales con scripts enable-* | Mediante scripts de shell (enable-auth.sh, enable-ai-chat.sh, etc.), comandos npm (npm run enable-auth, npm run dev, npm run build, npm run deploy), y edición de archivos del scaffold. Las instrucciones también se dan mediante comentarios en el código que se descomentan con los scripts |
| 3 | **cloudflare-worker-dev** | Skill de desarrollo avanzado para Workers, KV y Durable Objects | Facilita el desarrollo de APIs edge de alto rendimiento con patrones avanzados de caching, rate limiting y características en tiempo real | - Patrones de arquitectura (cuándo usar cada servicio)<br>- Estructura básica de Worker con TypeScript<br>- Gestión de CORS<br>- Configuración wrangler.toml<br>- Operaciones KV (lectura, escritura, TTL, metadata, list)<br>- Caching basado en geohash<br>- Rate limiting por IP<br>- Durable Objects para coordinación en tiempo real<br>- WebSockets en Durable Objects<br>- Triggers programados (cron)<br>- Comandos de deployment y debugging | - Incluye patrones anti-patrón con explicaciones<br>- Ejemplos específicos de rate limiting y caching<br>- Soporte para Durable Objects con WebSockets<br>- Incluye tabla de códigos de error<br>- Metadata de pairing con otras skills<br>- allowed-tools definidos explícitamente | - Desarrolladores de APIs edge de alto rendimiento<br>- Sistemas de caching distribuido<br>- Aplicaciones en tiempo real (chat, coordinación)<br>- Casos de uso con rate limiting<br>- Integración con otras skills de DevOps | 1. Definir interfaz Env con bindings<br>2. Implementar fetch handler con TypeScript<br>3. Configurar wrangler.toml con servicios<br>4. Usar patrones KV para caching<br>5. Implementar rate limiting si es necesario<br>6. Desplegar con wrangler deploy<br>7. Debuggear con wrangler tail | Mediante edición de código TypeScript con patrones específicos (checkRateLimit, getMeetingsWithCache, etc.), configuración en wrangler.toml, y comandos wrangler. Las instrucciones se dan implementando los patrones de código proporcionados y usando los comandos de gestión de KV, logs y deployment |
| 4 | **bun-cloudflare-workers** | Skill para desarrollo de Workers usando Bun como runtime de desarrollo | Permite construir y desplegar Cloudflare Workers utilizando Bun para gestión de paquetes, build y testing | - Creación de proyectos con bunx create-cloudflare<br>- Configuración de package.json con scripts Bun<br>- Uso de Hono con Bun<br>- Operaciones KV y D1<br>- Durable Objects<br>- Almacenamiento R2<br>- Testing con Bun test<br>- Build para producción con Bun.build<br>- Variables de entorno y secretos<br>- Workers programados (cron) | - Mayor velocidad de desarrollo con Bun<br>- Testing integrado con bun:test<br>- Build optimizado con Bun.build<br>- Sintaxis más concisa en configuración<br>- Compatible con wrangler existente<br>- Tabla de compatibilidad de APIs (qué funciona y qué no) | - Desarrolladores que ya usan Bun en su flujo<br>- Proyectos que buscan velocidad en build/test<br>- Equipos que prefieren Bun sobre npm/node<br>- Desarrollo de Workers con tooling moderno | 1. Crear proyecto con `bunx create-cloudflare`<br>2. Instalar dependencias con `bun install`<br>3. Configurar wrangler.toml<br>4. Implementar worker con TypeScript<br>5. Desarrollo con `bun run dev`<br>6. Testing con `bun test`<br>7. Build con `bun run build.ts`<br>8. Deploy con `bun run deploy` | Mediante comandos Bun (bunx, bun install, bun run, bun test, bun build) y edición de archivos TypeScript. Las instrucciones se dan usando los comandos específicos de Bun y siguiendo los patrones de código proporcionados para cada servicio |

---

## 2. Diferencias Entre los Cuatro Skills

| ID | Aspecto | cloudflare-workers | cloudflare-full-stack-scaffold | cloudflare-worker-dev | bun-cloudflare-workers |
|----|---------|-------------------|-------------------------------|----------------------|----------------------|
| 1 | **Nivel de abstracción** | Bajo: configuración manual desde cero | Alto: proyecto completo preconfigurado | Medio: patrones avanzados listos para implementar | Medio: tooling Bun sobre configuración estándar |
| 2 | **Stack tecnológico** | JavaScript/TypeScript puro, sin framework | React 19 + Hono + AI SDK + Tailwind v4 + shadcn/ui | TypeScript con patrones específicos | Bun + Hono + TypeScript |
| 3 | **Enfoque principal** | Despliegue básico y fundamentos | Full-stack production-ready con IA | Desarrollo avanzado con patrones específicos | Desarrollo con tooling Bun |
| 4 | **Servicios Cloudflare** | KV (básico), variables, secretos | D1, KV, R2, Workers AI, Vectorize, Queues (todos preconfigurados) | KV, Durable Objects, R2, D1 (con patrones avanzados) | KV, D1, Durable Objects, R2 (con Bun) |
| 5 | **Frontend incluido** | No incluye frontend | React completo con routing, componentes, temas | No incluye frontend | No incluye frontend |
| 6 | **Autenticación** | No incluida | Clerk opcional (comentado, activable con script) | No incluida | No incluida |
| 7 | **Inteligencia Artificial** | No mencionada | AI SDK con múltiples proveedores (Workers AI, OpenAI, Anthropic, Gemini) | No mencionada | No mencionada |
| 8 | **Scripts helper** | No tiene | 6 scripts (setup, init-services, enable-auth, enable-ai-chat, enable-queues, enable-vectorize) | No tiene | No tiene (usa comandos bun) |
| 9 | **Documentación de planificación** | No incluye | docs/ completo (ARCHITECTURE, DATABASE_SCHEMA, API_ENDPOINTS, etc.) + SCRATCHPAD.md | No incluye | No incluye |
| 10 | **Patrones anti-patrón** | No incluye | No incluye explícitamente | Incluye 5 anti-patrones con explicación | Incluye tabla de APIs compatibles/incompatibles |
| 11 | **Testing** | No mencionado | No mencionado explícitamente | No mencionado | Testing con bun:test y Miniflare |
| 12 | **Durable Objects** | No menciona | No menciona en routes del scaffold | Incluye ejemplo completo con WebSockets | Incluye ejemplo básico |
| 13 | **Rate limiting** | No incluye | No incluye | Incluye implementación completa por IP | No incluye |
| 14 | **Caching avanzado** | No incluye | No incluye específicamente | Incluye caching por geohash con metadata | No incluye específicamente |
| 15 | **Configuración** | wrangler.jsonc | wrangler.jsonc + vite.config.ts + múltiples configs | wrangler.toml | wrangler.toml + package.json scripts |
| 16 | **Metadata de skill** | name, description, license, metadata | name, description, license, metadata, references, content, sections | name, description, allowed-tools, metadata (category, tags, pairs-with) | name, description |
| 17 | **Ahorro estimado** | No cuantificado | ~90% tokens, ~95% tiempo (3-4h → 5-10min) | No cuantificado | No cuantificado |
| 18 | **Errores prevenidos** | No cuantificados | 12+ errores de configuración e integración | No cuantificados | No cuantificados |

---

## 3. Complementariedad Entre los Cuatro Skills

| ID | Área de complementariedad | cloudflare-workers aporta | cloudflare-full-stack-scaffold aporta | cloudflare-worker-dev aporta | bun-cloudflare-workers aporta |
|----|---------------------------|--------------------------|--------------------------------------|-----------------------------|------------------------------|
| 1 | **Configuración inicial** | Fundamentos de wrangler.jsonc, tokens API, subdominio workers.dev | Proyecto completo copiable con todas las configuraciones ya hechas | Configuración wrangler.toml con todos los servicios | Scripts de package.json optimizados para Bun |
| 2 | **KV Storage** | Operaciones básicas (put, get, delete) con TTL | KV preconfigurado en wrangler.jsonc con ejemplos en routes/kv.ts | Patrones avanzados: geohash caching, metadata, list con cursor | Operaciones KV con sintaxis Bun |
| 3 | **Manejo de CORS** | Headers CORS básicos y manejo de OPTIONS | Middleware CORS aplicado en orden correcto (antes de rutas) | Funciones handleCORS y json helper con headers completos | CORS implícito en Hono |
| 4 | **Variables y secretos** | Configuración en wrangler.jsonc, secretos con wrangler secret put | .dev.vars.example completo, secrets para producción | Variables en wrangler.toml [vars], secretos externos | Variables en wrangler.toml, acceso desde env |
| 5 | **Estructura de proyecto** | Estructura mínima (src/index.js, wrangler.jsonc, package.json) | Estructura completa frontend/backend con 57 archivos | Estructura TypeScript con interfaz Env definida | Estructura con scripts Bun y build configuration |
| 6 | **Despliegue** | Comandos wrangler deploy, verificación, troubleshooting | Scripts npm run build y npm run deploy, migraciones DB | Comandos wrangler con flags --env, --remote | Comandos bun run deploy, bun build para producción |
| 7 | **Desarrollo local** | npx wrangler dev, testing con curl | npm run dev con Vite + Worker en mismo puerto | npx wrangler dev --remote para servicios reales | bun run dev, bunx wrangler dev |
| 8 | **TypeScript** | Opcional (ejemplo en JS) | TypeScript completo con tipos inferidos | TypeScript con interfaz Env explícita | TypeScript con build de Bun |
| 9 | **R2 Storage** | No menciona | R2 preconfigurado con ejemplos upload/download | Patrones de streaming, metadata, pagination | Operaciones R2 con Bun |
| 10 | **D1 Database** | No menciona | D1 con schema.sql, migraciones, typed queries | No enfocado en D1 | D1 con prepare, bind, batch transactions |
| 11 | **Durable Objects** | No menciona | No incluye en scaffold | Ejemplo completo ChatRoom con WebSockets | Ejemplo Counter con persistencia |
| 12 | **Testing** | No menciona | No menciona explícitamente | No menciona explícitamente | bun:test, Miniflare para testing |
| 13 | **Build/Bundle** | wrangler maneja el build | Vite + @cloudflare/vite-plugin, wrangler deploy | wrangler maneja el build | Bun.build con target browser, minify, sourcemap |
| 14 | **Manejo de errores** | Tabla de troubleshooting común | Errores prevenidos por configuración pre-hecha | Tabla de códigos de error (1101, 1102, 1015, 524) | Tabla de errores comunes (Bun API, module, script size, CPU) |
| 15 | **Patrones de código** | Fetch handler básico, routing switch | Routes separadas por servicio con Hono | Patrones específicos (checkRateLimit, getMeetingsWithCache) | Hono app pattern, export default app |
| 16 | **Documentación** | Referencias a docs oficiales de Cloudflare | docs/ completo + SCRATCHPAD.md + 5 reference guides | Referencias a /references/ locales | Referencias a references/bindings.md y performance.md |
| 17 | **Integración IA** | No menciona | AI SDK completo con 3 enfoques (directo, workers-ai-provider, providers externos) | No menciona | No menciona |
| 18 | **Autenticación** | No menciona | Clerk opcional con scripts enable-auth | No menciona | No menciona |

---

## 4. Papel de Cada Skill en un Flujo de Trabajo Amplio

| ID | Skill | Papel en el flujo de trabajo | Cuándo usarlo | Cuándo NO usarlo |
|----|-------|-----------------------------|---------------|------------------|
| 1 | **cloudflare-workers** | **Punto de entrada**: ideal para aprender fundamentos o crear workers simples sin overhead | - Primer contacto con Cloudflare Workers<br>- APIs serverless básicas<br>- Proxies o transformación de peticiones<br>- Proyectos que requieren configuración manual controlada | - Proyectos full-stack complejos<br>- Cuando se necesita frontend<br>- Aplicaciones con IA<br>- Cuando se busca production-ready inmediato |
| 2 | **cloudflare-full-stack-scaffold** | **Acelerador de proyectos**: proporciona base completa para aplicaciones full-stack production-ready | - Inicio de proyecto full-stack nuevo<br>- Aplicaciones con IA (chat, RAG)<br>- Cuando se necesitan múltiples servicios Cloudflare<br>- Equipos que buscan evitar errores de configuración<br>- Proyectos con planificación documentada desde el inicio | - Sitios estáticos sin backend<br>- Uso de Next.js, Remix, Astro<br>- APIs backend-only sin frontend<br>- Aplicaciones extremadamente simples |
| 3 | **cloudflare-worker-dev** | **Optimizador avanzado**: proporciona patrones específicos para casos de uso complejos | - APIs edge de alto rendimiento<br>- Sistemas de caching distribuido<br>- Rate limiting por IP<br>- Aplicaciones en tiempo real con Durable Objects<br>- Coordinación entre workers | - Proyectos simples sin necesidades de caching<br>- Cuando no se requiere rate limiting<br>- Sin necesidades de tiempo real<br>- Frontend-heavy applications |
| 4 | **bun-cloudflare-workers** | **Optimizador de tooling**: acelera desarrollo con Bun para build, test y gestión de dependencias | - Equipos que ya usan Bun<br>- Cuando se busca velocidad en build/test<br>- Desarrollo con tooling moderno<br>- Proyectos que priorizan velocidad de iteración | - Equipos comprometidos con npm/yarn/pnpm<br>- Cuando se requieren APIs específicas de Node<br>- Entornos que no soportan Bun |

---

## 5. Recomendación para Iniciar un Proyecto Nuevo en Cloudflare Desde Cero (Metodología Doc-First)

### Contexto de la recomendación

Esta recomendación se enfoca en una metodología **doc-first**, donde primero se realiza:
1. El diseño del proyecto
2. La definición estructural
3. El plan de desarrollo

Antes de comenzar a desarrollar.

### Análisis de evidencia encontrada

De los cuatro skills analizados, **únicamente cloudflare-full-stack-scaffold** incluye documentación de planificación explícita como parte integral del recurso:

**Documentación incluida en cloudflare-full-stack-scaffold**:
- `docs/ARCHITECTURE.md` - Diseño del sistema
- `docs/DATABASE_SCHEMA.md` - Esquema de base de datos D1
- `docs/API_ENDPOINTS.md` - Todos los routes documentados
- `docs/IMPLEMENTATION_PHASES.md` - Enfoque de construcción por fases
- `docs/UI_COMPONENTS.md` - Jerarquía de componentes
- `docs/TESTING.md` - Estrategia de tests
- `SCRATCHPAD.md` - Protocolo de handoff de sesión con tracking de fase actual, checkpoints de progreso y siguientes acciones

**Los otros tres skills NO incluyen**:
- cloudflare-workers: No tiene documentación de planificación, solo referencias a docs oficiales externos
- cloudflare-worker-dev: No tiene documentación de planificación, solo referencias a /references/ locales
- bun-cloudflare-workers: No tiene documentación de planificación, solo referencias a references/bindings.md y performance.md

### Recomendación

**Para comenzar un proyecto nuevo en Cloudflare desde cero con metodología doc-first, conviene utilizar: `cloudflare-full-stack-scaffold`**

### Razones basadas en evidencia de los archivos analizados

1. **Único con documentación de planificación estructurada**: Es el único skill que incluye un directorio `docs/` completo con 6 archivos de planificación cubriendo arquitectura, esquema de base de datos, endpoints API, fases de implementación, componentes UI y estrategia de testing.

2. **Protocolo de handoff de sesión**: Incluye `SCRATCHPAD.md` con tracking de fase actual, checkpoints de progreso y siguientes acciones, lo cual facilita la continuidad del desarrollo entre sesiones.

3. **Enfoque por fases documentado**: El archivo `docs/IMPLEMENTATION_PHASES.md` proporciona un plan de desarrollo estructurado por fases, alineado con la metodología doc-first.

4. **Definición estructural preestablecida**: La estructura del scaffold (57 archivos) proporciona una definición estructural completa que puede servir como punto de partida para la planificación del proyecto.

5. **Ahorro cuantificado**: Según la documentación analizada, el scaffold ahorra ~90% de tokens (~44-58k → ~3-6k tokens) y ~95% de tiempo (3-4 horas → 5-10 minutos), además de prevenir 12+ errores de configuración.

### Limitaciones de la recomendación

**Información no disponible en los archivos analizados**:
- No hay evidencia sobre cómo adaptar la documentación de planificación del scaffold a proyectos que no requieren todas las características incluidas (por ejemplo, proyectos sin IA, sin autenticación, sin frontend)
- No hay información sobre el proceso de personalización de los documentos de planificación para proyectos específicos
- Los otros tres skills no proporcionan alternativas de documentación de planificación que puedan combinarse con cloudflare-full-stack-scaffold

### Conclusión

Basado exclusivamente en la evidencia encontrada en los directorios analizados, **cloudflare-full-stack-scaffold** es el único recurso que soporta explícitamente una metodología doc-first al incluir documentación de planificación estructurada como parte integral del skill. Los otros tres recursos (cloudflare-workers, cloudflare-worker-dev, bun-cloudflare-workers) se enfocan en aspectos técnicos específicos pero no proporcionan documentación de planificación que pueda usarse para diseño, definición estructural y plan de desarrollo previos al desarrollo.

---

**Documento generado a partir del análisis exclusivo de**:
- `/workspaces/astro_skill/.agents/skills/cloudflare-workers/SKILL.md`
- `/workspaces/astro_skill/.agents/skills/cloudflare-full-stack-scaffold/` (SKILL.md, README.md, IMPLEMENTATION_STATUS.md, SKILL.json)
- `/workspaces/astro_skill/.agents/skills/cloudflare-worker-dev/SKILL.md`
- `/workspaces/astro_skill/.agents/skills/bun-cloudflare-workers/SKILL.md`
