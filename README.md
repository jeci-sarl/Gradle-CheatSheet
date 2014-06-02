Gradle-CheatSheet
=================

>    I found this cheat sheet looks beautiful, but I don't speak Japanese. Translation was made with translate.google.com. Any help are welcome.

Gradleのチートシートです。個人的に欲しいと思っていたのですが、見当たらなかったので試しに作ってみました。

>    It is a cheat sheet of Gradle. 

フィードバック大歓迎です。

>    Feedback are welcome.


チートシートは Sphinx で作られており、HTMLやPDFに生成することができます。
PDFの生成の際、はVLゴシックフォント( http://vlgothic.dicey.org/ )と
IPAフォント( http://ipafont.ipa.go.jp/ )を利用しています。

>    * Cheat sheet is made of Sphinx, you can generate a PDF or HTML.
>    * In the generation of PDF we use [VL Gothic font](http://vlgothic.dicey.org/)
>    * I hate [IPA font](http://ipafont.ipa.go.jp/).


PDFの生成は設定が手間だったり、OSの制約があるので、実際のPDFは以下からダウンロードできます：

>    Setting "Dattari time", because there is a limitation of the OS generation of PDF. PDF of fact can be downloaded from the following:

https://github.com/tq-jappy/Gradle-CheatSheet/raw/master/gradle-cheatsheet.pdf

## Disclaimer

内容の確認はGradle1.11で行なっています。
それ以外のバージョンではエラーになるかもしれません。

>    I have performed in Gradle1.11 to check the contents.
>    It may have errors in other versions.

## Build

このチートシート自体も Gradle でビルドできるようになっています。

ただし、Windows 以外ではビルドに失敗します（外部コマンドの実行の際に.batを指定しているため）

>    This cheat sheet itself comes to be able to build with Gradle. However it will fail to build in non-Windows OS.

以下のタスクが利用できます。

>    You  can use the following tasks:

- makeHtml
- archiveHhtml
- makePdf
- install

### Generate HTML

```
gradle makeHtml
```

中では以下のSphinxのビルドバッチを実行しているだけなので、そのまま以下のコマンドでも可。

>    This is only call to the build batch of Sphinx, it can be the following command.

```
make html
```

### Generate PDF

PDFの生成にrst2pdfを使っているので、そのためのセットアップが必要です。
また、Windows以外だと設定ファイルの書き換えが必要です。

>    Because I use the rst2pdf to generate the PDF, you must have set up for that.
>    Also, you should rewrite the configuration file in non-Windows.

1. Windows版 PIL をインストール
  http://www.pythonware.com/products/pil/
2. rst2pdf をインストール
```
easy_install rst2pdf
```
3. VLゴシックフォント(http://dicey.org/vlgothic/) を :file:`C:\Windows\Fonts` にインストール


>    1. Install the Windows version of PIL  
>       http://www.pythonware.com/products/pil/
>    2. Install the rst2pdf
>  ```
>  easy_install rst2pdf
>  ```
>    3. VL Gothic font (http://dicey.org/vlgothic/): Install to `C:\Windows\Fonts`

セットアップ後は下記コマンドで PDF が生成できます。

>    After setup, you can generate a PDF in the following command.

```
gradle makePdf
```

または普通に

>    Or normally

```
make pdf
```

### Install the Maven local repository

ZipでアーカイブしたHTMLファイルとPDFをMavenのローカルリポジトリにインストールします。

>    It will be installed on local Maven repository the HTML and PDF archived files in Zip.

```
gradle install
```

## Change history

### 1.0.0

- First edition
