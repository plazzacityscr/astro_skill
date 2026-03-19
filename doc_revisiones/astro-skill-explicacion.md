# Astro Skill - Explicación Detallada

**Documento original:** `.agents/skills/astro/SKILL.md`

**Fecha de revisión:** 14 de marzo de 2026

---

Este documento define las capacidades y mejores prácticas para desarrollar con **Astro**, un framework moderno para crear sitios web centrados en contenido.

## 🎯 Conceptos Fundamentales

### 1. **Filosofía Zero-JS-by-Default**
Astro prioriza el rendimiento generando HTML estático por defecto. El JavaScript solo se incluye cuando es explícitamente necesario mediante hidratación parcial.

### 2. **Arquitectura de Islas**
En lugar de hidratar toda la aplicación, solo se hidratan componentes interactivos específicos ("islas") mientras el resto permanece como HTML estático.

---

## 📁 Estructura de Proyecto Detallada

```
src/
├── pages/              # Routing basado en archivos
│   ├── index.astro     # Página principal (/)
│   ├── about.astro     # Página estática (/about)
│   └── blog/
│       ├── index.astro # Listado (/blog)
│       └── [slug].astro # Ruta dinámica (/blog/:slug)
├── components/         # Componentes reutilizables (.astro, .jsx, .svelte, .vue)
├── layouts/            # Plantillas base que envuelven páginas
├── content/            # Colecciones de contenido (markdown/MDX)
└── styles/             # Estilos globales
```

---

## 🔑 Características Principales Ampliadas

### **Sintaxis de Archivos .astro**

Cada archivo tiene dos secciones claras:

| Sección | Propósito | Cuándo se ejecuta |
|---------|-----------|-------------------|
| **Frontmatter** (`---`) | Lógica, imports, fetch de datos | Build time (servidor) |
| **Template** (HTML) | Renderizado visual | Runtime (cliente como HTML) |

### **Directivas `client:*` para Hidratación**

| Directiva | Cuándo hidrata | Caso de uso ideal |
|-----------|----------------|-------------------|
| `client:load` | Inmediatamente al cargar | Búsqueda, navegación crítica |
| `client:idle` | Cuando el navegador está inactivo | Widgets no críticos |
| `client:visible` | Cuando el elemento entra en viewport | Carruseles, comentarios |
| `client:media` | Según media query | Menús móviles |
| `client:only` | Solo en cliente (sin SSR) | Componentes que dependen de APIs del navegador |

---

## 📝 Colecciones de Contenido

Las colecciones proporcionan **validación de tipos** para contenido markdown/MDX:

```typescript
// Schema con Zod
schema: z.object({
  title: z.string(),           // Requerido
  description: z.string(),     // Requerido
  pubDate: z.date(),           // Requerido
  author: z.string().default('Anonymous'), // Opcional con default
  tags: z.array(z.string()).default([]),
  draft: z.boolean().default(false),
})
```

**Ventajas:**
- Validación automática en build time
- TypeScript generado automáticamente
- Filtrado y ordenamiento tipados

---

## 🖼️ Optimización de Imágenes

Astro optimiza imágenes automáticamente:

```astro
import { Image } from 'astro:assets';
import hero from '../assets/hero.jpg';

<Image 
  src={hero} 
  alt="Descripción" 
  width={800} 
  height={600}
  loading="lazy"        // Lazy loading automático
  format="avif"         // Conversión automática de formato
/>
```

**Características:**
- Conversión automática a WebP/AVIF
- Generación de múltiples tamaños
- Lazy loading incorporado

---

## 🚀 Despliegue

### **Cloudflare Pages**
- Ideal para sitios estáticos o serverless
- Usa el adapter `@astrojs/cloudflare`
- Soporta SSR con Cloudflare Functions

### **DigitalOcean (Node.js)**
- Para aplicaciones que requieren servidor Node
- Modo `standalone` o `middleware`
- Dockerizable fácilmente

---

## ✅ Checklist de Producción

Antes de desplegar, verifica:

1. **Contenido**: Colecciones con schemas definidos
2. **Imágenes**: Usan `astro:assets` para optimización
3. **Interactividad**: Directivas `client:*` apropiadas
4. **SEO**: Meta tags en layouts
5. **Build**: `npm run build` sin errores
6. **Preview**: `npm run preview` funciona correctamente

---

## 🔗 Skills Relacionados

El documento menciona integración con otras habilidades:
- **xhtml-author** - Estructura HTML
- **css-author** - Estilos scoped y globales
- **javascript-author** - Islas interactivas
- **deployment** - Configuración de despliegue
- **performance** - Optimización Core Web Vitals

---

## 📌 Notas Adicionales

### View Transitions
Astro soporta transiciones suaves entre páginas mediante la API de View Transitions del navegador, permitiendo animaciones personalizadas y persistencia de elementos entre navegaciones.

### Web Components
Astro tiene soporte nativo para Web Components, permitiendo integrar custom elements sin necesidad de hidratación adicional.

### Integraciones con Frameworks UI
Astro es framework-agnóstico y permite usar componentes de:
- React
- Preact
- Svelte
- Vue
- Solid
- Lit

Cada uno con su propia directiva de hidratación según corresponda.
