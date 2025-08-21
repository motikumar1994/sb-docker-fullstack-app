FROM node:16-alpine AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build  # <-- just this line, no extra flags

FROM nginx:alpine
COPY --from=builder /app/dist/angular10-springboot-client /usr/share/nginx/html

EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
