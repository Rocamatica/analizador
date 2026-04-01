# Índice de contenido

1. Introducción
2. Qué hace `PHP-React-Framework`
3. Qué lo hace diferente
4. Detalles técnicos clave
5. Conclusión

---

## 1. Introducción

`PHP-React-Framework` es una plantilla (boilerplate) que integra backend en PHP con frontend en React (Vite). Proporciona estructura de aplicación tipo framework para acelerar el desarrollo de SPA con API versionada.

## 2. Qué hace `PHP-React-Framework`

- Un front controller en `public/index.php` que unifica solicitudes.
- Router con rutas de API versionadas bajo `/api/v1` y rutas web.
- Controladores organizados (`app/Controllers/Api`, `app/Controllers/Web`).
- Middleware para CORS, logging y autenticación por API key.
- Soporte de modelos Eloquent y validación básica.
- Inyección dinámica de metadatos SEO para la respuesta inicial del SPA.
- Configuración centralizada (app, database, cors, auth) y uso de `App\Core\Support\Config`.
- Comandos listos: `npm run dev`, `npm run build`, `npm run preview`, `npm run migrate`, `npm run seed`.

## 3. Qué lo hace diferente

- Combina PHP (con patrones de framework: controlador, middleware, DI, exceptions, routing) y React/Gerenciador Vite en un solo repositorio.
- Rutas API versionadas y separadas de la lógica de ruta en archivos de controladores, no en un solo archivo monolítico.
- Middleware pipeline configurable con protección selectiva de endpoints (SEO/settings via `ApiKeyAuthMiddleware`).
- Modo demo automático (sin `API_KEY` no requiere autenticación), facilita arranque rápido para pruebas.
- SPA + backend unificado con inyección SEO dinámica en HTML inicial (beneficia SEO y SSR-like prerender).

## 4. Detalles técnicos clave

- Estructura de carpetas clara: `app`, `routes`, `public`, `config`, `database`.
- API principal: CRUD de `todos`, SEO y configuración SEO-toggle.
- Seguridad opcional por header `x-api-key` si `API_KEY` está establecido.
- Base de datos predeterminada `sqlite` (fácil setup local) con posibilidad de otros drivers.

## 5. Conclusión

`PHP-React-Framework` es un starter kit muy orientado al desarrollo rápido de aplicaciones web modernas donde se quiere tener un backend PHP estructurado y un frontend React en la misma base de código. Su valor diferencial es la integración out-of-box de patterns de backend y SPA React con routing versionado, middleware y SEO.
