# Deploy en Render

Este proyecto expone una app FastAPI en `main_chatwoot.py` con el objeto `app`.

## Opcion recomendada: Blueprint

1. Sube esta carpeta a un repositorio de GitHub.
2. En Render, crea un nuevo Blueprint y selecciona el repo.
3. Render leera `render.yaml`.
4. Completa las variables marcadas como secretas en el dashboard.

## Opcion manual: Web Service

Si prefieres crear un Web Service manualmente, usa:

- Runtime: `Python`
- Root Directory: `LangChain-AgenteIA-MultiTool-Pinecone` si el repo contiene varias carpetas de proyectos
- Build Command: `pip install --upgrade pip && pip install -r requirements.txt`
- Start Command: `uvicorn app:app --host 0.0.0.0 --port $PORT`
- Health Check Path: `/health`

El archivo `app.py` exporta la misma app FastAPI desde `main_chatwoot.py`.

## Variables de entorno

No subas el archivo `.env` al repositorio. En Render debes crear estas variables:

- `OPENAI_API_KEY`
- `DB_USER`
- `DB_PASSWORD`
- `DB_HOST`
- `DB_PORT`
- `DB_NAME`
- `PINECONE_API_KEY`
- `PINECONE_INDEX_NAME`
- `TAVILY_API_KEY`
- `CHATWOOT_BASE_URL`
- `CHATWOOT_ACCOUNT_ID`
- `CHATWOOT_API_ACCESS_TOKEN`
- `CHATWOOT_BOT_LABEL`
- `AGENT_TIMEZONE`

Despues del deploy, prueba:

- `https://TU-SERVICIO.onrender.com/health`
- `https://TU-SERVICIO.onrender.com/docs`

El webhook de Chatwoot debe apuntar a:

`https://TU-SERVICIO.onrender.com/webhook`
