# Índice de contenido

1. Introducción
2. Qué hace Open Agent Builder
3. Qué lo hace diferente
4. Plataforma y Despliegue
5. Requisitos y Recursos
6. Conclusión

---

## 1. Introducción

`Open Agent Builder` es un constructor visual sin código para crear pipelines de agentes IA impulsados por Firecrawl. Permite diseñar flujos de trabajo complejos con interfaz drag-and-drop, ejecutarlos en tiempo real con actualizaciones streaming y orquestar tareas de IA/web scraping automatizadas.

## 2. Qué hace Open Agent Builder

- Constructor visual de flujos de trabajo con 8 tipos de nodos (Start, Agent, MCP Tools, Transform, If/Else, While Loop, User Approval, End).
- Scraping web nativo con Firecrawl para extraer datos preparados para LLM.
- Ejecución de workflows con orquestación LangGraph + state management.
- Streaming en tiempo real de resultados.
- Autenticación multiusuario (Clerk).
- Base de datos persistente (Convex) para almacenar workflows y ejecuciones.
- Soporte MCP (Model Context Protocol) para integración de herramientas extensibles.
- Integración con múltiples LLM: Anthropic Claude, OpenAI GPT-5, Groq.
- Plantillas prebuilds: web scraper simple, web search, price tracker, content research, data extractor, etc.
- Ejecución sandboxeada de código (E2B Code Interpreter).
- Aprobaciones humanas en flujos sensibles.
- Endpoints API para ejecución programática.

## 3. Qué lo hace diferente

- **Visual + Full-Stack**: No solo UI visual, sino full-stack con backend real (Convex, LangGraph, Firecrawl).
- **No-code para no-developers**: Drag-and-drop asequible para usuarios no-técnicos.
- **MCP Protocol**: Soporte nativo para MCP, permitiendo extensibilidad con herramientas custom.
- **Firecrawl integrado**: Web scraping de primera clase, no solo llamadas a HTTP básicas.
- **LangGraph para workflows**: Orquestación robusta con state management, conditional routing.
- **Multi-LLM**: Soporta múltiples proveedores (Anthropic, OpenAI, Groq) con MCP.
- **Enterprise-ready**: Autenticación (Clerk), base de datos (Convex), seguridad.
- **Plantillas listas para usar**: Workflows prebuilds que funcionan inmediatamente.
- **Humano en el loop**: Aprobaciones manuales para workflows sensibles.

## 4. Plataforma y Despliegue

### Opciones de despliegue:

**1. Stack completo (Recomendado)**
- **Frontend**: Next.js 16 (App Router) en Vercel
- **Backend**: API routes de Next.js + LangGraph
- **Base de datos**: Convex (managed)
- **Autenticación**: Clerk (managed)
- **Scraping**: Firecrawl API (managed)

**2. Local (Desarrollo)**
- Next.js dev server en localhost:3000+
- Convex dev server local
- Acceso a Convex dashboard

**3. Vercel (Producción)**
- Deploy automático desde GitHub
- Edge functions para performance
- Escalado automático

**4. Auto-hospedado (Avanzado)**
- Posibilidad de que usuarios desplieguen LangGraph self-hosted
- Convex puede hospedarse on-prem (Enterprise)

## 5. Requisitos y Recursos

### Requisitos previos:

- **Node.js**: 18+
- **Firecrawl API key**: OBLIGATORIO (web scraping core)
- **Convex account**: Para base de datos y persistencia
- **Clerk account**: Para autenticación
- **LLM API keys**: Anthropic / OpenAI / Groq (agregable en UI o `.env.local`)

### Dependencias principales (package.json):

- **Next.js**: 16 (canary)
- **React Flow**: Workflow visual builder
- **Convex**: Base de datos reactiva
- **Clerk**: Autenticación
- **LangGraph**: Orquestación de workflows
- **Anthropic SDK**: IA (MCP support)
- **OpenAI SDK**: IA (GPT-5)
- **Groq SDK**: IA rápida
- **E2B**: Code interpreter sandboxeado
- **Tailwind CSS**: Estilos
- **TypeScript**: Tipado

### Recursos recomendados:

| Elemento | Requisito | Notas |
|----------|-----------|-------|
| **CPU** | 2+ cores | Para dev local; Vercel/cloud escala automático |
| **RAM** | 4 GB mínimo | 8+ GB recomendado para Convex dev + Next.js |
| **Almacenamiento** | 1-2 GB | Deps de node_modules + datos de Convex |
| **Ancho de banda** | 5+ Mbps | Para API calls y web scraping |
| **Node.js version** | 18+ | 20+ recomendado |

### Costos (cloud):

- **Convex**: Gratuito hasta 50 ejecuciones/mes (escalable por pago)
- **Clerk**: Gratuito hasta 10K MAU (usuarios activos mensuales)
- **Firecrawl**: Pagado por requests (free tier disponible)
- **Vercel**: Hosting gratuito con plan pro opcional
- **LLM APIs**: OpenAI/Anthropic/Groq pagan por uso

### Componentes de infraestructura:

```
┌─ Vercel (Frontend + API routes de Next.js)
├─ Convex (Servidor real-time database)
├─ Clerk (Auth + JWT)
├─ Firecrawl (Web scraping API)
├─ LangGraph (Workflow orchestration)
├─ LLM Providers (Anthropic/OpenAI/Groq)
└─ E2B (Sandboxed execution)
```

