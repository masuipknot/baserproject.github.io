# REST API

## コアのAPIの有効化
baserCMSコアが提供するAPIを有効化するには、`/config/.env` の `USE_CORE_API` の値を `true` に設定します。

　
## 独自のAPIを開発する
独自のAPIを開発するには、[プレフィックス認証](./prefix_auth) を利用すると JWT認証を簡単に実装する事ができます。

　
## 管理システムからAPIへのアクセス
管理システムでは内部的にAJAXによるAPIへのアクセスを行っており、`USE_CORE_API` に関わらず、例外的にアクセスを許容します。

`USE_CORE_API` が `false` に設定されているにも関わらず、アクセスが可能となる条件は次のとおりです。

- プレフィックスが `Api` である
- 管理システムへのログインが完了している
- リファラが自身のサイトである