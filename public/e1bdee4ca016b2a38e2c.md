---
title: Discord.js v14 botの作り方【基礎・下準備編】 (2024/5/21現在)
tags:
  - JavaScript
  - Node.js
  - discord
  - discord.js
private: false
updated_at: '2024-06-18T14:34:23+09:00'
id: e1bdee4ca016b2a38e2c
organization_url_name: null
slide: false
ignorePublish: false
---
# Discord.js とは
Discord.js (以下d.js) とは、discordのbotを開発するときに使用するパッケージの1つです。
同様に、Discord.pyというものがあります。これはpythonで開発する場合のパッケージになります。

今回は、botをプログラムするために、bot自体を作成していきます！
**※ 現時点での情報ですので、見た目などが今後変更される可能性がございます。**

# Botを開発するサーバーを作ろう
|手順|説明|備考|
|---|---|---|
|1|Discordの画面左上にある「**サーバーを追加**」をクリックします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/a466c895-9b8f-31e3-fe9d-0741c430226b.png)|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/17a3bef2-2b7c-7dfa-ec4e-28bfba00c405.png)
|2|「**オリジナルの作成**」をクリックします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/96265a89-8f39-5169-9935-10f76ceda7fc.png)|
|3|「**自分と友達のため**」をクリックします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/8df40796-4388-ad51-b341-58573f6cc977.png)|
|4|右下にある「**新規作成**」をクリックします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/17f6a8b2-5ea3-c4ca-fc91-2ab71f6ac82d.png)|

これで開発のテストや、メモなどに使用するサーバーが作成できました！

# Botを作ってみよう
Botの作成方法は、以下の通りです。
|手順|説明|備考|
|---|---|---|
|1|[Discord Developer Portal](https://discord.com/developers/applications)にアクセスします。||
|2|画面右上の「**New Application**」をクリックします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/f5e3c547-31dd-c96e-d5cd-577961a9a14d.png)|
|3|自分のbotのユーザー名を入力し、チェックボックスのチェックを入れ、青い「**Create**」ボタンをクリックします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/49f77f55-c12e-384e-d552-374100b6cd75.png)

これで、botを作成することができました！
## Botをサーバーに導入してみよう
|手順|説明|備考|
|---|---|---|
|1|Botのアカウントを作ったページの、左にあるメニューから「**OAuth2**」に移動します。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/a1a7528e-6b22-72b1-5e63-37ebd09bfc7a.png)|
|2|すこし下にスクロールして、`OAuth2 URL Generator`を見つけます。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/e25fdd24-f5d4-c451-7274-5517c17c98ea.png)|
|3|たくさんチェックボックスがありますが、「**application.commands**」と「**bot**」を選択します。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/9d097bc4-6e33-5004-1b96-b3f9a3a80ae9.png)|
|4|するともう1つたくさんのチェックボックスが出てくるので、一番左上にある「**Administrator**」にチェックを入れます。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/d74f6648-d2b0-df48-e78b-ece253ee5667.png)|
|5|すると一番下にURLが生成されますので、右の青い「**Copy**」ボタンをクリックし、リンクをコピーします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/929dcf90-52db-baff-cc0c-c71788e1cdf0.png)|
|6|discordに移動し、コピーしたリンクを貼り付け、送信します。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/4aa3df39-454e-4bff-7869-a5d436687f39.png)|
|7|送信したリンクをクリックします。||
|8|すると`アクセスを要求しています`という画面が出てくるので、右下の青い「**はい**」ボタンをクリックし、「**認証**」ボタンをクリックします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/1c861e14-6c68-14e0-6a18-d0e185d8c25c.png)|
|9|すると頭脳クイズが出てくるので、脳をフルに回転させてクイズをクリアします。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/a85c22d4-6c2d-36e2-aa38-329b3389bb5b.png)|
|10|クイズをクリアしたら、サーバーに導入することができます。|![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/3794632/b4655754-fd1f-0024-54ce-1b6e709de1e2.png)|

これで先程作ったbotを開発サーバーに導入することができました！

# 終わりに
以上でBotを作成し、テストサーバーに導入することができました！
次は[環境構築編](https://qiita.com/minoru_kinugasa/items/9e40ede6e8ee3cfb7d43)をごらんください！
