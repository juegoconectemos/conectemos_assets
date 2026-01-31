# Conectemos - Activos de imágenes para jsDelivr

Este repositorio contiene imágenes y variantes optimizadas. Puede usarse de dos formas:

1. Servir las imágenes directamente desde tu backend (recomendado si necesitas control).
2. Servir las imágenes desde este repositorio mediante jsDelivr (https://www.jsdelivr.com/), apuntando a la rama `master`.

Estructura recomendada:
- images/                ← fotos originales (ej. `conectemos-01.jpg`)
- images/variants/       ← variantes generadas (ej. `conectemos-01-800.webp`)
- server/                ← backend que sirve las imágenes al frontend
- examples/              ← ejemplos HTML que usan el backend o jsDelivr
- .github/workflows/     ← workflows (opcional, p. ej. generador de variantes)

URLs:
- jsDelivr (si subes imágenes al repo y quieres usarlas desde CDN):
  https://cdn.jsdelivr.net/gh/juegoconectemos/conectemos_assets@master/images/conectemos-01.jpg

Consejos:
- Si tu frontend obtendrá imágenes desde el backend, expón endpoints JSON listando las imágenes (p. ej. `/api/images`) y endpoints para la propia imagen (p. ej. `/images/:name`).
- Usa `Cache-Control` y `ETag` en el backend para mejorar rendimiento.
- Si también quieres CDN, sitúa un CDN (Cloudflare, Fastly) delante de tu backend o usa jsDelivr si las imágenes están en el repo.
- Para versiones inmutables en producción, usa `@<tag>` o el SHA del commit en las URLs jsDelivr.

Automatización:
- Incluye `.github/workflows/image-optimizer.yml` para generar variantes (400/800/1600 jpg + webp) cuando subas imágenes a `images/`. Opcional: el workflow puede commitear automáticamente `images/variants/` o subir artefactos.

Cómo desplegar el backend:
- El backend de ejemplo usa Node/Express y puede desplegarse en Railway, Vercel (serverless), Heroku o un VPS.