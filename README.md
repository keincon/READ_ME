
![Logo](https://scontent-nrt1-1.xx.fbcdn.net/v/t39.30808-6/336496830_895864821713758_6061715320632767707_n.jpg?_nc_cat=101&ccb=1-7&_nc_sid=5f2048&_nc_ohc=JlhHotflTAcAX9WbBk8&_nc_ht=scontent-nrt1-1.xx&oh=00_AfDabnqnZzo4xFgosH0rMkXfSBuleYN__YXwg7Jy9_smjA&oe=65F89E80)


# Composerで新しいライブリの使い方

こちらは　新しいライブリのインストール仕方になります。

## 準備するもの

#### 準備したいもののリストになります。 
```
 PHP 「インストール済みは条件」
 Composer
```
## Composer のインストールする方法
Step 1
最初に　システムENVを変更します。
システムENV　で　http_proxy　と　https_proxy の値を入れます。
```bash
  http://172.26.67.100:80
```

[![](https://github.com/keincon/READ_ME/blob/main/composer_images/ENV1.PNG)]

[![](https://github.com/keincon/READ_ME/blob/main/composer_images/ENV.PNG)]

Step 2
そして ComposerのURLでComposerをダウンロードします。
ここで　Composer-Setup.exe を　クリックします。
```bash
  https://getcomposer.org/download/
```
[![](https://github.com/keincon/READ_ME/blob/main/composer_images/Composer_WEB.PNG)]

Step 3
Composer-Setup.exe を開けます
そして Composerを以下の画像通りにインストールします。
[![](https://github.com/keincon/READ_ME/blob/main/composer_images/Composer_Install1.PNG)]

[![](https://github.com/keincon/READ_ME/blob/main/composer_images/Composer_Install2.PNG)]

[![](https://github.com/keincon/READ_ME/blob/main/composer_images/Composer_Install3.PNG)]

[![](https://github.com/keincon/READ_ME/blob/main/composer_images/Composer_Install4.PNG)]

##Composerでライブリをインストールします。
Step 1
最初に　自分のプロジェクトでcomposer.jsonやcomposer.lockが　ある　フォルダを探します。
[![](https://github.com/keincon/READ_ME/blob/main/composer_images/composer_dir.PNG)]

Step 2
そこまでCMDで移動します。
```bash
  cd [Folder]
```
[![](https://github.com/keincon/READ_ME/blob/main/composer_images/ComposerCMD.PNG)]


Step 3
自分がインストールしたい　ライブリをインストールします。
ここで　私は　LaravelのDDというライブリをインストールしたいので　インストールします。
```bash
  https://packagist.org/packages/larapack/dd
```

コマンドを押します。
```bash
  composer require larapack/dd 1.*
```
何もエラー出なかったらライブリインストールしました。
[![](https://github.com/keincon/READ_ME/blob/main/composer_images/Composer_cmd2.PNG)]


##Composerでインストールしたライブリをプロジェクトに入れます。
自分のプロジェクトの index.php まで　行きます。
そこで　先ほど　Composerがある場所を　requireで以下のように参考します。
```bash
  require('../../_codeigniter/composer/vendor/autoload.php');
```
[![](https://github.com/keincon/READ_ME/blob/main/composer_images/PJ_Index.PNG)]


これでライブリを使えるようになりました。


## Authors

- [@Kein Pyi Si[ケインピィーシー]](https://www.github.com/keincon)
- [@Takehara[竹原]](https://github.com/ascon-takehara-2021)

