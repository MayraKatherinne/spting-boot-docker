
# Usa una imagen base con Java 20
FROM eclipse-temurin:17 AS builder

# Establece el directorio de trabajo dentro del contenedor
WORKDIR /app

# Copia el archivo JAR de tu aplicación al contenedor
COPY . .

#BUIL THE APPLICATION
RUN ./mvnw clean package -DskipTests

FROM eclipse-temurin:17

WORKDIR /app

COPY --from=builder /app/target/*.jar app.jar

# Expone el puerto si tu aplicación usa un servidor (por ejemplo, 8080 para Spring Boot)
EXPOSE 8098

ENTRYPOINT [ "java", "-jar", "app.jar" ]