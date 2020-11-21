# documents

## 配信概要

- Kubernetes/Cloud Native関連のニュースや記事について視聴者/他の配信メンバーに紹介する形式で雑談していく配信
- 取り上げる記事については
  - 事前に結構読み込んだり調べたりした上で話すものもあれば
  - ちょっと面白そうだから一緒に読まない？くらいの温度感のものもあり
- という感じで紹介する内容が正しいかどうかにはこだわらず
  - こういうのがあるらしいよ
  - これ気になったので他の人のコメントが欲しい
- くらいの感じで配信メンバーの興味があったり配信メンバーが面白そうと思うことベースで雑談していく
- なので記事紹介の配信というより、雑談配信のネタとして記事やニュースを取り上げているというのに近い


## 配信について

- 基本は毎週金曜 22:00~で配信
- 金曜だと参加できない人がいる場合で土曜に変更すれば全員参加できそうな場合は土曜に変更
- ずらすのも難しい場合は金曜で配信参加可能なメンバーで配信する


## 雑談ネタの準備

- 基本配信の2日前までにネタを用意
- ネタは3人×1人3~4個用意=合計9~12くらいで収まるように調整
- ネタは https://github.com/kubernetes-internal/kubenews/brob/main/episodes/XXX/README.md にまとめる形で用意する
- それで被りとかあれば前日~配信前までに調整


## 配信で利用するツール

種別 | 利用するツール | 用途
--- | --- | ---
配信プラットホーム | YouTube | ライブ配信/動画/ライブチャット
画面構成/配信ツール | OBS | 配信用の画面構成+Youtube Liveへの配信
MTGツール | Zoom | 画面+カメラ+音声共有
SNS | Twitter | #kubenews ハッシュタグ付きで感想など
雑談ネタ置き場+α+公式サイト？ | Github | 雑談ネタ置き場+α+公式サイト？

## 配信周りの機器構成

![](https://github.com/kubernetes-internal/kubenews/blob/main/documents/streaming-overview.png)

Google Drawing: https://docs.google.com/drawings/d/1evvAtWzqhbcgnoeR16KrIy2iZjIO7sp1TbxTmJCB_5M/edit

- 配信用マシンは
  - OBS
  - Youtube Live管理
  - Youtube Live Chat
  - Zoom画面+音声共有
- のみ行い、配信マシンから直接Zoomの画面共有や音声共有は行わない
- 配信者含め画面共有やマイク音声などは別マシンからZoomにつないで行い、全てZoomを経由して情報を共有する

## 配信画面

実際の配信画面の例  
![12311231321kubenews__1_-_YouTube](https://user-images.githubusercontent.com/2158863/99866961-fc514380-2bf8-11eb-82cb-3b5d54bb120e.png)

このOBS設定については  
https://github.com/kubernetes-internal/kubenews/tree/main/OBS
においてある

![](https://github.com/kubernetes-internal/kubenews/blob/main/documents/streaming-overview.png)

YouTube LiveについてはOBSのブラウザ機能を使って表示しており  
http://css4obs.starfree.jp/  
で生成したCSSを利用している

利用している実際のCSSは  
https://github.com/kubernetes-internal/kubenews/blob/main/OBS/chat.css  
においてある

## 配信内容

基本的にはこんな感じ

種別 | 説明
--- | ---
Opening | 挨拶
_ | 配信の説明
_ | 自己紹介
_ | リアルタイム視聴のコメントはYoutube Liveコメント/感想などはTwitter #kubenews ハッシュタグ付きでツイートお願いします
メインコンテンツ | https://github.com/kubernetes-internal/kubenews/tree/main/episodes で用意したネタを中心に雑談
Ending | 来週も同じ時間にやるので良ければ見てください
_ | 良ければ高評価、チャンネル登録お願いします
_ | 締めの挨拶


