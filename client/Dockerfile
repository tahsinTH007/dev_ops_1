FROM node:20-alpine

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

# Vite bakes this into the bundle at build time, and .dockerignore strips .env,
# so it must be supplied here. Override for non-local targets with:
#   docker build --build-arg VITE_API_URL=https://api.example.com/api .
ARG VITE_API_URL=http://localhost:5000/api
ENV VITE_API_URL=$VITE_API_URL

RUN npm run build

EXPOSE 5173
CMD [ "npm", "run", "preview" ]
