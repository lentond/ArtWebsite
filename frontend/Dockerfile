# pull official base image for running React apps
FROM node:13.12.0-alpine

# set working directory
WORKDIR /app

# Add `/app/node_modules/.bin` to $PATH so those dependencies can be accessed.
ENV PATH /app/node_modules/.bin:$PATH

# install app dependencies
COPY package.json ./
COPY package-lock.json ./
RUN npm install --silent
RUN npm install react-scripts@3.4.1 -g --silent

# Copy local react app into downloaded image
COPY . ./

# Expose local port 3000 for running frontend
EXPOSE 3000

# Start app
CMD ["npm", "start"]

