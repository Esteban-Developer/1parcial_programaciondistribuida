# Inferno Colombia - E-commerce de Moda

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=for-the-badge&logo=fastapi&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-ORM-red?style=for-the-badge)
![Jinja2](https://img.shields.io/badge/Jinja2-Templates-black?style=for-the-badge)

**Plataforma e-commerce para venta de prendas de vestir**

Una solución completa de tienda online desarrollada para **Inferno Colombia** 🇨🇴 — migrada a **Python + FastAPI** con catálogo, carrito, checkout, autenticación y API REST de productos.

---

## Tabla de contenidos

- [Documento de arquitectura](#-documento-de-arquitectura)
- [Diagrama de componentes](#-diagrama-de-componentes)
- [Descripción](#-descripción)
- [Características](#-características)
- [Tecnologías](#-tecnologías)
- [Instalación y ejecución](#-instalación-y-ejecución)
- [API REST](#-api-rest)
- [Autor](#-autor)
- [Licencia](#-licencia)

---

##  Documento de arquitectura

- **Backend:** Python 3.10+ con FastAPI (ASGI con Uvicorn).
- **Base de datos:** MySQL (ej. XAMPP), base de datos `threaderz_store`. Conexión vía **SQLAlchemy** + **PyMySQL**; configuración por variables de entorno (`.env`): `DB_HOST`, `DB_PORT`, `DB_USER`, `DB_PASSWORD`, `DB_NAME`.
- **Sesión:** Starlette `SessionMiddleware` (cookie); identificador de usuario: `customer_email`.
- **Capas:** Rutas (web + API) → lógica en handlers y `utils` → acceso a datos con ORM (`models.py`) → presentación con plantillas Jinja2 y estáticos (CSS/JS/img/fuentes) desde la raíz del repo.
- **Componentes principales:** `main.py` (app, rutas web, estáticos), `api_products.py` (API `/productos`), `db.py` (engine, sesiones), `models.py` (Category, Product, Customer, Cart, Order, Slider), `settings.py`, `utils.py`, `templates/`.

---

##  Diagrama de componentes

![Arquitectura del sistema](arquitectura.png)

##  Descripción

Proyecto de **e-commerce** para Inferno Colombia: catálogo de productos por categorías (Hombres, Mujeres, Niños), carrito de compras, checkout, registro e inicio de sesión, cuenta de usuario (pedidos y datos), página de contacto y panel de administración para insertar productos. Incluye una **API REST** para el catálogo (`POST/GET /productos`, `GET /productos/{id}`). La aplicación está implementada en **Python con FastAPI** y utiliza la misma base de datos MySQL que la versión original en PHP.

---

##  Características

- Inicio con slider y productos destacados (hombres/mujeres).
- Tienda con filtros por categoría y paginación.
- Detalle de producto con relacionados y agregar al carrito (talla y cantidad).
- Carrito y eliminación de ítems.
- Checkout y creación de pedido (vacía el carrito y registra en `orders`).
- Login, registro (con imagen de perfil) y logout con sesión por cookie.
- Cuenta: mis pedidos y mis datos.
- Contacto (formulario; envío opcional por SMTP).
- Admin: alta de productos (imágenes, categorías, precio, descripción).
- API REST: `POST /productos`, `GET /productos`, `GET /productos/{id}` (datos desde MySQL).
- Búsqueda desde el header (redirige al primer producto que coincida).
- Reutilización de CSS, JS, imágenes y fuentes del proyecto original.

---

##  Tecnologías

| Área        | Tecnología        |
|------------|-------------------|
| Lenguaje   | Python 3.10+      |
| Framework  | FastAPI           |
| Servidor   | Uvicorn (ASGI)    |
| ORM / BD   | SQLAlchemy + PyMySQL |
| Base de datos | MySQL (threaderz_store) |
| Plantillas | Jinja2            |
| Sesión     | Starlette SessionMiddleware |
| Config     | python-dotenv (`.env`) |

---

---

##  Instalación y ejecución

1. Clonar el repositorio y tener **MySQL** (ej. XAMPP) con la BD creada e importada desde `store.sql`.
2. En `fastapi_app/` crear `.env` (copiar `.env.example`) y configurar `DB_*` y opcionalmente `APP_SECRET_KEY`, `SMTP_*`.
3. Crear entorno virtual, instalar dependencias y ejecutar:


cd fastapi_app


python -m venv .venv


.venv\Scripts\activate    # Windows


pip install -r requirements.txt


pip install itsdangerous


uvicorn app.main:app --reload --host 127.0.0.1 --port 8000



## Abrir en el navegador: http://127.0.0.1:8000/.


 API REST
Método	Ruta	Descripción


POST	/productos	Crear producto (JSON)


GET	/productos	Listar todos los productos


GET	/productos/{id}	Detalle de un producto


Documentación interactiva: http://127.0.0.1:8000/docs.

## 👤 Autor

Esteban Murillo — Proyecto Inferno Colombia
Miguel Villamil
