# テーマ用初期データダウンロード

設置済のbaserCMSに登録されているデータを元に、テーマ内に梱包できる初期データを生成しダウンロードする機能です。

固定ページのデータや、コンテンツ管理機能を利用してメニューなどが登録された前提のテーマを作成する場合や、制作会社の立場で、お客様向けに何度もbaserCMSを納品する際、いつも同じ設定を行うのであれば、自社の雛形としても有効利用する事ができます。

ダウンロードデータは、CSVファイルとして作成され、「default」というフォルダにパッケージングされますので、解凍してできたフォルダを次のパスに保存します。

また、default の名称を変更する事で複数セット梱包する事ができます。

```shell
/plugins/{YourThemeName}/config/data/default/
```

テーマ用初期データダウンロードは、テーマ管理のサブメニューより利用する事ができます。
