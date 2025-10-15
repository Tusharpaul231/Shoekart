FROM node:18-alpine AS builder

WORKDIR /app

ARG VITE_BACKEND_URL
ENV VITE_BACKEND_URL=http://localhost:5000

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

FROM nginx:alpine

COPY --from=builder /app/dist /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]