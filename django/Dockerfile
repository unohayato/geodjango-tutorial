FROM python:3.11-slim

ENV PYTHONUNBUFFERED 1

# 作業ディレクトリを設定
WORKDIR /code

# 依存関係ファイルをコピー
COPY ./requirements.txt /code/

# 必要なパッケージと依存関係をインストール
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
        unzip \
        wget \
        binutils \
        libproj-dev \
        gdal-bin \
        libgdal-dev \
        libgeos-dev \
        postgresql \
        postgresql-contrib \
        postgis && \
    pip install --upgrade pip && \
    pip install -r requirements.txt && \
    apt-get purge -y --auto-remove && \
    rm -rf /var/lib/apt/lists/*

# GDALライブラリのパスを設定 (このパスはインストールされたGDALバージョンによって異なる場合がある)
ENV GDAL_LIBRARY_PATH /usr/lib/libgdal.so

# プロジェクトファイルをコピー
COPY . /code/
