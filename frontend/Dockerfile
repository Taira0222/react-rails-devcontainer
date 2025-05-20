FROM node:20
WORKDIR /app

# --- 本番/CI/CD環境向けのファイルコピーについて ---
# 
# 下記のCOPY命令は、GitHub Actionsや本番環境など
# Docker Engine上でコンテナイメージをビルドする場合に必要です。
#
# ローカル開発時にはdocker-composeのvolumesで
# ./frontendディレクトリをコンテナの/appにマウントしているため
# このCOPY命令の有無は影響しませんが、
# 
# 本番やCI環境ではマウントせず「イメージ単体でコンテナを起動」するため、
# 事前にアプリ本体（frontend配下の全ファイル）を
# Dockerイメージ内の/appにパッケージしておく必要があります。
#
# これにより、どの環境でも同じ状態でアプリが再現可能となります。
#
# COPY package*.json ./
# RUN npm install
# COPY . .

