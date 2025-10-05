# Usa una imagen oficial de Python 3.11 
FROM python:3.11-slim
# Define el directorio de trabajo dentro del contenedor
WORKDIR /app
# Copia el archivo requirements.txt al contenedor
COPY requirements.txt .
# Instala las dependencias de Python usando pip
RUN pip install -r requirements.txt
# Copia el resto del código fuente de la aplicación al contenedor
COPY . .
# Expone el puerto 5000
EXPOSE 5000
# Define el comando por defecto que se ejecutará al iniciar el contenedor
CMD ["python", "app.py"]
