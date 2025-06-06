# 🤖 n8n CV Automation Project

Este proyecto implementa una serie de automatizaciones usando [n8n](https://n8n.io/), una herramienta de automatización de flujos de trabajo. El objetivo principal es facilitar el proceso de preselección de hojas de vida y notificación al equipo de reclutamiento.

---

## ¿Qué hace este proyecto?

- **Analiza hojas de vida (PDFs)** y determina si coinciden con ciertos criterios definidos en un prompt.
- **Envía notificaciones** por **correo electrónico** o **Telegram** cuando se actualiza un Google Sheet con información sobre nuevas hojas de vida.
- Utiliza modelos locales vía **Ollama** para análisis de texto, integrados con n8n.

---

## Estructura del repositorio

```
.
├── cv_pdf_examples/ # Hojas de vida de ejemplo (PDF)
├── n8n/            # Volumen persistente local de n8n
├── workflow_nodes/ # Nodos exportados manualmente
├── .gitignore
├── .python-version
├── README.md
├── docker-compose.yml # Entorno con n8n y Ollama
└── pyproject.toml 
```


---

## Instalación y ejecución

### Requisitos

- Docker y Docker Compose
- Git
- Claves de API (para Gmail, Google Drive, Telegram y Google Sheets)

### Pasos

```
# Clona el repositorio
git clone <URL-del-repo>
cd <nombre-del-repo>
```

```
# Levanta el entorno
docker-compose up -d
```

Esto desplegará:

n8n en http://localhost:5678

Ollama en http://localhost:11434 

## Workflows disponibles

| Archivo JSON                        | Descripción                                                          |
|------------------------------------|----------------------------------------------------------------------|
| `cv_automation.json`               | Automatiza el análisis de CVs usando un modelo de lenguaje.         |
| `notification_workflow_gmail.json` | Notifica por correo cuando se actualiza el Google Sheet.            |
| `notification_workflow_telegram.json` | Notifica por Telegram cuando se actualiza el Google Sheet.                      |

### Para usarlos:

1. Importa los archivos `.json` desde la interfaz de n8n.
2. Configura las credenciales necesarias desde la sección **Credentials** en n8n.
3. Asegúrate de que las integraciones (como Gmail o Telegram) están activas.

---

## Credenciales

- Las credenciales se configuran directamente en la interfaz de n8n.
- Ver documento de soporte en [docs/LLMs_HireGen.pdf](docs/LLMs_HireGen.pdf)

---

## Notas

- Este proyecto está diseñado para ejecutarse **localmente**.
- Puedes cambiar el prompt de análisis según el perfil de vacante deseado.
- Las notificaciones por correo y Telegram son opcionales y personalizables.