
FROM node:16-alpine AS builder

WORKDIR /app

COPY package*.json ./

RUN npm install --legacy-peer-deps && npm cache clean --force

COPY . .

RUN npm run build --prod

FROM nginx:alpine

RUN apk add --no-cache shadow

RUN groupadd -r appgroup && useradd -r -g appgroup appuser

RUN rm -rf /usr/share/nginx/html/*

COPY --from=builder /app/dist/angular10-springboot-client /usr/share/nginx/html

RUN chown -R appuser:appgroup /usr/share/nginx/html

USER appuser

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]