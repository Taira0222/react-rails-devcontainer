ARG VARIANT=3.4-bookworm 
FROM mcr.microsoft.com/vscode/devcontainers/ruby:${VARIANT}

ARG NODE_VERSION="24"
RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"

# コンテナ内の/usr/local/bundleにbundlerをインストール。
# /usr/local/bundle内にgemの内容が入る
ARG BUNDLER_VERSION='2.6.8'
RUN gem install bundler -v ${BUNDLER_VERSION}
ENV BUNDLE_PATH='/usr/local/bundle'

# Install Rails
ARG RAILS_VERSIONS='8.0.2'
RUN gem install rails -v ${RAILS_VERSIONS}
RUN gem install ruby-lsp

# psql コマンドインストール
RUN apt-get update && apt-get install -y postgresql-client

# 上記のRUNコマンドを コンテナ内の/appで実行する
WORKDIR /app



# # Railsプロジェクトの依存ファイルだけを先にコピー
# COPY Gemfile* ./
# RUN bundle install

# # アプリ全体をコピー
# COPY . .

# # 必要ならportを公開（例: 3000）
# EXPOSE 3000