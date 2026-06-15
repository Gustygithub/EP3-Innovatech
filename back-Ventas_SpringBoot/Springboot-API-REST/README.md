# Springboot-API-REST-VENTAS

API REST desarrollada con Spring Boot y Java 17 para la gestión de ventas de Innovatech Chile.

## Tecnologías utilizadas

- Java 17
- Spring Boot
- Docker (multi-stage build)
- GitHub Actions (CI/CD)

## Cómo ejecutar con Docker

### 1. Clonar el repositorio
```bash
git clone https://github.com/Gustygithub/back-ventas.git
cd back-ventas
```

### 2. Construir la imagen
```bash
docker build -t back-ventas .
```

### 3. Ejecutar el contenedor
```bash
docker run -d --name back_ventas \
  -p 8082:8080 \
  back-ventas
```

## Pipeline CI/CD

El pipeline se activa automáticamente con cada push a la rama `deploy` y realiza:

1. **Build** → Construye la imagen Docker
2. **Push** → Publica la imagen en Docker Hub
3. **Deploy** → Despliega automáticamente en EC2

## Estructura del proyecto

```
├── src/                    # Código fuente
├── .github/
│   └── workflows/
│       └── deploy.yml      # Pipeline CI/CD
├── Dockerfile              # Multi-stage build
└── README.md
```