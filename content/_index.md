---
weight: 1
bookFlatSection: true
title: "Lina's Guide to Streaming on Fedora"
---

# Lina's Guide to Streaming on Fedora

Hi, welcome to the guide! This guide is a collection of tips, recipes, and knowledge to help streamers who are using Fedora Linux. It is primarily written to help newcomers who are switching to Fedora Linux from another OS (primarily Windows). This guide particularly focuses on the [Fedora KDE Plasma Desktop](https://fedoraproject.org/kde) edition.

If you're using another distribution, or you're doing non-streaming work in the multimedia field, you will probably also find some of these tips useful.

## About me

I'm Hoshino Lina, a tech VTuber. In the past I used to work on open source GPU drivers, and now I'm focusing on developing streaming and related technology such as [Spout2PW](https://spout2pw.lina.yt). I also contribute to OBS and many other projects. My goal is to help make streaming on Linux as easy, powerful, and stable as possible. I stream some of my work on [my channel](https://lina.yt), so feel free to drop by and say hi! You can also join [my Discord](https://lina.yt/discord) if you want to chat or ask questions about Linux, we have lots of cool people who are happy to help.

## About this guide

This is an *opinionated* guide. There are many ways of doing everything on Linux, and trying to cover them all would end up being a confusing mess for newcomers. Instead, this guide focuses on the approaches I recommend, and which are closest to the setup I use. You don't have to follow everything to the letter! However, if you choose your own path, then you'll have to find your way yourself.

This is not a "how to use Linux in general" guide, but rather focuses on streaming. There is already a huge amount of general documentation and guides for working on Linux, and the [Fedora Documentation](https://docs.fedoraproject.org) is a great place to learn more about how to work with Fedora in general. This guide focuses on the niche of streaming, since it's very hard to find comprehensive information for this use case. That said, for those new to Linux and Fedora, this guide will point out tips, tricks, and basic concepts that are relevant to the rest of the guide, so newcomers don't feel lost.


# Lina による Fedora での配信ガイド

こんにちは、ガイドでようこそ！このガイドは、Fedora Linux を使用している配信者を支援するためのヒントや手法、そして知識を集めたものです。主に他の OS (主に Windows) から Fedora Linux に移行する新規ユーザーを支援するために書かれています。このガイドは特に [Fedora KDE Plasma デスクトップ](https://fedoraproject.org/kde)エディションに焦点を当てています。

別のディストリビューションを使用している場合や、マルチメディアの分野で配信以外の作業を行っている場合も、これらのヒントが役立つかもしれません。

## 私について

私は、技術系 VTuber の星乃リナと申します。以前はオープンソースの GPU ドライバの開発に携わっていましたが、現在は [Spout2PW](https://spout2pw.lina.yt) などの配信関連技術の開発に注力しています。OBS をはじめ、様々なプロジェクトにも貢献しています。Linux での配信をできるだけ簡単でパワフル、そして安定したものにすることが私の目標です。[私のチャンネル](https://lina.yt)にて配信をしているので、ぜひお気軽にお立ち寄りくださいませ！Linux についてチャットをしたり質問をしたい場合は、[私の Discord](https://lina.yt/discord) に参加してみてください。喜んでサポートしてくれる素敵な仲間たちがたくさんいますよ。

## このガイドについて

これは *個人的な* ガイドです。Linux ではあらゆることを行う方法が数多く存在し、すべてを網羅するとなると初心者にとって混乱を招く可能性があります。このガイドでは、私が推奨するアプローチと実際に使用している設定に最も近いものに焦点を当てています。すべてを忠実に行う必要はありませんよ！ただし、独自の方法を選ぶのであれば、ご自身でその方法を見つける必要があります。

これは「Linux 全般の使い方」のガイドではなく、配信に焦点を当てています。Linux での作業に関する一般的なドキュメントやガイドはすでに多く存在しており、[Fedora のドキュメント](https://docs.fedoraproject.org)は Fedora の一般的な使用方法についてさらに学ぶのに最適な場所となります。このユースに関する包括的な情報を見つけるのは非常に難易度が高いため、このガイドでは「配信」というニッチな分野にのみ焦点を当てています。とはいえ、このガイドでは Linux と Fedora を初めて使用する方のために、ガイドの残りの部分に関連するヒントやコツ、基本概念を紹介するので初心者が迷うことはないでしょう。