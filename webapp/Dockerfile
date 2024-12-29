# debian:bookworm-slim をベースイメージとして使用
FROM nginx:1.26

# 必要なパッケージをインストールして alp をダウンロード & 解凍
RUN apt-get update \
  && apt-get install -y --no-install-recommends \
     curl \
     tar \
  # ▼ arm64 用バイナリを取得 (バージョンは適宜最新を確認)
  && curl -sL https://github.com/tkuchiki/alp/releases/download/v1.0.21/alp_linux_arm64.tar.gz \
     -o /tmp/alp_linux_arm64.tar.gz \
  && tar xzf /tmp/alp_linux_arm64.tar.gz -C /usr/local/bin/ alp \
  && chmod +x /usr/local/bin/alp \
  && rm -rf /var/lib/apt/lists/* /tmp/*
RUN alp --version

# デフォルトの CMD を nginx のデーモンオフに変更
CMD ["nginx", "-g", "daemon off;"]