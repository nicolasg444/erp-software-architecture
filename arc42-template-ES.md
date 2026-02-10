# 

**Acerca de arc42**

arc42, La plantilla de documentación para arquitectura de sistemas y de
software.

Por Dr. Gernot Starke, Dr. Peter Hruschka y otros contribuyentes.

Revisión de la plantilla: 7.0 ES (basada en asciidoc), Enero 2017

© Reconocemos que este documento utiliza material de la plantilla de
arquitectura arc42, <https://www.arc42.org>. Creada por Dr. Peter
Hruschka y Dr. Gernot Starke.

# Introducción y Metas
# 1. Introducción y Objetivos

## Objetivo del Sistema ERP
El sistema ERP tiene como objetivo integrar y automatizar los procesos empresariales, permitiendo la gestión eficiente de compras, inventarios, proveedores y productos, mejorando la trazabilidad y control de la información.

## Objetivo del Módulo de Compras
El módulo de compras permite gestionar proveedores, registrar órdenes de compra, controlar la adquisición de productos y garantizar la disponibilidad de inventario.

## Vista de Requerimientos 
## Requisitos de Negocio Principales
- Registrar y gestionar proveedores.
- Crear y administrar órdenes de compra.
- Registrar productos adquiridos.
- Consultar historial de compras.
- Generar reportes de compras.
- Controlar el estado de las órdenes (pendiente, aprobada, recibida).

## Metas de Calidad 
## Metas de Calidad

- Usabilidad: El sistema debe ser fácil de usar por el personal de compras.
- Rendimiento: Las consultas deben responder en menos de 2 segundos.
- Seguridad: Acceso controlado mediante autenticación y roles.
- Escalabilidad: Permitir agregar nuevos módulos en el futuro.

## Partes interesadas (Stakeholders)

| Rol            | Contacto                  | Expectativas                              |
|----------------|---------------------------|------------------------------------------|
| Administrador  | admin@empresa.com         | Control total del sistema                |
| Compras        | compras@empresa.com       | Gestionar proveedores y órdenes de compra|
| Gerencia       | gerente@empresa.com       | Reportes y métricas del sistema          |


# Restricciones de la Arquitectura

- Backend desarrollado en Java con Spring Boot.
- Base de datos PostgreSQL.
- Frontend desarrollado en React (SPA).
- Comunicación mediante API REST.
- Despliegue usando Docker.
- El sistema debe ser accesible vía navegador web.

## Estrategia de Solución

La solución se basa en una arquitectura de tres capas:

Presentación: Frontend React (SPA).

Lógica de Negocio: Backend Spring Boot.

Persistencia: Base de datos PostgreSQL.

Se utiliza Docker para facilitar el despliegue y la portabilidad del sistema.
  
## Sistema General de Caja Blanca 
Motivación

Separar responsabilidades para facilitar el mantenimiento, la escalabilidad y la evolución del sistema.

Bloques de Construcción Contenidos

Frontend

Backend

Base de Datos

Servicio de Autenticación

Interfaces Importantes

API REST entre Frontend y Backend

Conexión JDBC entre Backend y PostgreSQL

Caja Negra 1: Frontend Web

Propósito: Interacción con el usuario.

Interfases: API REST.

Características de Calidad: Usabilidad y rendimiento.

Caja Negra 2: Backend API

Propósito: Lógica de negocio.

Interfases: REST, JDBC.

Características de Calidad: Seguridad y rendimiento.

Caja Negra 3: Base de Datos

Propósito: Persistencia de información.

Interfases: SQL.

# Alcance y Contexto del Sistema 
## Contexto de Negocio

El sistema ERP interactúa con usuarios internos (personal de compras y administradores) y proveedores externos.



# Vista de Bloques 
### Bloques de Construcción

- Frontend Web (React): Interfaz para usuarios.
- Backend API (Spring Boot): Lógica de negocio.
- Base de Datos PostgreSQL: Almacenamiento de datos.
- Servicio de Autenticación: Gestión de usuarios y roles.


# Vista de Ejecución 

## Escenario de ejecución: Registrar Producto


### Flujo
1. El usuario ingresa los datos del producto en el frontend.
2. El frontend envía la solicitud al backend.
3. El backend valida los datos.
4. El backend guarda el producto en la base de datos.
5. Se devuelve confirmación al usuario.




## Nivel de infraestructura 1 
Motivación

Garantizar disponibilidad, escalabilidad y facilidad de despliegue.

Características de Calidad/Rendimiento

Alta disponibilidad.

Aislamiento mediante contenedores.

Facilidad de escalado.

Mapeo de Bloques a Infraestructura

Frontend → Contenedor Web

Backend → Contenedor Spring Boot

Base de Datos → Contenedor PostgreSQL

## Conceptos Transversales 
Seguridad

Autenticación basada en usuarios y roles.

Manejo de Errores

Gestión centralizada de excepciones en el backend.

Logging

Registro de eventos y errores para auditoría y soporte.

## Decisiones de Diseño 

Uso de arquitectura REST.

Separación Frontend / Backend.

Uso de contenedores Docker.

Base de datos relacional PostgreSQL.

## Requerimientos de Calidad 
Árbol de Calidad 
Usabilidad

Rendimiento

Seguridad

Escalabilidad
# Vista de Despliegue

El sistema se desplegará en un servidor usando contenedores Docker.

- Contenedor Backend Spring Boot
- Contenedor PostgreSQL
- Servidor Web React
- Nginx como proxy inverso

# Glosario

| Término        | Definición |
|----------------|------------|
| Producto       | Bien adquirido o vendido por la empresa |
| Proveedor      | Persona o empresa que suministra productos |
| Orden de Compra| Documento que autoriza la compra |
| ERP            | Sistema de planificación de recursos empresariales |
| Inventario     | Productos almacenados |
| Usuario        | Persona que usa el sistema |
