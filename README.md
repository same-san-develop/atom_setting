## TL;DR
Atom の設定を丸ごとバックアップし、異なるマシンでもいつもの環境ですぐに作業できるようにする手順。  
`sync-settings` を利用する。

## sync-settings のインストール
バックアップの取得・復元、いずれの場合も `sync-settings` をまずインストールする必要がある。  
（Atom本体のインストールも完了していること）
```sh
$ apm install sync-settings
```

## バックアップ取得手順
### （初回のみ）トークン生成とGistページ作成
`sync-settings` は、 `Personal access token` を使用して、 `Gist` へバックアップ内容をアップロードする。  
そのため、まずはGitHub上で、`Personal access token` とアップロード先のGistを一意に特定する `Gist ID` を作成する必要がある。

#### トークンの生成
- 下記の順番にアクセスする
  - `Setting` >  `Developer settings` > `Personal access tokens` > `Generate New Token`
- 次の通り、入力・選択する
  - Note: `Atom sync-settings` と入力
  - Select scopes: `gist` にチェックを入れる
  - `Generate Token` をクリックする
- トークン生成され、画面上表示される。このトークンは二度と表示することはできないので、確実に控えておくこと。

#### Gistページの生成
https://gist.github.com/ にアクセスし、 バックアップ用のGistを作成する。
タイトル、本文は何でもよい。  
作成が完了したら、URLから `Gist ID` を取得する。URL規則は以下の通り。
```
https://gist.github.com/{GitLab ID}/{Gist ID}
```


### Atom上でバックアップ作成
Atom上で `設定` > `パッケージ` > `sync-setting`とアクセスし、次の3点を入力する。
- `Personal Access Token`
- `Gist ID`
- `Gist Description`

次の3点が完了したら、次の通りにクリックすると、設定のバックアップが作成される。
- `ステータスバー` > `パッケージ` > `Synchronize settings` > `Backup`

## バックアップ復元手順
次の通りにクリックすると、バックアップから設定が復元される。
- `ステータスバー` > `パッケージ` > `Synchronize settings` > `Restore`
