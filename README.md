# 💧 AguaYa (EcoSantaMarta) — Plataforma de Reporte y Monitoreo Hídrico

Aplicación web **Full-Stack** diseñada para el reporte ciudadano, geolocalización y análisis estadístico de problemáticas en el suministro de agua en Santa Marta, Colombia.

---

## 🚀 Características principales
- **Mapa interactivo y geocodificación:** Registro y visualización geográfica de reportes mediante integración con Nominatim (OpenStreetMap).
- **Gestión de incidencias (CRUD):** Creación, filtrado por categoría (ej. *Sin agua*, fugas, baja presión), actualización de estado y eliminación de reportes.
- **Panel de estadísticas:** Visualización de métricas agregadas y gráficas en tiempo real sobre las zonas y tipos de fallas más frecuentes.
- **Arquitectura Full-Stack:** Frontend reactivo en Vue.js conectado a una API REST propia en Node.js/Express con persistencia en MySQL.

---

## 🛠️ Stack Tecnológico
- **Frontend:** Vue 3, Vite, Pinia (`stores`), JavaScript (ES6+), HTML5, CSS3.
- **Backend:** Node.js, Express, CORS, Dotenv.
- **Base de datos:** MySQL.
- **Servicios externos:** Nominatim API (Geocodificación).

---

## 📂 Estructura del proyecto

    aguaya/
    ├── aguaya-backend/          # API REST (Node.js + Express + MySQL)
    │   ├── server.js
    │   ├── schema.sql
    │   ├── .env.example
    │   └── package.json
    └── aguaya-frontend/         # Aplicación cliente (Vue 3 + Vite + Pinia)
        └── src/
            ├── stores/
            │   └── waterReports.js
            └── views/
                ├── MapaView.vue
                └── EstadisticasView.vue

---

## ⚙️ Instalación y ejecución en local

### 1. Clonar el repositorio

    git clone [https://github.com/Frixmas-dot/EcoSantaMarta_v2.git](https://github.com/Frixmas-dot/EcoSantaMarta_v2.git)
    cd EcoSantaMarta_v2

### 2. Configurar la base de datos (MySQL)
Importa el esquema inicial desde la terminal o ejecuta el contenido de `schema.sql` en MySQL Workbench:

    mysql -u root -p < aguaya-backend/schema.sql

### 3. Configurar y arrancar el Backend

    cd aguaya-backend
    npm install
    cp .env.example .env

Edita el archivo `.env` con tus credenciales locales de MySQL:

    DB_HOST=localhost
    DB_PORT=3306
    DB_USER=root
    DB_PASSWORD=tu_password_aqui
    DB_NAME=aguaya
    PORT=3001

Inicia el servidor:

    node server.js

La API quedará disponible en `http://localhost:3001`.

### 4. Configurar y arrancar el Frontend
En una nueva terminal:

    cd aguaya-frontend
    npm install
    npm run dev

Abre `http://localhost:5173` en tu navegador.

---

## 🔌 Endpoints de la API

| Método | Ruta | Descripción |
| :--- | :--- | :--- |
| `GET` | `/api/reportes` | Obtener todos los reportes (admite filtro `?tipo=Sin agua`) |
| `GET` | `/api/reportes/:id` | Consultar un reporte específico |
| `POST` | `/api/reportes` | Crear un nuevo reporte con geocodificación |
| `PATCH` | `/api/reportes/:id/estado` | Actualizar el estado de un reporte |
| `DELETE` | `/api/reportes/:id` | Eliminar un reporte |
| `GET` | `/api/estadisticas` | Obtener datos agregados para gráficas |
| `GET` | `/api/health` | Verificar el estado de la API |

---

## 👨‍💻 Autor
**Friedrick Riojas Gutiérrez**
- GitHub: [@Frixmas-dot](https://github.com/Frixmas-dot)
- Correo: riojas0804@gmail.com
