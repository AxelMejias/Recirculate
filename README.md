# 👕 Recirculate

Un sistema web para gestionar productos de moda circular (ropa de segunda mano). Básicamente es un e-commerce con panel de admin para cargar productos, ver ventas, controlar stock y todo eso.

## ¿Qué hace?

- **Para clientes**: Ver catálogo, buscar productos, filtrar por categoría/género, agregar al carrito, comprar
- **Para admins**: Cargar productos con fotos, gestionar stock por talle, registrar ventas, llevar control de gastos
- **Autenticación**: Login/registro con JWT, permisos de admin

# Recirculate — tienda + admin (versión local / deploy)

Bienvenido. Este repo contiene la tienda (frontend) y la API (backend) de Recirculate. Lo armamos para probar funcionalidades reales: catálogo, carrito, panel de administración y gestión de stock por talle.

No es una super app, pero funciona para demostrar cómo montar una pequeña tienda que usa PostgreSQL y Cloudinary.

Qué vas a encontrar aquí:

- Frontend: `RecirculateLoe/` — archivos estáticos (HTML/CSS/JS)
- Backend: `api/` — Express + PostgreSQL (endpoints REST)

Si preferís saltarte la lectura larga: head to `RecirculateLoe/home/home.html` para ver la tienda.

---

## Cómo probar en tu máquina (fast-track)

1. Cloná el repo

```bash
git clone https://github.com/AxelMejias/Recirculate.git
cd Recirculate
```

2. Levantá la API (desde la carpeta `api`)

```bash
cd api
npm install
npm start
```

Por defecto el servidor arranca en `http://localhost:3001`.

3. Abrí la tienda en tu navegador:

```
file://<ruta-al-repo>/RecirculateLoe/home/home.html
```

O si preferís que todo lo sirva el backend (más simple para deploy): visita `http://localhost:3001/RecirculateLoe/home/home.html`.

---

## Variables de entorno (básicas)

Dentro de `api/.env` necesitás al menos:

```env
DATABASE_URL=postgresql://usuario:contraseña@localhost:5432/recirculate
JWT_SECRET=algún-secreto
CLOUDINARY_CLOUD_NAME=xxx
CLOUDINARY_API_KEY=xxx
CLOUDINARY_API_SECRET=xxx
```

Si no tenés Cloudinary podés comentar la parte de subida o usar imágenes locales.

---

## Credenciales para pruebas

Usá estas si querés explorar el panel de admin rápidamente:

- Email: `admin@recirculate.com`
- Password: `admin123`

---

## Deploy (recomendado: Render)

Si vas a desplegar en Render, lo más sencillo es crear un **Web Service (Node)** apuntando a la carpeta `api` del repo. Configuración mínima:

```
Root Directory: api
Build Command: npm install
Start Command: npm start
```

El `server.js` ya está preparado para servir también los archivos estáticos (la carpeta `RecirculateLoe`).

El backend público queda en `https://<tu-backend>.onrender.com` y la tienda en `https://<tu-backend>.onrender.com/RecirculateLoe/home/home.html`.

---

## Estructura resumida

```
/
├─ api/                # Express + endpoints
├─ RecirculateLoe/     # Frontend público
├─ productos/          # Panel admin (frontend)
└─ index.html          # Dashboard admin
```

---

## Notas rápidas

- La búsqueda es en vivo y las páginas de producto usan `data-stock` para manejar talles.
- Hay un keep-alive en el backend para ayudar a que el servicio no entre en sleep en Render.
- Si algo no anda, mirá los logs del servidor (`npm start`) y chequeá la URL de la API.

---



