# earthly

This repository contains a sample React application, built and tested using Earthly.

## Prerequisites

- [Node.js](https://nodejs.org/)
- [Earthly](https://earthly.dev/)

## Setup

1. Clone the repository:

   ```bash
   cd ~/git/sample/earthly
   ```

   ```bash
   git clone [your-repository-url]
   cd earthly/client
   ```

2. Install the dependencies:
   ```bash
   npm install
   ```

## Building with Earthly

To build the application using Earthly, run:

```bash
earthly +build
```

## Testing with Earthly

To test the application using Earthly, run:

```bash
earthly +test
```

## Sample Earthfile
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
