# Build the app
FROM node:18 AS build
WORKDIR /app
COPY . .
ARG REACT_APP_API_BASE_URL
ARG REACT_APP_WS_BASE_URL
ENV REACT_APP_API_BASE_URL=$REACT_APP_API_BASE_URL
ENV REACT_APP_WS_BASE_URL=$REACT_APP_WS_BASE_URL
RUN npm install
RUN npm run build

# Serve with Nginx
FROM nginx:alpine
COPY --from=build /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
