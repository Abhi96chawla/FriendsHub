# Builder container to compile typescript
FROM node:18-alpine AS build
WORKDIR /app/react-app

# Clone the Git repository
#RUN git clone https://github.com/Abhi96chawla/maven-project.git /usr/src/app
# Install dependencies

RUN pwd
RUN ls -l
COPY package.json .
#COPY package-lock.json .
RUN npm install
 
# Copy the application source
COPY . .
RUN npm run build 
RUN ls -al
 
#FROM nginx:stable-alpine
FROM node:18-alpine as prod
WORKDIR /app/react-app

COPY --from=build /usr/src/app .
#COPY --from=build /app/react-app/dist/ /app/react-app/dist/
 
EXPOSE 8000
COPY package.json .
COPY vite.config.ts .
CMD [ "npm", "run", "preview" ]
