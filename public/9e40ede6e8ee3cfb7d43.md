---
title: Discord.js v14 botの作り方【基礎・環境構築編】 (2024/5/21現在)
tags:
  - JavaScript
  - Node.js
  - discord
  - discord.js
private: false
updated_at: '2024-05-21T16:20:04+09:00'
id: 9e40ede6e8ee3cfb7d43
organization_url_name: null
slide: false
ignorePublish: false
---
# Discord.js とは
Discord.js (以下d.js) とは、discordのbotを開発するときに使用するパッケージの1つです。
同様に、Discord.pyというものがあります。これはpythonで開発する場合のパッケージになります。
詳しくは[こちら](https://qiita.com/minoru_kinugasa/items/e1bdee4ca016b2a38e2c)をごらんください！

# 環境構築とは
discord.jsというパッケージをインストールする`npm`と、
discord.jsを実行する`Node.js`をインストールしなければ、botを開発したり、動かしたりすることができません。

そのための環境を作り、開発や実行を行える状況にすることを`環境構築`といいます。

# インストール方法
:::note warn
Node.jsのインストール方法は頻繁に変更される可能性がございます。
現時点でのインストール方法を記載しますが、できない場合は`Node.js install`などとググったほうが早いと思われます。
:::
|手順|説明|備考|
|---|---|---|
|1|[https://nodejs.org/en/download/package-manager](https://nodejs.org/en/download/package-manager)にアクセスします。||
|2|真ん中のメニューにて、自分のPCのOSを選択します。[^1]|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/cb1c0ec0-c797-4a4e-c5f8-d707a00abf43.png)|
|3|表の右下にある「**Copy to clipboard**」ボタンをクリックします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/e70bd925-11d5-58a8-a12c-6b6d3f690f0d.png)|
|4|ターミナルまたはコマンドプロンプトを開きます。 (以下ターミナル) [^2]|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/9c4a5ef4-4371-fbd8-7dfe-68dcf47deca9.png)|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/20f83506-f2b2-c379-40f3-898ca2e28735.png)|
|5|ターミナルに先ほどコピーしたものを`Command + V`または`Ctrl + V`でペーストします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/d0a23a19-6aac-b2d1-fe35-daf18ed6d90e.png)|
|6|貼り付けたものを実行するため、`Enter`を押します。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/d84f5950-3c56-9c4e-73ff-f57603a22031.png)|

これでインストールすることができました！
インストールできたかどうかの確認には、以下のコマンドを実行します。
|Node.jsの確認|npmの確認|
|---|---|
|`node -v`| `npm -v`|
|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/e67b5df4-60c7-cde2-3baa-929587a35c46.png)|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/4ec08597-137f-9f68-c424-e75bda26f01e.png)|

このように、バージョンが出てきたら正しくインストールできています。
バージョンではなく、`zsh: command not found: node`や`zsh: command not found: npm`などが出てきた場合はインストールすることができていません。
もう一度やり直すか、別の記事をごらんください(-_-;)

[^1]: OSがわからなくても、すでに自分自身のOSが適用されている場合がおおいです。
[^2]: Windowsの場合は、スタートキーを押して、`cmd`と入力、`Enter`を押します。
Macの場合は、`Command + スペース`を押してターミナルと入力、`Enter`を押します。

# 終わりに
これで環境構築編は完了です！環境構築に関しては、バージョン、OSとの互換性など色々なものが絡まってきてしまい、この記事ではリアルタイムの情報を書ききることが難しいので、できなかった方はご自身で調べてみてください！

次は[ワークスペース作成編](https://qiita.com/minoru_kinugasa/items/ea3d193562ec27b6f9c2)となります！
botの開発をするファイルやフォルダなどの準備や、パッケージのインストールを行いますのでぜひごらんください！
