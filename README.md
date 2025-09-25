# TAREA3_PCD: Users API

Este proyecto implementa una API REST para la gestión de usuarios, construida con **FastAPI** (como framework), **Pydantic** (para validación de datos) y **SQLAlchemy** (para ORM y persistencia de datos). La seguridad de las rutas principales se implementa mediante una clave de API.

---

## 🛠️ Instalación y Configuración

El proyecto utiliza **`uv`** como gestor de paquetes para un manejo de dependencias rápido y eficiente, y requiere **Python 3.13**.

### 1. Requisitos

Asegúrate de tener la versión de Python especificada y la herramienta `uv` instalada.

### 2. Crear Entorno Virtual e Instalar Dependencias

Usa el archivo `uv.lock` proporcionado para instalar todas las dependencias en un entorno virtual:

```bash
# Sincroniza las dependencias e instala el entorno virtual
uv sync

# Activa el entorno virtual (necesario antes de correr la app)
source .venv/bin/activate  # Para Linux/macOS
# .venv\Scripts\activate   # Para Windows (ejemplo)
```

## 🔑 Clave de API (.env file)
La aplicación requiere una clave de API (API_KEY) para la autenticación de las rutas seguras.

1. Ejemplo de Configuración (.env.example)
El archivo base para la configuración de la clave es:

API_KEY=<YOUR_API_KEY_HERE>
2. Definir la Clave de API (.env)
Crea un archivo llamado .env en la raíz del proyecto. El valor de tu clave se cargará en la aplicación:
```bash
# Contenido de .env (Ejemplo, usa tu propia clave)
API_KEY=tu_api_key 
```
▶️ Ejecución de la Aplicación
Para iniciar el servidor FastAPI, ejecuta el siguiente comando con el entorno virtual activado:

```bash
uv run fastapi dev main.py
```

## 🗺️ Endpoints de la API
| Método | Ruta | Descripción | Seguridad |
| :--- | :--- | :--- | :--- |
| `GET` | `/` | Retorna un mensaje de estado. | No |
| `POST` | `/api/va/users/` | Crea un nuevo usuario. Incluye verificación de email duplicado. | API Key |
| `GET` | `/api/v1/users/{user_id}` | Busca y retorna un usuario por su ID. | API Key |
| `PUT` | `/api/v1/users/{user_id}` | Actualiza completamente los datos de un usuario existente. | API Key |
| `DELETE` | `/api/v1/users/{user_id}` | Elimina un usuario por su ID. | API Key |

## 📝 Esquema del Modelo User (Pydantic)
El modelo de Pydantic define la estructura y validación de los datos que se esperan para un usuario:

| Campo | Tipo | Requerido | Validación/Comentarios |
| :--- | :--- | :--- | :--- |
| `user_name` | `str` | Sí | Mínima longitud de 1. |
| `user_email` | `EmailStr` | Sí | Debe ser un formato de correo electrónico válido. |
| `age` | `int \| None` | No | Opcional. Debe ser un entero. |
| `recommendations` | `list[str]` | No | Por defecto, una lista vacía `[]`. Se almacena como JSON en la DB. |
| `zip` | `str \| None` | No | Opcional. Longitud mínima 5 y máxima 9. |
