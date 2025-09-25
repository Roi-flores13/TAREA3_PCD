# TAREA3_PCD: Users API

Este proyecto implementa una API REST para la gestión de usuarios, construida con **FastAPI** (como framework), **Pydantic** (para validación de datos) y **SQLAlchemy** (para ORM y persistencia de datos). La seguridad de las rutas principales se implementa mediante una clave de API.

---

## 🛠️ Instalación y Configuración

El proyecto utiliza **`uv`** como gestor de paquetes para un manejo de dependencias rápido y eficiente, y requiere **Python 3.13**.

### 1. Requisitos

Asegúrate de tener la versión de Python especificada y la herramienta `uv` instalada.

### 2. Crear Entorno Virtual e Instalar Dependencias

[cite_start]Usa el archivo `uv.lock` [cite: 23] proporcionado para instalar todas las dependencias en un entorno virtual:

```bash
# Sincroniza las dependencias e instala el entorno virtual
uv sync

# Activa el entorno virtual (necesario antes de correr la app)
source .venv/bin/activate  # Para Linux/macOS
# .venv\Scripts\activate   # Para Windows (ejemplo)