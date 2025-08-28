# Simulador Electoral D'Hont - Córdoba 2025

Simulador interactivo del sistema electoral D'Hont para las elecciones de diputados nacionales de Córdoba 2025.

## 🗳️ Características

- **Simulación completa del método D'Hont** con 18 listas electorales reales
- **Interfaz educativa** que explica paso a paso cómo funciona el sistema
- **Tabla de cocientes interactiva** con visualización del proceso de asignación
- **Distribución automática** de votos entre listas menores
- **Diseño responsivo** con Tailwind CSS v4
- **Resultados detallados** con candidatos electos por orden de lista

## 🚀 Desarrollo Local

### Requisitos
- Node.js 18+
- npm

### Instalación
```bash
npm install
npm run dev
```

### Docker (Desarrollo)
```bash
# Construir y ejecutar contenedor de desarrollo
npm run docker:dev

# O manualmente
docker-compose up dhont-dev
```

## 🐳 Deployment con Docker

### Build local
```bash
npm run docker:build
npm run docker:run
```

### Docker Compose (Producción)
```bash
docker-compose up dhont-prod
```

## 🌐 Deployment en Render

### Opción 1: Usando render.yaml (Recomendado)
1. Conecta tu repositorio a Render
2. El archivo `render.yaml` configurará automáticamente el servicio
3. Render detectará el Dockerfile y construirá la imagen

### Opción 2: Manual
1. Crear nuevo Web Service en Render
2. Conectar repositorio de GitHub
3. Configurar:
   - **Environment**: Docker
   - **Dockerfile Path**: `./Dockerfile`
   - **Port**: 80
   - **Health Check Path**: `/health`

### Variables de entorno (Render)
```
NODE_ENV=production
PORT=80
```

## 📁 Estructura del Proyecto

```
/
├── src/
│   ├── components/
│   │   └── ElectoralSimulator.astro    # Componente principal
│   ├── layouts/
│   │   └── Layout.astro                # Layout base
│   ├── pages/
│   │   └── index.astro                 # Página principal
│   └── styles/
│       └── global.css                  # Estilos globales
├── Dockerfile                          # Imagen de producción
├── Dockerfile.dev                      # Imagen de desarrollo
├── docker-compose.yml                  # Orquestación de contenedores
├── nginx.conf                          # Configuración Nginx
├── render.yaml                         # Configuración Render
└── .dockerignore                       # Archivos excluidos de Docker
```

## 🛠️ Scripts Disponibles

| Comando | Descripción |
|---------|-------------|
| `npm run dev` | Servidor de desarrollo |
| `npm run build` | Build de producción |
| `npm run preview` | Preview local del build |
| `npm run start` | Servidor de producción |
| `npm run docker:dev` | Desarrollo con Docker |
| `npm run docker:build` | Build imagen Docker |
| `npm run docker:run` | Ejecutar contenedor |

## 🎯 Tecnologías

- **Astro 5.13** - Framework web moderno
- **Tailwind CSS v4** - Estilos utilitarios
- **Docker** - Containerización
- **Nginx** - Servidor web de producción
- **Render** - Plataforma de deployment

## 📊 Funcionalidades del Simulador

1. **Configuración de participación electoral**
2. **Carga de resultados por lista** (mínimo 4 listas principales)
3. **Distribución automática** del resto de votos
4. **Cálculo D'Hont** con visualización paso a paso
5. **Resultados detallados** con diputados electos
6. **Tabla explicativa** del proceso de asignación

## 🔧 Configuración para Producción

El proyecto está optimizado para deployment en Render con:
- Build multi-stage para optimizar tamaño de imagen
- Nginx con compresión gzip y headers de seguridad
- Health check endpoint en `/health`
- Configuración de cache para assets estáticos
- Variables de entorno para diferentes ambientes
