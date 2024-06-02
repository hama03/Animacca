# Docker手順書

## 手順

1. docker-compose.ymlを作る
2. docker-composeでビルドとアップをして立ち上げる

---

## 1. docker-compose.ymlを入れる

以下のコードを「docker-compose.yml」としてファイルを作成する  
※場所は作成したディレクトリ直下

```docker-compose.yml

version: '3.1'

services:
  web:
    build: ./team_tiger_docker_web
    ports:
      - "3000:3000"
    volumes:
      - ./team_tiger_docker_web:/app
      - node_modules:/app/node_modules
    command: sh -c "npm run dev"
    networks:
      - my_network

  api:
    build: ./team_tiger_docker_api
    ports:
      - "3001:3001"
    volumes:
      - ./team_tiger_docker_api:/rails
    command: bundle exec rails s -p 3001 -b '0.0.0.0'
    depends_on:
      - db
    environment:
      - DATABASE_PASSWORD=root
      - SECRET_KEY_BASE=secret
    networks:
      - my_network

  db:
    image: postgres:14.0
    environment:
      - POSTGRES_PASSWORD=root
    volumes:
      - animecca_db:/var/lib/postgresql/data
    networks:
      - my_network

networks:
  my_network:
    driver: bridge

volumes:
  node_modules:
  animecca_db:

```

## 2. docker-composeでビルドとアップをして立ち上げる

1. ```docker compose build```でイメージを作成  
2. ```docker compose up```でイメージから環境を立ち上げて下さい

## 問題点

- dockerでデータベースを作成したがrailsとの連携が取れていません
