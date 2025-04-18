# ベースイメージとして、Python 3.9 を含む軽量な Debian ベースの公式イメージを使用します
FROM python:3.9-slim-buster

# 作業ディレクトリを /app に設定します
WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 5000

CMD ["python", "app.py", "--host=0.0.0.0", "--port=5000"]
