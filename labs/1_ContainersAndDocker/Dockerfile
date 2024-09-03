# FROM: use the official Node.js image from the Docker Hub, specifically version 9.4.0 on Alpine Linux
FROM node:9.4.0-alpine

# COPY: copy the application file app.js to our image
COPY app.js .

# Copy the package.json file to the working directory in the container
COPY package.json .

# RUN: instruction executes commands
# Install the dependencies specified in package.json
# Then update and upgrade the Alpine package manager (apk)
RUN npm install &&\
    apk update &&\
    apk upgrade

# Expose port 8080 to allow external access to the application
EXPOSE 8080

# Define the command to run the application 
# The CMD instruction provides a default for executing a container, or in other words, an executable that should run in your container.

CMD node app.js
# CMD ["node", "app.js"]