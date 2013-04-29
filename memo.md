# サインアップ

- [http://www.heroku.com/](http://www.heroku.com/)

# Heroku Toolbelt のダウンロード＆インストール

- [https://toolbelt.heroku.com/windows](https://toolbelt.heroku.com/windows)

フルインストールすると Git までインストールされます。既に msysgit が利用可能ならカスタムインストールで「`Git and SSH`」のチェックを外しておきます。

インストール後に Heroku の bin ディレクトリに環境変数 PATH を通しておきます。

なお、一緒に ruby もインストールされますが、既に ruby がインストールされていたとしても、それとは別に追加でインストールされてしまうようです。不要であればコントロールパネルから削除してください。

# ログイン

コンソールから `heroku login` と入力します。

    heroku login
    
メールアドレスやパスワードを聞かれるので入力します。

    Enter your Heroku credentials.
    Email: adam@example.com
    Password (typing will be hidden):

続いて、次のように公開鍵の作成の確認が表示されます。自前の鍵を後で登録するので `n` とします。

    Could not find an existing public key.
    Would you like to generate one? [Yn]

公開鍵は次のように登録します。

    heroku keys:add /path/to/id_rsa.pub

known_hosts に登録するため、一旦 heroku に SSH でログインしておきましょう。

    plink git@heroku.com

次のようなエラーメッセージが表示されれば成功です。  

    FATAL ERROR: Server refused to start a shell/command

# サンプルアプリの作成

とりあえずサンプルアプリを作成してみます。GitHub からサンプルアプリをクローンします。

    git clone git://github.com/heroku/ruby-sample.git

サンプルアプリのディレクトリに移動して heroku アプリケーションを作成します。

    cd ruby-sample
    heroku create

このとき、アプリの URL とか Git の URL とかが表示されますが、後で確認できるのでメモる必要はありません。

次に Heroku の Git リポジトリにアプリをプッシュします。
`heroku create` で、作業ディレクトリに heroku というリモートリポジトリが登録されているので、次のようにプッシュ出来ます。

    git push heroku master

プッシュすると、デブロイしている感じのメッセージが流れると思います。

プッシュに成功した後、次のコマンドでアプリの URL がブラウザで開かれます。

    heroku open

上手くブラウザが立ち上がらない場合は次のコマンドで URL などが表示されます。

    heroku info

# 名前を指定してアプリケーションの作成

    heroku create redcarpet-markdown-editor --remote haroku

# 環境変数の利用

登録

    heroku config:add HOGE="abc123"

登録済みの一覧表示

    heroku config
