# Front Despacho

Aplicación Frontend desarrollada con React + Vite para el sistema de despachos de Innovatech Chile.

## Tecnologías utilizadas

- React 18
- Vite
- Tailwind CSS
- Docker (multi-stage build + Nginx)
- GitHub Actions (CI/CD)

## Cómo ejecutar con Docker

### 1. Clonar el repositorio
```bash
git clone https://github.com/Gustygithub/front-despacho.git
cd front-despacho
```

### 2. Construir la imagen
```bash
docker build -t front-despacho .
```

### 3. Ejecutar el contenedor
```bash
docker run -d --name frontend \
  -p 80:80 \
  front-despacho
```

### 4. Abrir en el navegador
http://localhost

## Pipeline CI/CD

El pipeline se activa automáticamente con cada push a la rama `deploy` y realiza:

1. **Build** → Construye la imagen Docker con Nginx
2. **Push** → Publica la imagen en Docker Hub
3. **Deploy** → Despliega automáticamente en EC2

## Estructura del proyecto
├── src/                    # Código fuente React
├── public/                 # Archivos estáticos
├── .github/
│   └── workflows/
│       └── deploy.yml      # Pipeline CI/CD
├── Dockerfile              # Multi-stage build con Nginx
├── docker-compose.yml      # Stack completo
└── README.md

## Despliegue en AWS EC2

El Frontend está desplegado en una instancia EC2 pública accesible desde Internet. Se comunica con el Backend desplegado en subred privada respetando las políticas de Security Groups.