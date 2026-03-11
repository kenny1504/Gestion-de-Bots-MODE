# Gestion de Bot Whatsapp

Panel web ligero (archivo HTML único) para **supervisar conversaciones de WhatsApp** y cambiar el modo de atención entre **BOT** y **HUMAN**.

## ¿Para qué sirve?

Este proyecto permite:
- Ver el estado actual de conversaciones (modo, lock humano, actividad, notas).
- Filtrar por teléfono/`wa_id` y por tipo de modo (`BOT` o `HUMAN`).
- Cambiar rápidamente el modo de una conversación desde la interfaz.
- Refrescar automáticamente los datos cada 5 segundos.

## Uso rápido

1. Abrí `Test.html` en el navegador.
2. En **Webhook base URL**, ingresá tu base (ejemplo: `https://tu-dominio/webhook`).
3. El panel consultará datos y te permitirá alternar el modo BOT/HUMAN por conversación.

## API esperada

El frontend consume estos endpoints:

- `GET {BASE_URL}/wa-contact-state`
  - Respuesta esperada: objeto con `data` (array de conversaciones).
- `POST {BASE_URL}/wa-contact-state/mode`
  - Body JSON:
    ```json
    {
      "phone": "50583699238",
      "mode": "BOT"
    }
    ```

Campos comunes por conversación (según el render actual): `phone`, `wa_id`, `mode`, `human_lock_until`, `last_inbound_at`, `last_bot_at`, `last_human_at`, `first_seen_at`, `notes`.
