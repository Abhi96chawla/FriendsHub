# Builder container to compile typescript
FROM node:lts-alpine AS build
WORKDIR /usr/src/app

# Clone the Git repository
#RUN git clone https://github.com/Abhi96chawla/maven-project.git /usr/src/app
# Install dependencies

RUN pwd
RUN ls -l
COPY package.json .
COPY package-lock.json .
RUN npm install
 
# Copy the application source
COPY . .
# Build typescript
#RUN npm run build
 
 RUN ls -al
 
#FROM nginx:stable-alpine
FROM node:carbon-alpine
WORKDIR /usr/src/app

COPY --from=build /usr/src/app .
#COPY --from=build /usr/src/app/index.html /usr/share/nginx/html
 
EXPOSE 8000
CMD [ "npm", "start" ]
