---
name: docker-deploy
description: Guía para dockerizar y desplegar proyectos en Oracle Cloud Ubuntu con Nginx
inclusion: manual
---

# Docker Deploy — Oracle Cloud Ubuntu

Cuando el usuario pida dockerizar o desplegar un proyecto, sigue este proceso completo.

## Stack de Producción

```
Internet
   │
   ▼
Nginx (reverse proxy + SSL)  → puerto 80/443
   │
   ├── runningtrainer.logisoft-web.com  → contenedor Running     (puerto 3001)
   ├── indoornavigator.logisoft-web.com → contenedor Orientacion (puerto 3002)
   ├── postienda.logisoft-web.com       → contenedor Tienda      (puerto 3003)
   └── logisoft-web.com                 → Portafolio estático    (puerto 3000)
```

## Paso 1 — Dockerfile estándar para proyectos Node.js

```dockerfile
FROM node:20-alpine

WORKDIR /app

# Copiar dependencias primero (cache de capas)
COPY package*.json ./
RUN npm ci --only=production

# Copiar código fuente
COPY . .

# Crear directorio de datos persistente
RUN mkdir -p /app/data

EXPOSE 3000

CMD ["node", "src/server.js"]
```

## Paso 2 — docker-compose.yml por proyecto

```yaml
version: '3.8'
services:
  app:
    build: .
    container_name: nombre-proyecto
    restart: unless-stopped
    ports:
      - "3001:3000"
    volumes:
      - ./data:/app/data        # persistencia de BD
      - ./.env:/app/.env        # variables de entorno
    environment:
      - NODE_ENV=production
      - TZ=America/Bogota
```

## Paso 3 — Configuración Nginx por subdominio

```nginx
server {
    listen 80;
    server_name runningtrainer.logisoft-web.com;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl;
    server_name runningtrainer.logisoft-web.com;

    ssl_certificate /etc/letsencrypt/live/runningtrainer.logisoft-web.com/fullchain.pem;
    ssl_certificate_key /etc/letsencrypt/live/runningtrainer.logisoft-web.com/privkey.pem;

    location / {
        proxy_pass http://localhost:3001;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_cache_bypass $http_upgrade;
    }
}
```

## Paso 4 — Instalación en servidor Ubuntu (Oracle Cloud)

```bash
# 1. Actualizar sistema
sudo apt update && sudo apt upgrade -y

# 2. Instalar Docker
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER

# 3. Instalar Docker Compose
sudo apt install docker-compose-plugin -y

# 4. Instalar Nginx
sudo apt install nginx -y

# 5. Instalar Certbot
sudo apt install certbot python3-certbot-nginx -y

# 6. Abrir puertos en Oracle Cloud (Security List)
# Puerto 80 (HTTP) y 443 (HTTPS) — hacerlo desde la consola de Oracle

# 7. Abrir puertos en firewall Ubuntu
sudo ufw allow 80
sudo ufw allow 443
sudo ufw allow 22
sudo ufw enable
```

## Paso 5 — Desplegar un proyecto

```bash
# Clonar repo
git clone https://github.com/usuario/proyecto.git
cd proyecto

# Crear .env de producción
cp src/config/.env.example src/config/.env
nano src/config/.env  # editar valores reales

# Build y arrancar
docker compose up -d --build

# Ver logs
docker compose logs -f

# Verificar que corre
docker compose ps
```

## Paso 6 — SSL con Certbot

```bash
# Obtener certificado (el dominio debe apuntar al servidor)
sudo certbot --nginx -d runningtrainer.logisoft-web.com

# Renovación automática
sudo certbot renew --dry-run
```

## Comandos útiles en producción

```bash
# Ver todos los contenedores
docker ps

# Reiniciar un contenedor
docker compose restart

# Actualizar código (pull + rebuild)
git pull && docker compose up -d --build

# Ver uso de recursos
docker stats

# Limpiar imágenes viejas
docker system prune -f
```

## Checklist antes de hacer deploy

- [ ] DNS del subdominio apuntando a la IP del servidor
- [ ] `.env` de producción configurado con valores reales
- [ ] Puerto correcto en docker-compose.yml (sin conflictos)
- [ ] Nginx configurado para el subdominio
- [ ] Firewall de Oracle Cloud con puertos 80 y 443 abiertos
- [ ] SSL obtenido con Certbot
- [ ] Contenedor corriendo y respondiendo
