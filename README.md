# deploy-laravel-vue-sharehost
```
name: Deploy to cPanel

on:
  push:
    branches:
      - main

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Remove old build folder 🗑️
        run: rm -rf ./public/build

      - name: Checkout Code 🚚
        uses: actions/checkout@v3

      # - name: Install Dependencies 📦
      #   run: npm install

      # - name: Build React App / Vue App (depending on user app) 🏗️
      #   run: npm run build

      - name: Upload to cPanel 📂
        uses: SamKirkland/FTP-Deploy-Action@v4.3.4
        with:
          server: ${{ secrets.FTP_SERVER }}
          username: ${{ secrets.FTP_USERNAME }}
          password: ${{ secrets.FTP_PASSWORD }}
          server-dir: ./
          exclude: |
            **/.git**
            **/.git*/**
            **/node_modules/**
            **/.**
```
