# 🐳 Usar el Dev Container con Docker Compose

Esta guía te explica cómo levantar el Dev Container sin necesidad de usar Visual Studio Code.

## 📋 Requisitos Previos

1. **Docker Desktop** instalado y corriendo
2. **Docker Compose** (generalmente viene incluido con Docker Desktop)

## 🚀 Inicio Rápido

### Opción 1: Usando el script automatizado

Ejecuta el script `run.sh` que prepara todo automáticamente:

```bash
chmod +x run.sh
./run.sh
```

### Opción 2: Manualmente

1. Construye y levanta el contenedor:
```bash
docker compose up -d --build
```

2. Instala las dependencias:
```bash
docker compose exec app npm install
```

3. Inicia el servidor de desarrollo:
```bash
docker compose exec app npm run dev
```

## 📂 Comandos Útiles

### Acceder al contenedor
```bash
docker compose exec app bash
```

### Iniciar el servidor de desarrollo
```bash
docker compose exec app npm run dev
```

### Ver logs del contenedor
```bash
docker compose logs -f
```

### Detener el contenedor
```bash
docker compose down
```

### Reconstruir el contenedor
```bash
docker compose up -d --build
```

## 🌐 Acceder a la Aplicación

Una vez iniciado el servidor de desarrollo, puedes acceder a la aplicación en:
- **http://localhost:5174**

## 📝 Estructura de Archivos

- `docker-compose.yml`: Configuración del servicio Docker
- `run.sh`: Script automatizado para levantar el entorno
- `.devcontainer/`: Configuración original del Dev Container

## 🔧 Personalización

Si necesitas modificar la configuración:

1. **Para cambiar el puerto**: Modifica la sección `ports` en `docker-compose.yml`
2. **Para añadir variables de entorno**: Modifica la sección `environment` en `docker-compose.yml`
3. **Para cambiar la imagen base**: Modifica el `Dockerfile` en `.devcontainer/Dockerfile`

## 🐛 Solución de Problemas

### El contenedor no se inicia
1. Verifica que Docker esté corriendo
2. Ejecuta `docker compose down` y luego `docker compose up -d --build`

### Los cambios no se reflejan
1. Verifica que los volúmenes estén montados correctamente
2. Reinicia el servidor de desarrollo con `docker compose exec app npm run dev`

### No puedo acceder a la aplicación
1. Verifica que el puerto 5174 no esté en uso en tu máquina
2. Confirma que el servidor de desarrollo esté corriendo en el contenedor

## 📚 Más Información

- [Documentación de Docker Compose](https://docs.docker.com/compose/)
- [Documentación de Vite](https://vitejs.dev/)
- [README principal del proyecto](./README.md)