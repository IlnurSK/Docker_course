FROM node:17 AS BUILD
WORKDIR /app
COPY  frontend/package.json ./package.json
RUN npm i   

COPY frontend ./
RUN npm run build

#!!!
FROM nginx

COPY --from=BUILD /app/dist/index.html /nginx/static/index.html
COPY --from=BUILD /app/dist/static/css /nginx/static/
COPY --from=BUILD /app/dist/static/js /nginx/static/