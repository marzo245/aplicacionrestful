# Aplicación RESTful - Spring Boot

Esta aplicación es un servicio web RESTful construido con Spring Boot que proporciona un endpoint de saludo básico. El proyecto está basado en la [guía oficial de Spring Boot para construir servicios REST](https://spring.io/guides/gs/rest-service).

## ¿Qué construye esta aplicación?

Esta aplicación construye un servicio que acepta peticiones HTTP GET en `http://localhost:8080/greeting`.

Responde con una representación JSON de un saludo, como se muestra a continuación:

```json
{"id":1,"content":"Hello, World!"}
```

Puedes personalizar el saludo con un parámetro opcional `name` en la cadena de consulta:

```
http://localhost:8080/greeting?name=Usuario
```

El valor del parámetro `name` anula el valor predeterminado de "World" y se refleja en la respuesta:

```json
{"id":1,"content":"Hello, Usuario!"}
```

## Estructura del Proyecto

```
aplicacionrestful/
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com/
│   │   │       └── edu/
│   │   │           └── escuelaing/
│   │   │               └── aplicacionrestful/
│   │   │                   ├── AplicacionrestfulApplication.java
│   │   │                   └── RestServiceApplication.java
│   │   └── resources/
│   │       ├── application.properties
│   │       ├── static/
│   │       └── templates/
│   └── test/
│       └── java/
│           └── com/
│               └── edu/
│                   └── escuelaing/
│                       └── aplicacionrestful/
│                           └── AplicacionrestfulApplicationTests.java
├── target/
├── pom.xml
├── mvnw
├── mvnw.cmd
├── HELP.md
└── README.md
```

## Requisitos

- **Java 17** o superior
- **Maven 3.5+** o superior
- Editor de texto favorito o IDE (recomendado: IntelliJ IDEA, Eclipse, VS Code)

## Dependencias Principales

- **Spring Boot Starter Web**: Para construir aplicaciones web, incluyendo RESTful
- **Spring Boot Starter Test**: Para testing con JUnit, Hamcrest y Mockito
- **Jackson**: Para conversión automática de objetos Java a JSON (incluido por defecto)

## Cómo ejecutar la aplicación

### Opción 1: Usar Maven Wrapper (Recomendado)

```bash
# En Windows
mvnw.cmd spring-boot:run

# En Unix/Linux/macOS
./mvnw spring-boot:run
```

### Opción 2: Construir y ejecutar JAR

```bash
# Construir el proyecto
mvnw.cmd clean package

# Ejecutar el JAR generado
java -jar target/aplicacionrestful-0.0.1-SNAPSHOT.jar
```

### Opción 3: Usar Maven directamente (si tienes Maven instalado)

```bash
mvn spring-boot:run
```

## Probar el servicio

Una vez que el servicio esté ejecutándose, puedes probarlo visitando:

### Saludo básico
```
GET http://localhost:8080/greeting
```

Respuesta esperada:
```json
{"id":1,"content":"Hello, World!"}
```

### Saludo personalizado
```
GET http://localhost:8080/greeting?name=SpringBoot
```

Respuesta esperada:
```json
{"id":2,"content":"Hello, SpringBoot!"}
```

### Usando curl

```bash
# Saludo básico
curl http://localhost:8080/greeting

# Saludo personalizado
curl "http://localhost:8080/greeting?name=Developer"
```

## Desarrollo

### Agregar nuevos endpoints

Para agregar nuevos endpoints REST:

1. Crea una nueva clase de controlador en el paquete `com.edu.escuelaing.aplicacionrestful`
2. Anota la clase con `@RestController`
3. Define métodos con anotaciones como `@GetMapping`, `@PostMapping`, etc.

### Ejecutar tests

```bash
mvnw.cmd test
```

## Arquitectura

### Componentes principales

- **RestServiceApplication.java**: Clase principal de la aplicación Spring Boot
- **@SpringBootApplication**: Anotación que combina:
  - `@Configuration`: Marca la clase como fuente de definiciones de beans
  - `@EnableAutoConfiguration`: Habilita la auto-configuración de Spring Boot
  - `@ComponentScan`: Escanea el paquete en busca de componentes

### Características de Spring Boot utilizadas

- **Auto-configuración**: Spring Boot configura automáticamente la aplicación
- **Servidor embebido**: Incluye Tomcat embebido, no necesita servidor externo
- **Starter Dependencies**: Dependencias predefinidas que simplifican la configuración
- **Conversión JSON automática**: Jackson convierte automáticamente objetos a JSON

## Recursos adicionales

- [Guía oficial de Spring: Building a RESTful Web Service](https://spring.io/guides/gs/rest-service)
- [Documentación de Spring Boot](https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/)
- [Guías de Spring](https://spring.io/guides)
- [Spring Academy](https://spring.academy/)

## Licencia

Este proyecto es un proyecto de demostración basado en las guías oficiales de Spring.
