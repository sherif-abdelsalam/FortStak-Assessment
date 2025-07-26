# Docker Setup Instructions

## Prerequisites

- Docker
- Docker Compose

## Quick Start

### Using Docker Compose (Recommended)

1. **Clone the repository and navigate to the project directory**

2. **Copy environment file**
   ```bash
   cp .env.example .env
   ```
3. **Update the `.env` file with your MongoDB connection string** (optional - Docker Compose will use local MongoDB by default)

4. **Build and run the application**

   ```bash
   # For production
   docker-compose up --build

   # For development (with hot reload)
   docker-compose up app-dev --build
   ```

5. **Access the application**
   - Production: http://localhost:4000
   - Development: http://localhost:4001

### Using Docker Only

1. **Build the Docker image**

   ```bash
   # For production
   docker build --target production -t todo-app .

   # For development
   docker build --target development -t todo-app-dev .
   ```

2. **Run the container**

   ```bash
   # For production (requires external MongoDB)
   docker run -p 4000:4000 -e mongoDbUrl="your-mongodb-url" todo-app

   # For development
   docker run -p 4000:4000 -e mongoDbUrl="your-mongodb-url" todo-app-dev
   ```

## Environment Variables

- `mongoDbUrl`: MongoDB connection string
- `PORT`: Application port (default: 4000)
- `NODE_ENV`: Environment mode (development/production)

## Docker Compose Services

- **app**: Production version of the application
- **app-dev**: Development version with hot reload
- **mongo**: Local MongoDB instance

## Stopping the Application

```bash
# Stop all services
docker-compose down

# Stop and remove volumes
docker-compose down -v
```

## Logs

```bash
# View logs
docker-compose logs app

# Follow logs
docker-compose logs -f app
```
