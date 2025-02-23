# リリース手順

## プラグインをモノレポと Packagist に登録する

新しいプラグインを作成した場合は、リリース時にモノレポの分割対象のパッケージとして登録します。  
パッケージの分割は、 master ブランチ、または、タグをプッシュした際には、GitHub Actions にて実行されますので、 
`/.github/workflow/split_monorepo.yml` を編集して登録します。

```shell
jobs:
    packages_split:
        strategy:
            matrix:
                package:
                    -
                        local_path: 'new-plugin-name'
                        split_repository: 'new-plugin-name'
```

また、新しいプラグインのリポジトリを [Packagist](https://packagist.org/packages/submit) に登録します。

## composer の設定をマージ
マージコマンドを使って、パッケージの設定をルートの composer.json にマージします。

```shell
vendor/bin/monorepo-builder merge
```

 
## VERSION.txt を更新
`VERSION.txt` の先頭行をリリースするバージョン番号に変更し、変更内容をまとめます。  
plugins/baser-core/VERSION.txt  
その後、コミットしてプッシュします。

```shell
git commit -a -m "ucmitz-5.0.0 をリリース"
```

 
## master ブランチにマージ
`dev` ブランチを `master` ブランチにマージします。

```shell
git checkout master
git merge dev-5
```

 
## リリースコマンドを実行
モノレポのリリースコマンドを実行します。  
自動的にタグを作成しプッシュします。

```shell
vendor/bin/monorepo-builder release 5.x.x
```

 
## dev ブランチにマージ
master ブランチにおいてのリリースコマンドで更新された composer.json の変更内容を、 dev ブランチにマージした上でプッシュします。
```shell
git checkout dev-5
git merge master
git push origin dev-5
```

## dev ブランチのバージョン更新
plugins/baser-core/VERSION.txt の１行目に次回リリースバージョンの開発版として変更  
例) 5.0.1 -> 5.0.2-dev  

## パッケージの作成
```shell
bin/cake create release 5.x.x
```


 
## リリース記事を作成
GitHubにて [新しいリリース記事](https://github.com/baserproject/ucmitz/releases/new) を作成します。



これでリリース作業は完了です。　
