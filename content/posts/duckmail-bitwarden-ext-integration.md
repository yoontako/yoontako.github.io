---
title: "【拡張機能】 BitwardenでDuckDuckGoのランダムメール生成"
date: 2023-05-08T21:20:26+09:00
thumbnail: "images/duckduckgo_email_protection.png"
tags: ["セキュリティ", "拡張機能"]
---

パスワード管理ソフトは無料有料問わず様々なものがありますが、
私は無料かつオープンソースで有名な[Bitwarden](https://bitwarden.com/)を使っています。

そして、メールアドレス転送サービスは[DuckDuckGo Email Protection](https://duckduckgo.com/email/)を使っています。
これにより、ランダムなメールアドレスを DuckDuckGo で生成して使用することで、
データ侵害が発生した時にも無事でいられるような構成になっています。

DuckDuckGo Email Protection で生成した duck アドレスを Bitwarden に保存することになりますが、
こうしていると、例えばアカウントを作成するときに **Bitwarden の拡張機能の中で duck アドレスを生成したくなります**。

このやり方についてご紹介します。

## 1. DuckDuckGo Email Protection に登録・ログインする

[DuckDuckGo Email Protection](https://duckduckgo.com/email/)の指示にしたがって
登録・ログインしてください。

{{< img src="/images/duckduckgo_email_protection_screen.png" alt="ログイン画面" w="1000" h="400" >}}

## 2. API の Token を取得する

ログインしたら、右クリックから「検証」を開きます。

「Network」または「ネットワーク」タブを開いてください。

{{< img src="/images/ddgep-step-1.png" alt="" w="1000" h="400" >}}

その後、青色の「Generate Private Duck Address」をクリック。

{{< img src="/images/ddgep-step-2.png" alt="" w="1000" h="400" >}}

ネットワークタブに、2 つの通信が発生していることが確認できます。

メソッドが「POST」のものをクリックして開きます。

{{< img src="/images/ddgep-step-3.png" alt="" w="1000" h="400" >}}

またその右側に色々表示されます。その中の「Request Headers」または「要求ヘッダー」があります。
この一覧の中の、`Authorization: Bearer xxxxx...`を探します。

この xxxxx...の部分がごちゃごちゃした英数字のコードになっていますが、これをコピーしておきます。
このコードが API の Token になります。

{{< img src="/images/ddgep-step-4.png" alt="" w="1000" h="400" >}}

## 3. Bitwarden 拡張機能に設定

拡張機能の下ナビゲーションバーから「パス生成」を開き、
「ユーザー名」を選択、オプションは「転送されたメールアドレス」に設定します。

{{< img src="/images/ddgep-step-5.png" alt="" w="300" h="300" >}}

下にスクロールして、サービスを「DuckDuckGo」に選択し、
先ほどコピーした API を入力します。

{{< img src="/images/ddgep-step-6.png" alt="" w="1000" h="300" >}}

これで、メールアドレス生成に Bitwarden 拡張機能のみで対応できるようになりました。

## セキュリティはシンプルに

この設定をすることで、シームレスにランダムアドレスが生成でき、セキュリティも簡単に確保できます。

DuckDuckGo だけでなく、SimpleLogin や FastMail の転送サービスも使用できるようなので、
これらのサービスを使用している方はぜひ設定してみてください。

参考:
https://bitwarden.com/help/generator
