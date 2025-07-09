# 📦 Sistema de Soporte Técnico – Parcial Final Programación N-Capas

Este proyecto es parte del parcial final de la materia **Programación N-Capas**.
Simula un sistema de soporte técnico donde usuarios pueden registrar tickets y técnicos pueden gestionarlos. 
Se implementa seguridad con **JWT**, roles con **Spring Security**, 
y se despliega completamente con **Docker**.

---

## 🛠 Tecnologías utilizadas

- Java 21
- Spring Boot 3.4.4
- Spring Security + JWT
- PostgreSQL
- Docker + Docker Compose
- Lombok

---

## 🔐 Seguridad

La aplicación utiliza **JWT (JSON Web Tokens)** para autenticación y autorización. Todos los endpoints están protegidos excepto `/auth/login`.

### Roles implementados:

 Rol   | Permisos                                                       
 Rol   | Permisos                                                        
 USER  | Crear tickets, ver solo sus propios tickets                    
 TECH  | Ver todos los tickets, actualizar el estado de los tickets     

---

## 🔑 Endpoints principales

| Método | Endpoint         | Descripción                                     | Autenticación |
| POST   | `/auth/login`    | Iniciar sesión y obtener token JWT              |  Pública   |
| GET    | `/tickets`       | Listar tickets (según rol del usuario)          |  JWT       |
| POST   | `/tickets`       | Crear un nuevo ticket (solo USER)               |  JWT       |
| PUT    | `/tickets/{id}`  | Actualizar ticket (solo TECH)                   |  JWT       |

---

## ⚙️ Configuración de base de datos (en `application.yml`)

```yaml
spring:
  datasource:
    url: jdbc:postgresql://db:5432/supportdb
    username: postgres
    password: admin
  jpa:
    hibernate:
      ddl-auto: update
    show-sql: true
