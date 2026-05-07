# SpotESIfy API — Dockerfile
FROM node:20-alpine

WORKDIR /app

RUN apk add --no-cache curl 

COPY package*.json ./
RUN npm install --only=production

COPY . .

RUN addgroup -S spotesify && adduser -S spotesify -G spotesify && \
    chown -R spotesify:spotesify /app

USER spotesify

EXPOSE 5000

HEALTHCHECK --interval=10s --timeout=3s --retries=3 \
  CMD curl -f http://localhost:5000/api/health || exit 1

CMD ["npm", "start"]
