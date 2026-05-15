# Usos de IA en EINA · UNIZAR

Repositorio colaborativo de buenas prácticas docentes con inteligencia artificial en educación superior.

## Stack

| Capa | Tecnología |
|------|-----------|
| Contenido | Markdown + YAML frontmatter |
| Sitio web | [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) |
| CMS (panel editorial) | [Decap CMS](https://decapcms.org/) |
| Autenticación | Netlify Identity (login con Google) |
| Hosting + CI/CD | [Netlify](https://netlify.com) |

## Puesta en marcha

### 1. Clonar y subir a GitHub

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/TU_USUARIO/usos-ia-EINA-UNIZAR.git
git push -u origin main
```

### 2. Conectar con Netlify

1. Entra en [netlify.com](https://netlify.com) → **Add new site → Import from Git**
2. Selecciona el repositorio
3. El `netlify.toml` ya configura el build automáticamente
4. El sitio se publicará en `https://TU-SITIO.netlify.app`

### 3. Activar Netlify Identity

1. En Netlify → **Site settings → Identity → Enable Identity**
2. En **Registration**: cambia a **Invite only** (solo quien tú invites puede registrarse)
3. En **External providers**: activa **Google**
4. En **Git Gateway**: activa **Enable Git Gateway** (necesario para que Decap CMS pueda escribir en el repo)

### 4. Configurar el flujo de Pull Requests (revisión editorial)

El `admin/config.yml` ya tiene `publish_mode: editorial_workflow`.  
Esto significa que cada envío de un profesor crea un **Pull Request** en GitHub que tú debes aprobar antes de que se publique.

### 5. Invitar a los profesores

1. Netlify → **Identity → Invite users**
2. Introduce los emails `@unizar.es`
3. Los profesores recibirán un enlace, harán login con Google y podrán acceder al panel en `/admin/`

## Estructura de ficheros

```
usos-ia-EINA-UNIZAR/
├── mkdocs.yml              # Configuración del sitio
├── netlify.toml            # Configuración de Netlify
├── requirements.txt        # Dependencias Python
├── admin/
│   ├── index.html          # Panel Decap CMS
│   └── config.yml          # Campos del formulario
└── docs/
    ├── index.md            # Portada
    ├── etiquetas.md        # Índice de etiquetas (auto)
    ├── contribuir.md       # Instrucciones para profes
    ├── acerca-de.md        # Info del proyecto
    ├── assets/
    │   ├── extra.css       # Estilos personalizados
    │   └── logo.png        # ← Añade tu logo aquí
    └── practicas/
        ├── index.md        # Catálogo
        └── *.md            # Una práctica por fichero
```

## Desarrollo local

```bash
pip install -r requirements.txt
mkdocs serve
# → http://localhost:8000
```

## Añadir una práctica manualmente

Crea un fichero en `docs/practicas/nombre-descriptivo.md` con este frontmatter:

```yaml
---
title: "Título de la práctica"
autor: "Nombre del autor"
area: Ingeniería
tipo_practica: Metodología activa
nivel: Grado (3º-4º)
tamano_grupo: Mediano (20-50 estudiantes)
herramienta_ia: ChatGPT (GPT-4)
fecha: 2024-03-01
tags:
  - chatgpt
  - evaluacion
---
```

## Licencia

[CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/deed.es)
