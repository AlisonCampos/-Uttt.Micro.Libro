# Uttt.Micro.Libro

Microservicio para la gestión de libros, desarrollado en .NET 9, con Entity Framework Core y MySQL, preparado para ejecutarse en contenedores Docker.

## Características

- API RESTful para gestión de libros.
- Entity Framework Core con Pomelo para MySQL.
- Arquitectura limpia con MediatR, AutoMapper y FluentValidation.
- Swagger/OpenAPI para documentación y pruebas.
- Listo para desarrollo local y despliegue con Docker Compose.

## Requisitos

- [.NET 9 SDK](https://dotnet.microsoft.com/download)
- [Docker](https://www.docker.com/)
- [Docker Compose](https://docs.docker.com/compose/)

## Configuración rápida

### 1. Clonar el repositorio

```sh
git clone <url-del-repo>
cd Uttt.Micro.Libro
```

### 2. Levantar los contenedores

Esto iniciará tanto la API como la base de datos MySQL:

```sh
docker compose up --build -d
```

### 3. Aplicar migraciones (opcional)

Si necesitas aplicar migraciones manualmente:

```sh
docker compose exec libro dotnet ef database update
```

### 4. Probar la API

- Accede a la documentación Swagger en:  
  [http://localhost:5000/swagger](http://localhost:5000/swagger)
- Prueba los endpoints, por ejemplo:
  ```sh
  curl http://localhost:5000/api/LibroMaterial
  ```

## Variables de entorno y configuración

La cadena de conexión a MySQL se encuentra en [`appsettings.json`](appsettings.json):

```json
"ConnectionStrings": {
  "DefaultConnection": "server=mysql;database=librosdb;user=librouser;password=libropassword;"
}
```

Estos valores deben coincidir con los definidos en [`docker-compose.yml`](docker-compose.yml).

## Estructura del proyecto

- `Controllers/` - Controladores de la API.
- `Aplication/` - Lógica de aplicación (CQRS, DTOs, validaciones).
- `Modelo/` - Entidades del dominio.
- `Persistencia/` - Contexto de EF Core.
- `Migrations/` - Migraciones de base de datos.
- `Extensiones/` - Métodos de extensión para configuración.
- `Program.cs` - Configuración y arranque de la aplicación.

## Comandos útiles

- **Ver logs de la API:**
  ```sh
  docker compose logs -f libro
  ```
- **Detener y eliminar contenedores:**
  ```sh
  docker compose down
  ```

## Notas

- El proyecto expone la API en el puerto 5000 por defecto.
- Si cambias el puerto en [`docker-compose.yml`](docker-compose.yml), actualiza las instrucciones de acceso.

---

¡Contribuciones y sugerencias son bienvenidas!