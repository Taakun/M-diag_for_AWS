# 音楽診断アプリ「M-diag」
こちらは[Sakulabハッカソン2022の作品](https://github.com/Taakun/M-diag)の改良版です。  

## 改良点
バックエンドの処理において、flaskでの処理をやめて、データベースを追加し、AWS Lambdaで処理を行うようにしました。  
いいね機能を追加しました。  
いいね数のランキングを表示する機能を追加しました。

## 作品紹介
音楽診断アプリ「M-diag」は、簡単な質問に答えるだけで、あなたにぴったりの音楽を紹介してくれます!  
また、似た音楽を検索する機能や、音楽を数値で可視化する機能など、様々な機能もあるので、必ずあなたに合う音楽が見つかるでしょう!  
<img src="https://user-images.githubusercontent.com/106829693/197347769-9f5c0dfa-d972-4c8a-9009-934e92beb7a6.png" width="500">  
「M-diag」は[こちら](http://m-diag.com.s3-website-ap-northeast-1.amazonaws.com/index.html)  

## 作品の各種機能の説明
1. 質問による音楽診断  
6つの質問から、最も適した音楽を診断します。  
2. 類似した楽曲を診断する機能  
事前にクラスタリングした楽曲データから、同じクラスの楽曲をおすすめします。  
3. 特定の数値に最も近い楽曲を診断する機能  
指定した数値に最も近い楽曲をおすすめします。  
4. いいね数ランキング  
いいね数をランキング形式で表示します。  
5. レーダーチャートの表示  
楽曲の数値を基にレーダーチャートで表示します。

## ディレクトリの大まかな説明
・音楽診断用プログラム  
「音楽診断用データ.ipynb」と「spotify_apiの分析.ipynb」があり、それぞれ楽曲のデータを取得したり、分析したりするのに使用しました。  
楽曲データはSpotifyのAPIを用いて取得しました。  
・html, css  
webページを表示するために使用したhtmlとcssのファイルがあります。  
・music_data  
SpotifyのAPIを用いて取得した楽曲データが入っています。  
ここでは、「洋楽」「邦楽」「ボカロ」の3種類のデータがあります。  
・Lambda_function.ipynb  
バックエンドでの処理を行うのに使用したLambda関数をまとめたファイルです。

## webアプリケーションの技術的な内容
1. フロントエンドの処理  
html,css,javascriptで記述しました。  
ajax通信を用いてLambdaを処理するAPIを実行しました。これにより、データのやりとりを実現しています。  
2. バックエンドの処理  
AWSのdynamoDBに音楽データを格納し、Lambdaを用いてデータの処理を行っています。  
3. 全体的な構造  
s3にhtml,cssを入れて、静的ホスティングを実現しています。  
<img src="https://github.com/Taakun/M-diag_for_AWS/assets/106829693/8c12c559-9881-4e5a-be38-3f756e1d3851" width="500">

## pythonのバージョン
Python 3.10.1

## 取得した楽曲に関して
spotifyのapiから取得した楽曲は以下の通りです。

・現状の楽曲数と取得したプレイリストの情報  
<洋楽>  
https://open.spotify.com/playlist/1eBroudkoPFjKfBSl6m0q9?si=f8f863723c8c4af2  
https://open.spotify.com/playlist/4HSDhmLju8RKGFxMpr7JOQ?si=03f7f43f98254bd2  
187曲  
<邦楽>  
https://open.spotify.com/playlist/7s6EDeIROFUDWpg7xdzcvQ?si=f6c6da5fa3bc4959  
https://open.spotify.com/playlist/53Opp1EdwfHij4PVHIW16F?si=c434fb6d74ae4e68  
https://open.spotify.com/playlist/7bZGTIrO8XVJFqNFR1BHez?si=01240e12f3f94585  
391曲  
<ボカロ>  
https://open.spotify.com/playlist/4zg739VKrRbD5z3Xj4yjgz?si=8147f91f206e40f3  
https://open.spotify.com/playlist/2nZdwEso65CYx84J0h2urc?si=b14a1ed243c744a2  
https://open.spotify.com/playlist/7phdTgX9Bq19f1nqutnc6o?si=dc782acaab1c4ae8  
149曲  

## 参考文献
1. spotifyのapiの取得には、以下を参考  
https://knowledge.insight-lab.co.jp/sisense/information/spotify_music_data_1

2. AWSのLambdaを用いたdynamoDBの処理方法について、Lambdaをwebアプリで実行する方法については、以下を参考
[AWS API GatewayとLambdaでDynamoDB操作](https://business.ntt-east.co.jp/content/cloudsolution/column-try-20.html)  
[サーバレスな静的ウェブサイトをイチから作ってみた。その①](https://blog.denet.co.jp/serverless_web1/)  
[【AWS】簡単なサーバーレスアプリケーションを構築する](https://zenn.dev/soshimiyamoto/articles/dcb51cbd5725e0)  
