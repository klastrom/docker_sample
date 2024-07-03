
## 環境構築

```bash
# Docker イメージのビルド
docker-compose build

# Docker コンテナの起動
docker-compose up -d

# Docker コンテナの停止・削除
docker-compose down
```

```bash
# PHPStan でコードのバグを検知する
composer phpstan

# PHP_CodeSniffer でコーディング規約に準拠していないコードを検知する
composer phpcs
```
