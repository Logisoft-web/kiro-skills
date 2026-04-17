---
name: produccion-checklist
description: Checklist completo antes de subir cualquier proyecto a producción
inclusion: manual
---

# Checklist de Producción

Antes de hacer deploy de cualquier proyecto, verificar TODOS estos puntos.

## 🔐 Seguridad

- [ ] Auditoría de seguridad completada (ver skill `security-audit`)
- [ ] Contraseñas por defecto cambiadas
- [ ] Variables de entorno en `.env` (no hardcodeadas)
- [ ] `.env` en `.gitignore`
- [ ] CORS configurado solo para dominios permitidos
- [ ] `npm audit` sin vulnerabilidades críticas

## 🧪 Pruebas Locales

- [ ] La app corre localmente sin errores (`node src/server.js`)
- [ ] Todas las rutas principales responden correctamente
- [ ] Login funciona para todos los roles
- [ ] Funcionalidades críticas probadas manualmente:
  - [ ] Registro y login de usuarios
  - [ ] CRUD principal del proyecto
  - [ ] Flujos de negocio principales
- [ ] La app funciona en móvil (responsive)
- [ ] No hay errores en consola del navegador

## 🐳 Docker

- [ ] `Dockerfile` creado y probado localmente
- [ ] `docker compose up --build` funciona sin errores
- [ ] La app responde dentro del contenedor
- [ ] Volúmenes de datos configurados (base de datos persistente)
- [ ] Variables de entorno pasadas correctamente al contenedor
- [ ] `restart: unless-stopped` configurado
- [ ] Puerto correcto y sin conflictos con otros contenedores

## 🌐 DNS y Red

- [ ] Subdominio creado en el panel DNS (mi.com.co)
- [ ] Subdominio apuntando a IP `149.130.175.46`
- [ ] DNS propagado (verificar con `nslookup subdominio.logisoft-web.com`)
- [ ] Puertos 80 y 443 abiertos en Security List de Oracle Cloud
- [ ] Firewall Ubuntu configurado (`ufw allow 80`, `ufw allow 443`)

## 🔧 Servidor

- [ ] Nginx configurado para el subdominio
- [ ] Nginx recargado (`sudo nginx -t && sudo systemctl reload nginx`)
- [ ] SSL obtenido con Certbot
- [ ] Redirección HTTP → HTTPS funcionando
- [ ] Contenedor corriendo (`docker ps`)
- [ ] App respondiendo en el subdominio

## 📦 Código

- [ ] Último commit pusheado a GitHub
- [ ] No hay archivos de debug o console.log innecesarios
- [ ] `NODE_ENV=production` configurado
- [ ] `TZ=America/Bogota` configurado
- [ ] Puerto configurable por variable de entorno

## 🗄️ Base de Datos

- [ ] Base de datos inicializa correctamente en el contenedor
- [ ] Datos persistentes en volumen Docker (no se pierden al reiniciar)
- [ ] Usuario admin creado con contraseña segura
- [ ] Archivo `.db` no está en el repositorio

## 📋 Post-Deploy

- [ ] Verificar que la app carga en el subdominio
- [ ] Probar login con credenciales de producción
- [ ] Revisar logs del contenedor (`docker compose logs -f`)
- [ ] Verificar que el SSL está activo (candado verde en el navegador)
- [ ] Actualizar el portafolio con el link del proyecto desplegado

## 🚨 Rollback

Si algo falla en producción:
```bash
# Ver logs del contenedor
docker compose logs -f

# Reiniciar contenedor
docker compose restart

# Volver a versión anterior
git log --oneline
git checkout <commit-hash>
docker compose up -d --build
```
