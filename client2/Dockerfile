# Builder container to compile typescript
FROM node:lts-alpine AS build
WORKDIR /usr/src/app

# Clone the Git repository
RUN git clone https://github.com/Abhi96chawla/maven-project.git /usr/src/app
# Install dependencies

RUN pwd
RUN ls -l
COPY client2/package.json .
COPY client2/package-lock.json .
RUN npm ci
 
# Copy the application source
COPY . .
# Build typescript
RUN npm run build
 
 
 
FROM nginx:stable-alpine
 
#COPY nginx.conf /etc/nginx/nginx.conf
COPY --from=build /usr/src/app/client2/index.html /usr/share/nginx/html
 
EXPOSE 8000
