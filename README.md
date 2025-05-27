# Spring Boot Microservices Project

(Eureka Server, Config Server, API Gateway, Kafka, File Storage, JWT, Authentication, Authorization, Redis, Docker)

8 services whose name are shown below have been devised within the scope of this project.

- Config Server
- Eureka Server
- API Gateway
- Auth Service
- Job Service
- User Service
- Notification Service
- File Storage

¡Perfecto! Entender y documentar la arquitectura de un proyecto de **microservicios** es una excelente práctica, sobre todo para aclarar responsabilidades y facilitar futuras modificaciones.

Te ayudaré a **documentar el rol y funcionalidad de cada uno de los servicios** mencionados en tu proyecto de Spring Boot. Vamos a hacerlo de manera clara y profesional, como para incluirlo en un `README.md` o en la documentación técnica del sistema.

---

## 🧾 Documentación de servicios en la arquitectura de microservicios

### 🧩 1. **Config Server**

**Rol:**
Servidor centralizado de configuración.

**Funcionalidad:**
Proporciona archivos de configuración (`application.yml` o `application.properties`) a los demás microservicios. Permite centralizar y actualizar configuraciones sin necesidad de redeploy.

**Tecnología común:**
Spring Cloud Config Server.

---

### 📡 2. **Eureka Server**

**Rol:**
Servicio de descubrimiento.

**Funcionalidad:**
Permite que los microservicios se registren automáticamente y se descubran entre sí. Elimina la necesidad de conocer direcciones IP o puertos fijos.
Cuando un servicio se inicia, se registra en Eureka.

**Tecnología común:**
Spring Cloud Netflix Eureka.

---

### 🌐 3. **API Gateway**

**Rol:**
Punto de entrada único a todo el sistema.

**Funcionalidad:**

- Redirige las solicitudes entrantes a los microservicios correspondientes.
- Aplica filtros de seguridad (como autenticación de tokens).
- Puede manejar CORS, logging, throttling, etc.

**Tecnología común:**
Spring Cloud Gateway.

---

### 🔐 4. **Auth Service**

**Rol:**
Servicio de autenticación y autorización.

**Funcionalidad:**

- Registro y login de usuarios (ADMIN / USER).
- Generación y validación de tokens JWT.
- Control de acceso a los endpoints según el rol del usuario.

**Posible stack:**
Spring Security + JWT + BCrypt.

---

### 💼 5. **Job Service**

**Rol:**
Gestión de trabajos/ofertas/labores.

**Funcionalidad:**

- Crear, actualizar, eliminar y listar ofertas de trabajo.
- Asociar trabajos con usuarios (por ejemplo, postulaciones o publicaciones).
- Gestionar categorías, descripciones, requisitos, etc.

---

### 👤 6. **User Service**

**Rol:**
Gestión de información del usuario.

**Funcionalidad:**

- Consultar y actualizar el perfil del usuario.
- Relacionarse con los servicios de Auth y Job.
- Posiblemente tenga lógica como currículum, historial, etc.

---

### 📧 7. **Notification Service**

**Rol:**
Enviar notificaciones a los usuarios.

**Funcionalidad:**

- Puede enviar correos electrónicos o mensajes push.
- Notifica sobre nuevos trabajos, cambios de estado, etc.
- Suele comunicarse con otros servicios mediante colas (RabbitMQ, Kafka, etc.).

---

### 🗂️ 8. **File Storage Service**

**Rol:**
Gestión de archivos.

**Funcionalidad:**

- Subida y descarga de archivos como CV, imágenes de perfil, etc.
- Almacenamiento local o en la nube (S3, MinIO, etc.).
- Asocia archivos con usuarios u ofertas de trabajo.

---

## 🗺️ Mapa general del flujo

```plaintext
                   [ Usuario Frontend ]
                          │
                          ▼
                   [ API Gateway ]
                          │
        ┌─────────────────┼─────────────────┐
        ▼                 ▼                 ▼
 [ Auth Service ]  [ Job Service ]   [ User Service ]
                          │
                          ▼
                [ Notification Service ]
                          │
                          ▼
                [ File Storage Service ]
```

Los microservicios obtienen configuración desde el **Config Server**
Todos los servicios se registran en **Eureka Server**
Todos los llamados pasan por el **API Gateway**

---

### 🔨 Run the App

<b>Local</b>

<b>1 )</b> Clone project

<b>2 )</b> Go to the project's home directory : `cd spring-boot-microservices`

<b>3 )</b> Run docker compose <b>`docker compose up`</b></b>

<b>4 )</b> Run <b>Eureka Server</b>

<b>5 )</b> Run <b>Gateway</b>

<b>6 )</b> Run <b>Config Server</b>

<b>7 )</b> Run other services (<b>auth-service</b>, <b>user-service</b>, <b>job-service</b>, <b>notification-service</b> and lastly <b>
file-storage</b>)

<b>8 )</b> For swagger ui localhost:8080/v1/{service-name}/swagger-ui/index.html</b>
