# earthly

sample
```
# Earthfile
VERSION 0.7
FROM node:14

WORKDIR /app

# 依存関係のインストール
deps:
    COPY package.json package-lock.json ./
    RUN npm install

# アプリケーションのビルド
build:
    FROM +deps
    COPY . ./
    RUN npm run build

# アプリケーションのテスト
test:
    FROM +deps
    COPY . ./
    RUN npm test -- --watchAll=false
```
