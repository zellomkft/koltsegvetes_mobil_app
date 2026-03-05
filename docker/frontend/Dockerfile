FROM node:20-bullseye

WORKDIR /app

#  React Native DevTools futtatásához szükséges csomagok
RUN apt-get update && apt-get install -y \
    libnspr4 \
    libnss3 \
    libatk1.0-0 \
    libatk-bridge2.0-0 \
    libgtk-3-0 \
    libx11-xcb1 \
    libxcomposite1 \
    libxcursor1 \
    libxdamage1 \
    libxrandr2 \
    libasound2 \
    libpangocairo-1.0-0 \
    libxss1 \
    libxtst6 \
    libgbm1 \
    libglib2.0-0 \
 && rm -rf /var/lib/apt/lists/*

COPY frontend/package*.json ./

RUN npm install

COPY frontend/. .

CMD ["npm", "run", "start"]