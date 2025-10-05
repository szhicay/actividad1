# Usa una imagen oficial de Node.js
FROM node:18-alpine

# Define el directorio de trabajo dentro del contenedor
WORKDIR /usr/src/app

# Copia los archivos de dependencias (package.json y package-lock.json)
COPY package*.json ./

# Instala las dependencias del proyecto definidas en package.json
RUN npm install

# Copia el resto del código fuente de la aplicación al contenedor
COPY . .

# Expone el puerto 3000, el que usará la aplicación Node.js dentro del contenedor
EXPOSE 3000

# Define el comando por defecto que se ejecutará al iniciar el contenedor
# Aquí ejecuta "npm start" 
CMD ["npm", "start"]