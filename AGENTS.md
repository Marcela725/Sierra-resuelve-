# Sierra Resuelve

Plataforma para propietarios de las sierras de Córdoba que no pueden vender
por el circuito inmobiliario tradicional (lotes sin subdividir, escrituras
compartidas en familia, tasaciones muy bajas, sin crédito hipotecario).

## Estructura
- `index.html` — toda la página (landing, formulario de publicación, listado, chat).
- `api/chat.js` — función serverless de Vercel. Es el puente seguro hacia la IA:
  guarda la clave secreta y nunca la expone al navegador.

## Cómo funciona el chat
El navegador llama a `/api/chat` (nunca directo a Anthropic). Esa función
usa la variable de entorno `ANTHROPIC_API_KEY` para autenticarse.

## Variables de entorno necesarias
- `ANTHROPIC_API_KEY` — se configura en Vercel (Project Settings → Environment
  Variables), nunca se escribe en el código.

## Estado actual / próximos pasos
- Las propiedades publicadas se guardan en el navegador de cada visitante
  (localStorage), así que cada persona ve solo lo que ella misma publicó.
- Mejora pendiente: sumar una base de datos externa compartida (por ejemplo
  Supabase o Vercel Postgres) para que todas las personas vean el mismo
  listado de propiedades.
- No hay fotos por decisión del proyecto: se prioriza la información real
  de la situación de cada propiedad.
