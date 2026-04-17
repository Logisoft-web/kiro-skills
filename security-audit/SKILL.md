---
name: security-audit
description: Auditoría de seguridad para proyectos Node.js antes de producción
inclusion: manual
---

# Auditoría de Seguridad — Node.js / Express

Cuando el usuario pida auditar un proyecto, revisa TODOS estos puntos sin excepción.

## 1. Credenciales y Secrets

- [ ] No hay contraseñas hardcodeadas en el código fuente
- [ ] No hay tokens, API keys o secrets en archivos `.js`, `.ts`, `.html`
- [ ] El archivo `.env` está en `.gitignore` y NO está en el repositorio
- [ ] Existe un `.env.example` con valores de ejemplo (sin datos reales)
- [ ] Las contraseñas de admin por defecto han sido cambiadas (ej: `admin123`)
- [ ] Las contraseñas de usuarios se almacenan con hash (bcrypt, argon2) — NO en texto plano

## 2. Autenticación y Autorización

- [ ] Todas las rutas sensibles requieren autenticación
- [ ] Los roles (admin, monitor, etc.) se validan en el backend, no solo en el frontend
- [ ] Los tokens JWT tienen expiración definida
- [ ] No se exponen datos sensibles en los endpoints públicos
- [ ] El endpoint de login tiene protección contra fuerza bruta (rate limiting)

## 3. CORS y Headers

- [ ] CORS no está abierto a `*` en producción — solo dominios permitidos
- [ ] Headers de seguridad configurados (helmet.js recomendado)
- [ ] No se expone información del servidor en headers (X-Powered-By desactivado)

## 4. Base de Datos

- [ ] Todas las queries usan parámetros preparados (no concatenación de strings)
- [ ] No hay SQL injection posible
- [ ] El archivo de base de datos (.db) está en `.gitignore`
- [ ] Backups automáticos configurados en producción

## 5. Variables de Entorno

- [ ] `PORT` configurable por variable de entorno
- [ ] `NODE_ENV=production` en producción
- [ ] `TZ=America/Bogota` configurado
- [ ] No hay valores por defecto inseguros en producción

## 6. Dependencias

- [ ] Ejecutar `npm audit` y revisar vulnerabilidades críticas
- [ ] Dependencias actualizadas (sin versiones con CVEs conocidos)
- [ ] No hay dependencias de desarrollo en producción (`devDependencies` separadas)

## 7. Archivos Expuestos

- [ ] El servidor no sirve archivos sensibles (.env, .db, logs)
- [ ] El directorio `node_modules` no está en el build de producción
- [ ] No hay rutas de debug o endpoints de prueba activos en producción

## 8. HTTPS / SSL

- [ ] La app corre detrás de Nginx con SSL (Certbot)
- [ ] Redirección automática de HTTP a HTTPS
- [ ] Certificado SSL válido y con renovación automática

## Reporte

Al finalizar la auditoría, genera un reporte con:
- ✅ Puntos que pasan
- ⚠️ Puntos que necesitan atención
- ❌ Puntos críticos que DEBEN corregirse antes de producción