## 6. Conclusión

`Open Agent Builder` es una plataforma empresarial de construcción de workflows IA orientada a no-developers y developers que quieren rapid prototyping. Su diferencial es la integración completa con Firecrawl + LangGraph + multi-LLM en un UI visual. Ideal para automatización web, investigación IA, extracción de datos y pipelines de agentes. Requiere cuentas en múltiples servicios (Convex, Clerk, Firecrawl, LLM) pero ofrece stack totalmente manejado sin código de infraestructura.

---

## ANEXO: Firecrawl

### ¿Qué es Firecrawl?

**Firecrawl** es una API REST de scraping web especializada que convierte sitios web interos en datos estructurados **optimizados para modelos de lenguaje (LLM)**. No es un scraper genérico, sino una herramienta diseñada específicamente para extraer datos listos para procesar por IA.

**URL oficial**: https://firecrawl.dev

### Utilidad de Firecrawl

Firecrawl resuelve problemas comunes del web scraping tradicional:

1. **Conversión a Markdown/JSON limpio**: Transforma HTML complejo en Markdown legible o JSON estructurado.
2. **Extracción LLM-ready**: Los datos se formatean para que los LLM los entiendan directamente (sin ruido HTML).
3. **Búsqueda en la web**: API de búsqueda integrada que devuelve resultados scrapeados preparados.
4. **Crawling completo**: Recorre múltiples páginas de un sitio automáticamente.
5. **Mapeo de sitios**: Genera mapas de estructura de sitios web.
6. **Batch scraping**: Procesa múltiples URLs simultáneamente.
7. **Extracción JSON con esquemas**: Define qué datos extraer usando JSON Schema + prompts de extracción.
8. **Manejo de JavaScript**: Ejecuta JavaScript antes de extraer (importante para SPAs).

### Cómo se integra con Open Agent Builder

Firecrawl es el **núcleo de la funcionalidad de web scraping** en Open Agent Builder:

#### 1. **Node de Firecrawl en workflows**
En la interfaz visual, el usuario puede crear nodos Firecrawl que ejecutan acciones:
- `scrape`: Extrae contenido de una URL individual
- `search`: Busca en la web y devuelve resultados scrapeados
- `crawl`: Recorre un dominio completo
- `map`: Genera mapa de estructura del sitio
- `batch_scrape`: Procesa múltiples URLs en paralelo

#### 2. **API Backend**
El archivo `app/api/execute-firecrawl/route.ts` implementa un endpoint que:
- Recibe acciones y parámetros del workflow
- Instancia `FirecrawlApp` con la API key
- Ejecuta la operación solicitada
- Devuelve datos estructurados al workflow

```typescript
// Ejemplo de uso interno
const firecrawl = new FirecrawlApp({ apiKey: process.env.FIRECRAWL_API_KEY });
const result = await firecrawl.scrape(url, {
  formats: ['markdown'], // O JSON con esquema personalizado
});
```

#### 3. **Plantillas prebuilds que usan Firecrawl**
- **Simple Scraper**: Extrae contenido de una página
- **Web Search**: Busca información y la scrape automáticamente
- **Price Tracker**: Monitorea precios extrayendo datos de e-commerce
- **Content Research**: Recopila datos de múltiples fuentes
- **Data Extractor**: Extrae datos según esquema JSON definido

#### 4. **Flujo de datos**
```
Usuario define URL/query en workflow visual
           ↓
Firecrawl nodo se ejecuta (POST a /api/execute-firecrawl)
           ↓
API responde con datos scrapeados (Markdown/JSON)
           ↓
Datos pasan a nodo Agent/LLM siguiente en pipeline
           ↓
LLM procesa datos y genera respuesta/acción
```

### Características técnicas de Firecrawl en Open Agent Builder

| Característica | Descripción |
|----------------|-------------|
| **JSON Schema mode** | Define estructura personalizada para extracción |
| **Extract Prompts** | Instrucciones en lenguaje natural para qué extraer |
| **Markdown output** | Devuelve HTML como Markdown limpio |
| **Límites** | `limit` configurable (ej: 10 páginas para crawl) |
| **Batch operations** | Procesa múltiples URLs sin bloquear |
| **Error handling** | Gestiona URLs inaccesibles, timeouts, etc. |

### Requisitos para usar Firecrawl

- **API Key**: Obligatorio (generar en https://firecrawl.dev/app)
- **Configuración**: Asignar a `FIRECRAWL_API_KEY` en `.env.local`
- **Cuota**: Según plan de Firecrawl (free/pro)

### Ejemplo de flujo en Open Agent Builder

```
[Start] → [Firecrawl: Scrape URL] → [Agent: Procesar datos] → [End]
         ↓
    Extrae contenido de URL
    Convierte a Markdown limpio
    Devuelve al nodo Agent
         ↓
    Agent analiza/resume/clasifica
    Devuelve resultado final
```

### Ventaja diferencial

Mientras que herramientas genéricas de scraping devuelven HTML bruto o datos sin estructura, **Firecrawl integrado en Open Agent Builder permite workflows visuales que combinan scraping + IA sin escribir código**, haciendo posible que usuarios no-técnicos construyan pipelines de extracción y análisis de datos complejos.
