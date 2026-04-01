# Índice de contenido

1. Introducción
2. Qué hace AI-Video-Transcriber
3. Qué lo hace diferente
4. Plataforma y Despliegue
5. Requisitos y Recursos
6. Conclusión

---

## 1. Introducción

`AI-Video-Transcriber` es una herramienta impulsada por IA para transcribir y resumir videos de múltiples plataformas (YouTube, TikTok, Bilibili, y 30+). Utiliza tecnología de reconocimiento de voz de última generación y modelos LLM para generar transcripciones optimizadas y resúmenes en múltiples idiomas.

## 2. Qué hace AI-Video-Transcriber

- Descarga videos de 30+ plataformas (YouTube, TikTok, Bilibili, etc.)
- Transcribe audio de video a texto con Faster-Whisper (reconocimiento de voz preciso).
- Optimiza automáticamente transcripciones: corrección de errores, completación de oraciones, párrafos inteligentes.
- Genera resúmenes inteligentes con IA (OpenAI GPT-4o).
- Traduce transcripciones cuando el idioma del resumen difiere del idioma original.
- Interfaz web móvil-friendly con progreso en tiempo real.
- Descarga de archivos (Markdown) con transcripción, traducción y resumen.

## 3. Qué lo hace diferente

- **Multi-plataforma**: Soporta YouTube, TikTok, Bilibili y 30+ más (no solo YouTube).
- **Pipeline de optimización de IA**: No solo transcribe, sino que corrige y mejora el texto automáticamente.
- **Traducciones condicionales**: Detecta idioma original y traduce solo si es necesario.
- **Modo producción para videos largos**: Mantiene conexión SSE estable para procesos de 30-60+ minutos.
- **OpenAI-compatible**: Soporta custom gateways + OpenRouter (múltiples modelos).
- **Interfaz simple y responsive**: Fácil de usar tanto en desktop como mobile.

## 4. Plataforma y Despliegue

### Opciones de despliegue:

**1. Local (Desarrollo)**
- Python en máquina local con `python3 start.py`
- Accesible en `http://localhost:8000`

**2. Docker Compose (Recomendado para producción)**
- `docker-compose up -d` (fácil setup)
- Auto-construye imagen Docker
- Configurable via variables de entorno

**3. Docker directo**
- Build manual: `docker build -t ai-video-transcriber .`
- Run con: `docker run -p 8000:8000 -e OPENAI_API_KEY="..." ai-video-transcriber`

**4. Máquina dedicada/Cloud**
- Linux/macOS con Python 3.8+
- Soporta despliegue en cualquier VPS (DigitalOcean, AWS EC2, Linode, etc.)
- Recomendación: modo producción con `--prod` para estabilidad

## 5. Requisitos y Recursos

### Requisitos previos:

- **Python**: 3.8+
- **FFmpeg**: Instalado en el sistema
- **OpenAI API Key**: Opcional (para resúmenes/traducciones con IA)

### Dependencias Python principales:
- FastAPI >= 0.110.0
- Uvicorn = 0.27.0+
- yt-dlp >= 2024.12.13 (descarga videos)
- faster-whisper >= 1.1.0 (transcripción)
- torch >= 2.0.0 (modelos de ML)
- openai >= 1.51.0 (API)

### Recursos recomendados:

| Elemento | Requisito | Notas |
|----------|-----------|-------|
| **CPU** | 2 cores mínimo | 4+ recomendado para procesamiento rápido |
| **RAM** | 4 GB mínimo | 8+ GB si procesa múltiples videos simultáneamente |
| **GPU** | Opcional (NVIDIA) | CUDA acelera Faster-Whisper 3-5x |
| **Almacenamiento** | 20+ GB | Depende del número y duración de videos |
| **Ancho de banda** | 10+ Mbps | Para descargar videos sin interrupciones |
| **Docker** | 2-3 GB | Tamaño de imagen aproximado |

### Consumo de API:

- **OpenAI**: Cada transcripción optimizada + resumen consume tokens (GPT-4o/3.5-turbo).
- **Estimado**: Video 1 hora ≈ 100K-200K tokens dependiendo del modelo.

## 6. Conclusión

`AI-Video-Transcriber` es una solución integral para transcripción y resumen de videos en múltiples plataformas. Su fortaleza está en la integración de IA para mejorar calidad de transcripción, soporte multi-plataforma y despliegue flexible (local, Docker, cloud). Ideal para investigadores, creadores de contenido y empresas que necesitan automatizar la transcripción de videos a escala.
