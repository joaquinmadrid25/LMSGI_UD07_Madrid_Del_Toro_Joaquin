# Manual de Explotacion - WillmanTech S.L.
## Basado en ISO/IEC/IEEE 26514:2022

---
# 1.Introduccion y Arquitectura

El ERP de WillmanTEch S.L. ha sido desplegado utilizando una arquitectura modular basada en contenedores Docker Compose.

## Componentes Principales

- Odoo ERP
- PostgreSQL
- Nginx Reverse Proxy
- Servicio de copias de seguridad

## Topología lógica
Usuario → Nginx → Odoo ERP → PostgreSQL

# 2. Guía de Instalación y Reinstalación

## Requisitos previos

- Docker
- Docker Compose
- 4 GB RAM mínimo
- Linux Ubuntu 22.04

## Variables de entorno

POSTGRES_DB=odoo
POSTGRES_USER=odoo
POSTGRES_PASSWORD=odoo123
HOST=localhost
PORT=8069

## Instalación
docker compose up -d
## Reinstalación
docker compose down -v
docker compose up -d --build

# 3. Administración del Sistema
Acceso al ERP

URL: http://localhost:8200

- Usuarios
- Administrador
- Contable
- Comercial

# 4. Copias de Seguridad

## Backup manual
docker exec postgres pg_dump -U odoo odoo > backup.sql

## Restauración
psql -U odoo odoo < backup.sql

# 5. Seguridad
- Uso de HTTPS
- Gestión de permisos por roles
- Contraseñas cifradas
- Firewall activo

## 6. Monitorización y Logs
Logs principales:

docker logs odoo
docker logs postgres

# 7. Resolución de Problemas
Error de conexión con PostgreSQL
Verificar:

docker ps
Error de permisos
Comprobar permisos de carpetas:

chmod -R 755 ./data
