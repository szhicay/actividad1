# Construcción del proyecto con Maven
FROM maven:3.9.7-eclipse-temurin-17 AS build
# Usamos una imagen oficial de Maven con Java 17 . 
# El alias "build" permite referenciar esta etapa más adelante.

WORKDIR /app
# Define el directorio de trabajo dentro del contenedor como /app.

COPY pom.xml .
# Copia el archivo pom.xml al contenedor para descargar las dependencias

COPY src ./src
# Copia el código fuente al contenedor.

RUN mvn package -DskipTests
# Ejecuta el comando Maven para compilar el proyecto y generar el paquete .jar, 

# Imagen final para ejecutar la app (más liviana)
FROM eclipse-temurin:17-jre
# Usa una imagen base con solo el JRE de Java 17 (sin Maven) para correr la aplicación.

WORKDIR /app
# Define nuevamente el directorio de trabajo donde se copiarán los archivos compilados.

# Copia los archivos generados en la etapa de build al contenedor final.
COPY --from=build /app/target/quarkus-app/lib/ /app/lib/
COPY --from=build /app/target/quarkus-app/*.jar /app/
COPY --from=build /app/target/quarkus-app/app/ /app/app/
COPY --from=build /app/target/quarkus-app/quarkus/ /app/quarkus/

# Expone el puerto 8080, que es donde Quarkus escucha por defecto.
EXPOSE 8080
# Inicia la aplicación Java usando el jar principal generado por Quarkus.
ENTRYPOINT ["java", "-jar", "/app/quarkus-run.jar"]
*