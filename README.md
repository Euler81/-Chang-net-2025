# 🚀 **CHANGANET - INSTRUCTIVO COMPLETO PARA HACERLO FUNCIONAR**

Changánet es una plataforma web responsive que conecta a clientes con profesionales de servicios técnicos, con un enfoque en triple impacto: social, económico y ambiental.

## 📋 **TABLA DE CONTENIDOS**

*   [1. Requisitos Previos](#1-requisitos-previos)
*   [2. Estructura del Proyecto](#2-estructura-del-proyecto)
*   [3. Instalación Paso a Paso](#3-instalación-paso-a-paso)
*   [4. Configuración de Variables de Entorno](#4-configuración-de-variables-de-entorno)
*   [5. Creación de la Base de Datos](#5-creación-de-la-base-de-datos)
*   [6. Ejecución del Proyecto](#6-ejecución-del-proyecto)
*   [7. Prueba de Funcionalidades](#7-prueba-de-funcionalidades)
*   [8. Verificación de la Base de Datos](#8-verificación-de-la-base-de-datos)
*   [9. Solución de Problemas Comunes](#9-solución-de-problemas-comunes)
*   [10. Tecnologías Utilizadas](#10-tecnologías-utilizadas)

---

## 🛠️ **1. REQUISITOS PREVIOS**

Antes de empezar, asegúrate de tener instalado en tu computadora:

### **1.1 Instalar Node.js y npm**
1.  Ve a [https://nodejs.org/](https://nodejs.org/)
2.  Descarga la versión **LTS (Long Term Support)**.
3.  Ejecuta el instalador y sigue los pasos.
4.  **Verifica la instalación:**
    ```bash
    node -v
    npm -v
    ```

### **1.2 Instalar PostgreSQL**
1.  Ve a [https://www.postgresql.org/download/](https://www.postgresql.org/download/)
2.  Descarga e instala la versión para tu sistema operativo.
3.  **¡Anota la contraseña del usuario `postgres`!**
4.  **Verifica la instalación:**
    ```bash
    psql -U postgres -W
    ```

### **1.3 Instalar Git**
1.  Ve a [https://git-scm.com/](https://git-scm.com/)
2.  Descarga e instala la versión para tu sistema.
3.  **Verifica la instalación:**
    ```bash
    git --version
    ```

### **1.4 Instalar Visual Studio Code (Opcional pero Recomendado)**
1.  Ve a [https://code.visualstudio.com/](https://code.visualstudio.com/)
2.  Descarga e instala la versión para tu sistema.

### **1.5 Instalar Extensiones de VS Code (Opcional pero Recomendado)**
1.  **Thunder Client:** Para probar APIs.
2.  **Prisma:** Para resaltado de sintaxis en archivos `.prisma`.
3.  **ESLint:** Para mantener un código limpio.
4.  **Prettier:** Para formatear automáticamente el código.

---

## 📁 **2. ESTRUCTURA DEL PROYECTO**

```
changanet/
├── docker-compose.yml
├── package-lock.json
├── package.json
├── prometheus.yml
├── README.md
├── test-google-oauth.js
├── test-integration.js
├── test-jest.js
├── test-metrics-custom.js
├── test-prometheus.js
├── test-sentry-backend.js
├── test-sentry-frontend.js
├── changanet-backend/
│   ├── .env.example
│   ├── .eslintrc.js
│   ├── .gitignore
│   ├── .lintstagedrc.js
│   ├── .prettierrc
│   ├── docker-compose.redis.yml
│   ├── ecosystem.config.js
│   ├── jest.config.js
│   ├── package-lock.json
│   ├── package.json
│   ├── README-cache.md
│   ├── README-production.md
│   ├── README.md
│   ├── test-cloudinary.js
│   ├── test-db.js
│   ├── test-fcm-notifications.js
│   ├── test-fcm-push.js
│   ├── test-fcm-send.js
│   ├── test-firebase-admin.js
│   ├── test-register.js
│   ├── test-sendgrid.js
│   ├── test-socketio.js
│   ├── test-twilio.js
│   ├── docs/
│   │   ├── database-diagram.png
│   │   └── database-optimization-guide.md
│   │   └── swagger.yaml
│   ├── prisma/
│   │   ├── schema.prisma
│   │   ├── docs/
│   │   │   └── database-diagram.png
│   │   └── migrations/
│   │       ├── migration_lock.toml
│   │       ├── 20251008171024_init/
│   │       │   └── migration.sql
│   │       └── 20251010162315_add_google_fields/
│   │           └── migration.sql
│   └── src/
│       ├── server.js
│       ├── config/
│       │   ├── firebaseAdmin.js
│       │   └── passport.js
│       ├── controllers/
│       │   ├── authController.js
│       │   ├── availabilityController.js
│       │   ├── contactController.js
│       │   ├── custodyController.js
│       │   ├── galleryController.js
│       │   ├── healthController.js
│       │   ├── messageController.js
│       │   ├── newsletterController.js
│       │   ├── notificationController.js
│       │   ├── paymentController.js
│       │   ├── profileController.js
│       │   ├── quoteController.js
│       │   ├── rankingController.js
│       │   ├── reviewController.js
│       │   ├── searchController.js
│       │   ├── serviceController.js
│       │   ├── statsController.js
│       │   └── verificationController.js
│       ├── docs/
│       │   └── swagger.yaml
│       ├── middleware/
│       │   ├── authenticate.js
│       │   ├── logging.js
│       │   └── metricsMiddleware.js
│       ├── routes/
│       │   ├── authRoutes.js
│       │   ├── availabilityRoutes.js
│       │   ├── contactRoutes.js
│       │   ├── custodyRoutes.js
│       │   ├── galleryRoutes.js
│       │   ├── messageRoutes.js
│       │   ├── metricsRoutes.js
│       │   ├── newsletterRoutes.js
│       │   ├── notificationRoutes.js
│       │   ├── paymentRoutes.js
│       │   ├── profileRoutes.js
│       │   ├── quoteRoutes.js
│       │   ├── rankingRoutes.js
│       │   ├── reviewRoutes.js
│       │   ├── searchRoutes.js
│       │   ├── serviceRoutes.js
│       │   ├── servicesRoutes.js
│       │   ├── statsRoutes.js
│       │   └── verificationRoutes.js
│       ├── services/
│       │   ├── authService.js
│       │   ├── backupService.js
│       │   ├── cacheService.js
│       │   ├── chatService.js
│       │   ├── emailService.js
│       │   ├── logger.js
│       │   ├── loggingService.js
│       │   ├── metricsService.js
│       │   ├── notificationService.js
│       │   ├── paymentsService.js
│       │   ├── pushNotificationService.js
│       │   ├── queryMonitorService.js
│       │   ├── sentryService.js
│       │   ├── smsService.js
│       │   ├── storageService.js
│       │   └── verificationService.js
│       ├── tests/
│       │   ├── setupTestDB.js
│       │   ├── integration/
│       │   │   ├── authFlow.test.js
│       │   │   ├── authRoutes.test.js
│       │   │   ├── serviceRoutes.test.js
│       │   │   ├── statsRoutes.test.js
│       │   │   └── verification.test.js
│       │   └── unit/
│       │       ├── authController.test.js
│       │       └── statsController.test.js
│       └── tests/
│           ├── integration/
│           │   ├── authFlow.test.js
│           │   └── paymentFlow.test.js
├── changanet-frontend/
│   ├── README.md
│   ├── tailwind.config.js
│   ├── vite.config.js
│   ├── public/
│   │   ├── firebase-messaging-sw.js
│   │   ├── index.html
│   │   └── vite.svg
│   └── src/
│       ├── index.css
│       ├── main.jsx
│       ├── serviceWorker.js
│       ├── assets/
│       │   └── react.svg
│       ├── components/
│       │   ├── NotificationBell.jsx
│       │   ├── NotificationCenter.jsx
│       │   ├── NotificationPanel.jsx
│       │   ├── OnboardingTutorial.jsx
│       │   ├── PayButton.jsx
│       │   ├── ProfessionalCard.jsx
│       │   ├── ProfilePicture.jsx
│       │   ├── QuickMessageModal.jsx
│       │   ├── QuoteRequestForm.jsx
│       │   ├── RankingDisplay.jsx
│       │   ├── RatingDisplay.jsx
│       │   ├── SearchBar.jsx
│       │   ├── SubscribeForm.jsx
│       │   ├── SuccessAlert.jsx
│       │   ├── VerificationForm.jsx
│       │   ├── VerifiedBadge.jsx
│       │   └── modals/
│       │       ├── LoginModal.jsx
│       │       ├── ProfileModal.jsx
│       │       ├── QuoteRequestModal.jsx
│       │       └── SignupModal.jsx
│       ├── config/
│       │   ├── firebaseConfig.js
│       │   └── sentryConfig.js
│       ├── context/
│       │   ├── AuthContext.jsx
│       │   ├── ChatContext.jsx
│       │   ├── ModalContext.jsx
│       │   └── NotificationContext.jsx
│       ├── data/
│       │   └── helpContent.js
│       ├── hooks/
│       │   ├── useAccessibility.js
│       │   ├── useChat.js
│       │   ├── useNotifications.js
│       │   ├── useOnboarding.js
│       │   └── useSmartNavigation.js
│       ├── i18n/
│       │   └── index.js
│       ├── pages/
│       │   ├── AdminVerification.jsx
│       │   ├── AdminVerificationPage.jsx
│       │   ├── AuthCallback.jsx
│       │   ├── Availability.jsx
│       │   ├── ClientDashboard.jsx
│       │   ├── ClientProfile.jsx
│       │   ├── ClientSettings.jsx
│       │   ├── ClientSignupPage.jsx
│       │   ├── ContactPage.jsx
│       │   ├── Cookies.jsx
│       │   ├── Custody.jsx
│       │   ├── Dashboard.jsx
│       │   ├── Home.jsx
│       │   ├── JoinPage.jsx
│       │   ├── Notifications.jsx
│       │   ├── Privacy.jsx
│       │   ├── ProfessionalDashboard.jsx
│       │   ├── ProfessionalDetail.jsx
│       │   ├── ProfessionalProfile.jsx
│       │   ├── Professionals.jsx
│       │   ├── ProfessionalSignupPage.jsx
│       │   ├── Profile.jsx
│       │   ├── Quotes.jsx
│       │   ├── Ranking.jsx
│       │   ├── Terms.jsx
│       │   ├── VerifyIdentity.jsx
│       ├── services/
│       │   ├── apiService.js
│       │   ├── authService.js
│       │   ├── chatService.js
│       │   ├── fcmService.js
│       │   ├── mapService.js
│       │   ├── notificationService.js
│       │   └── storageService.js
│       ├── styles/
│       │   └── onboarding.css
│       ├── test/
│       │   ├── importMetaMock.js
│       │   └── setup.js
│       └── tests/
│           ├── e2e/
│           │   ├── authFlow.e2e.js
│           │   └── paymentFlow.e2e.js
│           ├── integration/
│           │   └── homePage.test.js
│           └── unit/
│               ├── App.test.js
│               ├── GoogleLoginButton.test.jsx
│               └── VerificationForm.test.jsx
└── tests/
    └── README.md

```

---

## 🚀 **3. INSTALACIÓN PASO A PASO**

### **Paso 1: Clonar el Repositorio**
```bash
# Abrir terminal (PowerShell, CMD, Terminal)
cd D:\
git clone https://github.com/tu-usuario/changanet.git
cd changanet
```

### **Paso 2: Configurar el Backend**
```bash
cd changanet-backend
npm install
```

### **Paso 3: Configurar el Frontend**
```bash
cd ../changanet-frontend
npm install
```

---

## ⚙️ **4. CONFIGURACIÓN DE VARIABLES DE ENTORNO**

### **Backend: `changanet-backend/.env`**
Crea un archivo llamado `.env` en `D:\changanet\changanet-backend\.env` con este contenido:

```env
DATABASE_URL="postgresql://postgres:TU_CONTRASEÑA@localhost:5432/changanet?schema=public"
JWT_SECRET="super_secreto_para_jwt_2025"
PORT=3002
```

**¡Reemplaza `TU_CONTRASEÑA` con la contraseña real de tu usuario `postgres` en PostgreSQL!**

---

## 🗃️ **5. CREACIÓN DE LA BASE DE DATOS**

### **Paso 1: Verificar que PostgreSQL esté Corriendo**
1.  Ve a **Inicio > Servicios**.
2.  Busca **"postgresql-x64-XX"**.
3.  **Asegúrate de que su estado sea "En ejecución"**.

### **Paso 2: Generar la Base de Datos con Prisma**
```bash
# En terminal (D:\changanet\changanet-backend)
npx prisma migrate dev --name init
npx prisma generate
```

**Resultado Esperado:**
```
✔ Name of migration … init
✔ Applied migration 20250825120000_init
✔ Generated Prisma Client
```

---

## ▶️ **6. EJECUCIÓN DEL PROYECTO**

### **Paso 1: Iniciar el Backend**
**Abrir una nueva terminal:**
```bash
cd D:\changanet\changanet-backend
npm run dev
```

**Verás:**
```
🚀 Backend y Socket.IO corriendo en http://localhost:3002
```

### **Paso 2: Iniciar el Frontend**
**Abrir OTRA terminal:**
```bash
cd D:\changanet\changanet-frontend
npm run dev
```

**Verás:**
```
🚀 Frontend corriendo en http://localhost:5173
```

---

## 🧪 **7. PRUEBA DE FUNCIONALIDADES**

### **Prueba 1: Registro de Usuario**
1.  **Abrir Thunder Client o Postman.**
2.  **Enviar solicitud POST:**
    *   **URL:** `http://localhost:3002/api/auth/register`
    *   **Headers:** `Content-Type: application/json`
    *   **Body (JSON):**
        ```json
        {
          "email": "test@ejemplo.com",
          "password": "123456",
          "name": "Usuario Test",
          "role": "cliente"
        }
        ```
3.  **Resultado Esperado (Código 201):**
    ```json
    {
      "message": "Usuario creado. Revisa tu email para verificar tu cuenta."
    }
    ```

### **Prueba 2: Verificar Usuario en la Base de Datos**
1.  **Abrir pgAdmin.**
2.  **Ir a:** `Databases > changanet > Schemas > public > Tables > usuarios`
3.  **Haz doble clic en `está_verificado` del usuario `test@ejemplo.com` y cámbialo a `true`.**

### **Prueba 3: Login de Usuario**
1.  **Enviar solicitud POST:**
    *   **URL:** `http://localhost:3002/api/auth/login`
    *   **Headers:** `Content-Type: application/json`
    *   **Body (JSON):**
        ```json
        {
          "email": "test@ejemplo.com",
          "password": "123456"
        }
        ```
2.  **Resultado Esperado (Código 200):**
    ```json
    {
      "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
      "user": {
        "id": "uuid-del-usuario",
        "email": "test@ejemplo.com",
        "name": "Usuario Test",
        "role": "cliente"
      }
    }
    ```

### **Prueba 4: Probar el Frontend**
1.  **Abrir navegador en:** `http://localhost:5173`
2.  **Haz clic en "Iniciar Sesión".**
3.  **Ingresa las credenciales:**
    *   **Email:** `test@ejemplo.com`
    *   **Contraseña:** `123456`
4.  **Haz clic en "Iniciar Sesión".**
5.  **Resultado Esperado:**
    *   Serás redirigido al **Dashboard**.
    *   Verás: `"Hola, Usuario Test"` en la cabecera.

### **Prueba 5: Buscar Profesionales**
1.  **En la página de inicio, busca:**
    *   **¿Qué necesitas?:** `plomero`
    *   **¿Dónde?:** `Buenos Aires`
2.  **Haz clic en "Buscar Profesionales".**
3.  **Resultado Esperado:**
    *   Verás una lista de profesionales (datos de ejemplo).

### **Prueba 6: Probar el Chat en Tiempo Real**
1.  **Abrir dos pestañas del navegador.**
2.  **En cada pestaña, ve a `http://localhost:5173`.**
3.  **Inicia sesión con dos usuarios diferentes.**
4.  **Ve al perfil de un profesional y abre el chat.**
5.  **Envía un mensaje desde una pestaña.**
6.  **Resultado Esperado:**
    *   El mensaje aparece en tiempo real en la otra pestaña.

### **Prueba 7: Dejar una Reseña**
1.  **Simula un servicio completado (modifica estado en pgAdmin).**
2.  **Ve al perfil del profesional.**
3.  **Haz clic en la pestaña "Reseñas".**
4.  **Haz clic en "Dejar Reseña".**
5.  **Rellena el formulario y haz clic en "Enviar Reseña".**
6.  **Resultado Esperado:**
    *   La reseña aparece en la lista de reseñas del profesional.

### **Prueba 8: Gestionar Disponibilidad**
1.  **Inicia sesión como profesional.**
2.  **Ve a "Mi Cuenta" > "Mi Agenda".**
3.  **Agrega un bloque de disponibilidad:**
    *   **Fecha:** `2025-09-15`
    *   **Hora de Inicio:** `09:00`
    *   **Hora de Fin:** `12:00`
4.  **Haz clic en "Agregar Disponibilidad".**
5.  **Resultado Esperado:**
    *   El bloque aparece en tu agenda.

---

## 🔍 **8. VERIFICACIÓN DE LA BASE DE DATOS**

### **Paso 1: Verificar que PostgreSQL esté Corriendo**
1.  Ve a **Inicio > Servicios**.
2.  Busca **"postgresql-x64-XX"**.
3.  **Asegúrate de que su estado sea "En ejecución"**.

### **Paso 2: Conectarse con pgAdmin**
1.  Ve a **Inicio > pgAdmin 4**.
2.  Conéctate al servidor PostgreSQL.
3.  **¿Ves la base de datos `changanet`?**
    *   **✅ Si:** La base de datos fue creada correctamente.
    *   **❌ No:** Ejecuta:
        ```bash
        npx prisma migrate dev --name init
        npx prisma generate
        ```

### **Paso 3: Verificar Tablas**
1.  En pgAdmin, ve a **"Databases" > "changanet" > "Schemas" > "public" > "Tables"**.
2.  **¿Ves todas estas tablas?**
    *   `usuarios`
    *   `perfiles_profesionales`
    *   `servicios`
    *   `reseñas`
    *   `mensajes`
    *   `disponibilidad`
    *   `notificaciones`
    *   **✅ Si:** Las tablas fueron creadas correctamente.
    *   **❌ No:** Revisa el log del backend.

### **Paso 4: Verificar Datos**
1.  Haz clic derecho en `usuarios` > **"View/Edit Data" > "All Rows"**.
2.  **¿Ves al usuario `test@ejemplo.com` con `está_verificado = true`?**
    *   **✅ Si:** El registro y verificación funcionan.
    *   **❌ No:** Revisa el endpoint de registro y el campo `está_verificado`.

### **Paso 5: Verificar Conexión desde el Backend**
1.  En la terminal del backend, **¿ves este mensaje?**
    ```
    🚀 Backend y Socket.IO corriendo en http://localhost:3002
    ✅ Conexión a la base de datos exitosa
    ```
    *   **✅ Si:** El backend se conecta correctamente a la base de datos.
    *   **❌ No:** Revisa el archivo `.env` y la contraseña de PostgreSQL.

---

## 🛠️ **9. SOLUCIÓN DE PROBLEMAS COMUNES**

### **Problema 1: "Error de conexión. Inténtalo de nuevo." (Frontend)**

*   **Causa:** El frontend no puede conectarse al backend.
*   **Solución:**
    1.  **Verifica que el backend esté corriendo:**
        ```bash
        cd D:\changanet\changanet-backend
        npm run dev
        ```
    2.  **Verifica la URL en el frontend:**
        *   Abre `src/components/modals/LoginModal.jsx`.
        *   Asegúrate de que la URL sea:
            ```javascript
            fetch('http://localhost:3002/api/auth/login', {...})
            ```
    3.  **Verifica CORS en el backend:**
        *   Abre `src/server.js` del backend.
        *   Asegúrate de que tenga:
            ```javascript
            const cors = require('cors');
            app.use(cors({
              origin: "http://localhost:5173",
              methods: ["GET", "POST", "PUT", "DELETE"],
              credentials: true
            }));
            ```

### **Problema 2: "Este email ya está registrado."**

*   **Causa:** El email ya existe en la base de datos.
*   **Solución:**
    1.  **Ve a pgAdmin.**
    2.  **Elimina el usuario duplicado de la tabla `usuarios`.**
    3.  **O usa un email diferente para la prueba.**

### **Problema 3: "Error al registrar el usuario." (500 Internal Server Error)**

*   **Causa:** Hay un error en el código del backend.
*   **Solución:**
    1.  **Revisa la terminal del backend** para ver el mensaje de error detallado.
    2.  **Copia y pega el error** aquí para que te ayude a solucionarlo.

### **Problema 4: "Cannot GET /api/auth/register"**

*   **Causa:** Estás usando el método HTTP `GET` en lugar de `POST`.
*   **Solución:**
    *   En Postman/Thunder Client, asegúrate de usar **`POST`**.
    *   **Nunca abras `http://localhost:3002/api/auth/register` directamente en el navegador.**

### **Problema 5: Puerto 3002 o 5173 ocupado**

*   **Causa:** Otro proceso está usando el puerto.
*   **Solución:**
    ```bash
    # En Windows (PowerShell)
    netstat -ano | findstr :3002
    # Anota el PID (último número de la línea)
    taskkill /PID NUMERO_DEL_PID /F
    ```

### **Problema 6: "Datos de entrada inválidos"**

*   **Causa:** Los datos enviados no cumplen con las reglas de validación.
*   **Solución:**
    *   Asegúrate de enviar todos los campos requeridos:
        *   `email`: Formato válido (ej: `test@ejemplo.com`)
        *   `password`: Mínimo 6 caracteres
        *   `name`: Entre 2 y 100 caracteres
        *   `role`: `cliente` o `profesional`

---

## 🧰 **10. TECNOLOGÍAS UTILIZADAS**

### **Frontend**
*   **React.js** (con Vite)
*   **Tailwind CSS** (para diseño responsive)
*   **React Router DOM** (para navegación)
*   **Socket.IO Client** (para chat en tiempo real)

### **Backend**
*   **Node.js** (entorno de ejecución)
*   **Express.js** (framework web)
*   **Prisma** (ORM para PostgreSQL)
*   **Socket.IO** (para chat en tiempo real)
*   **JWT** (para autenticación)
*   **bcryptjs** (para hashear contraseñas)

### **Base de Datos**
*   **PostgreSQL** (sistema de gestión de bases de datos)
*   **pgAdmin** (interfaz gráfica para PostgreSQL)

### **Herramientas de Desarrollo**
*   **Git** (control de versiones)
*   **GitHub** (repositorio remoto)
*   **Thunder Client** (pruebas de API)
*   **Visual Studio Code** (editor de código)

---

## 🎯 **¡ÉXITO! Changánet está Funcionando Completamente**

Con este instructivo, has logrado:

*   **Instalar todas las herramientas necesarias.**
*   **Configurar el entorno de desarrollo.**
*   **Crear la base de datos con Prisma.**
*   **Ejecutar el frontend y el backend simultáneamente.**
*   **Probar todas las funcionalidades clave del MVP.**
*   **Verificar que los datos se guardan correctamente en la base de datos.**
