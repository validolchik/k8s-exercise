FROM node:alpine

# Create app directory
WORKDIR /usr/src/app

# Install app dependecies
COPY package*.json ./

RUN npm install

# Building (for production)
# RUN npm ci --only=production

# Bundle app source
COPY . .

EXPOSE 3000

# HEALTHCHECK --interval=2m --timeout=30s --start-period=15s \
#   CMD curl -f --retry 6 --max-time 5 --retry-delay 15 --retry-max-time 60 "http://localhost:3000/health" || bash -c 'kill -s 15 -1 && (sleep 10; kill -s 9 -1)'

# HEALTHCHECK --interval=20s --timeout=5s --start-period=15s \
#    CMD curl -f localhost:3000/health || bash -c 'kill -s 15 -1 && (sleep 10; kill -s 9 -1)'

HEALTHCHECK --interval=5s --timeout=2s --start-period=15s CMD curl -f localhost:3000/health

# RUN npm start
CMD [ "node", "index.js"]
