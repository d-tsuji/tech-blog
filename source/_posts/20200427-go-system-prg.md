title: "Goならわかるシステムプログラミングが増刷されて初版4刷になりました"
date: 2020/04/27 10:03:55
tags:
  - Go
  - 出版
category:
  - Programming
thumbnail: /images/20200427/thumbnail.jpeg
author: "XXX"
featured: true
lede: "Goならわかるシステムプログラミングが増刷されました。増刷される場合にはたいてい誤字が修正されたりするんですが、今回12ページほど増量しております。前回の3刷でも16ページ増えたので、初版と比べると28ページ増です。写真は1刷〜4刷の比較です。"
---

Goならわかるシステムプログラミングが増刷されました。増刷される場合にはたいてい誤字が修正されたりするんですが、今回12ページほど増量しております。[前回の3刷でも16ページ増えた](http://blog.shibu.jp/article/185504106.html)ので、初版と比べると28ページ増です。写真は1刷〜4刷の比較です。

<img src="/images/20200427/photo_20200427_01.jpeg" class="img-middle-size">

なぜか、Real World HTTP 第2版の原稿の締め切りも、レビューの締め切りも、最終的な印刷所に原稿が運ばれて行くタイミングもだだ被りで、ちょっと忙しかったのですが、無事みなさまにお届けできる運びとなりました。

# 変わった内容

一番大きな変更はFUSEを使ったファイルシステムを作ろう、というネタを追加したことですね。もともとアスキーの連載から書籍版を作る時に、一度は足したいネタにリストアップはしていたのですが、実装や検証期間を考えるとちょっと手強そうだぞ、ということで落ちた内容です。[フューチャーの技術ブログでgocloud.devの紹介](https://future-architect.github.io/articles/20191111/)をしましたが、せっかくなのでこれを使って、AWS S3やらGoogle Cloud Storageをマウントとして読み込み専用でアクセスするファイルシステムを簡易実装しています。

それ以外はコラムが増えるとか、段落が増えるとか注釈が増えるとかが中心です。

TeeReaderのTeeはUNIXのteeコマンドが由来というのは知っていたけど、それはアルファベットのT由来だから、みたいな小ネタ（Qiitaの記事は消えてしまっているし、Wikipediaの説明の方を参照先としています）とか。

<blockquote class="twitter-tweet"><p lang="ja" dir="ltr">&gt; 区切り用のパイプの形がアルファベットのTに似ていることから<br><br>ｿｯﾁｶｰ (´・ω・`)<a href="https://t.co/GWMqZRXzFb">https://t.co/GWMqZRXzFb</a></p>&mdash; MURAOKA Taro (@kaoriya) <a href="https://twitter.com/kaoriya/status/1052060869780156416?ref_src=twsrc%5Etfw">October 16, 2018</a></blockquote> <script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script>

あとは、[Songmuさんの福岡の発表](https://songmu.jp/riji/entry/2019-07-16-gocon-fukuoka.html)がとてもシステムプログラミングだったので、シグナルの扱いとかいくつか引用させていただきました。``exec.CommandContext()``でタイムアウトとかキャンセルされるとSIGKILLが飛ぶんですよとか。シグナル周りでは、doi-t氏のブログエントリーの「[読了、Goならわかるシステムプログラミング: Linuxシグナル再訪 in Go](http://doi-t.hatenablog.com/entry/revisit-linux-signals-in-go)」も参照先にくわえさせていただきました。循環参照ですね。 

メモリ周りも[AlpineのDockerイメージを使うとPythonのパフォーマンスが落ちる話](https://superuser.com/questions/1219609/why-is-the-alpine-docker-image-over-50-slower-than-the-ubuntu-image)とか、メモリとパフォーマンスに関する説明をちょっと追記したりしました。あとは``sync.Pool``は``sync``パッケージではありますがスラブアロケータとかパフォーマンス改善の文脈で説明した方がよかろう、とメモリの章に移動しました。かの有名なLinuxコミッターの小崎さんが、メモリ管理のページテーブルで消費されるメモリを「天使のわけまえ」と呼んでいて、さすがオシャレだなぁ、と思って引用したり。

あとはさらに細かいところでは、ストレージがSSDに変わることでOS側の戦略が変わったところを紹介したり、/dev/urandom周りの話題をちょびちょび追加したり、[フューチャーの辻さんの発表資料](https://future-architect.github.io/articles/20191120/)を引用するなど、乱数まわりも少し追記したりしています。

# さらなる追加の章

今年は[n月刊ラムダノート](https://www.lambdanote.com/collections/frontpage/products/nmonthly-vol-2-no-1-2020)という方にも寄稿したのですが、これはもともと3刷のときに追加しようと書き始めたのですが、30ページ以上にも渡りそうで、分量が多すぎて収録を断念したコンテンツでした。本文の最初にも書いたのですが、システムプログラミングという言葉は範囲が広くて、本や説明によって多少範囲が違ったりします。OSの中、OSの外、ネイティブコードを生成するコンパイラetc。今までもOSの中についてはシステムコールの内側の実装紹介や、OSのファイルシステムやメモリの動きなどを紹介はしていましたが、主にOSのブートストラップ部分を中心に解説しています。

このn月刊ラムダノートですが、西田さんのQUICの説明はすばらしく、そのとき執筆中だったReal World HTTP第2版からも参照先としています。QUICに関する説明としては現在日本で一番詳しいと思います。

また、dRubyの記事を書かれた咳さんは、僕がホンダ時代に参加していた、とちぎRubyで一緒に勉強させていただいた、僕の方向性やら何やらにすごく影響を与えてくださったすごい人です。きちんと過去のアーキテクチャを把握して学び、それを現代の実装に生かす、しかも出来上がったものはその時の流行に左右されていないオンリーワンなもの、というdRubyのかっこよさは僕の中では未だにダントツです。今回は過去の書籍からいろいろアップデートされ、ブラウザに対してServer Sent Eventsを使った通信したり、Raspberry PiとQRコードリーダーが登場するなど、dRubyがRubyの枠を超えていてこれも必見です。

# どこで買える？

本日から、いろいろな書店とかには並んでいるようです。確実なのは[ラムダノートのウェブサイト](https://www.lambdanote.com/products/go)から購入ですね。あと、すでにラムダノートの直販サイトで購入してくださった方で、ユーザー登録している方は最新版のPDFのダウンロードができるようになっています。


----

関連記事：

* [Real World HTTP 第2版はなぜ1.5倍になったのか](https://future-architect.github.io/articles/20200421/)
* [TypeScript教育用コンテンツ公開のお知らせ](https://future-architect.github.io/articles/20190612/)
* [Go Conferenceの📛を作る](https://future-architect.github.io/articles/20191203/)