
![Logo](https://github.com/Ascon-Dev/omisemiyell/blob/develop/src/common/img/app_logo_local.png?raw=true)


# お店みえーる 
[![en](https://img.shields.io/badge/lang-en-red.svg)](https://github.com/Ascon-Dev/omisemiyell/raw/readme/README_en.md)
[![jpn](https://img.shields.io/badge/lang-jpn-green.svg)](https://github.com/Ascon-Dev/omisemiyell/raw/readme/README.md)

こちらは　お店みえるの　開発環境作り仕様書になります。

## 準備するもの

#### 準備したいもののリストになります。 
```
 VirtualBox
 Vagrant
 Apache
 PostgreSQL
 pgAdmin4
 VSCode
 PHP 8.2
 GIT
 WinSCP
```
## VirtualBox のインストールする方法
こちらで　VirtualBoxをダウンロードください。
```bash
  https://www.virtualbox.org/
```
Step 1
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image069.png?raw=true)]

Step 2
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image078.png?raw=true)]

## Vagrant のインストールする方法
こちらで　Vagrantをダウンロードください。

```bash
  https://developer.hashicorp.com/vagrant/install?product_intent=vagrant
```
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image087.png?raw=true)]

## Vagrant の プラグイン を　インストールする方法
インストールが終わったら コマンドでプラグインをインストールします。
Step 1
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image100.png?raw=true)]
Step 2
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image107.png?raw=true)]
Step 3
こちらのコードを　入力します。
```
vagrant plugin install vagrant-proxyconf
```
```
vagrant plugin install vagrant-vbguest
```

[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image113.png?raw=true)]
## Vagrant の プラグイン を　インストールできない場合は、プロキシ設定をする
こちらのコードを　入力します。
```
set HTTP_PROXY=172.26.67.100:80
```
```
set HTTPS_PROXY=172.26.67.100:80
```
上のプロキシが動かない時に　こちらを　使います。
```
set HTTP_PROXY=http://172.26.67.100:80
```
```
set HTTPS_PROXY=http://172.26.67.100:80
```
## Vagrant の OSをインストールします。
新しいフォルダを作ります。
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image123.png?raw=true)]

そこまで　コマンドで行きます。
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image129.png?raw=true)]

そして Vagrantの設定ファイルを作ります。
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image136.png?raw=true)]

そして　ファイルを　Editorで開けます。
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image149.png?raw=true)]

そして　以下のように　Vagrant設定ファイルを編集します。
    # -*- mode: ruby -*-
    # vi: set ft=ruby :
    
    # All Vagrant configuration is done below. The "2" in Vagrant.configure
    # configures the configuration version (we support older styles for
    # backwards compatibility). Please don't change it unless you know what
    # you're doing.
    Vagrant.configure("2") do |config|
      # The most common configuration options are documented and commented below.
      # For a complete reference, please see the online documentation at
      # https://docs.vagrantup.com.
    
      # Every Vagrant development environment requires a box. You can search for
      # boxes at https://vagrantcloud.com/search.
      config.vm.box = "generic/centos9s"
    
      # Disable automatic box update checking. If you disable this, then
      # boxes will only be checked for updates when the user runs
      # `vagrant box outdated`. This is not recommended.
      # config.vm.box_check_update = false
    
      # Create a forwarded port mapping which allows access to a specific port
      # within the machine from a port on the host machine. In the example below,
      # accessing "localhost:8080" will access port 80 on the guest machine.
      # NOTE: This will enable public access to the opened port
      # config.vm.network "forwarded_port", guest: 80, host: 8080
    
      # Create a forwarded port mapping which allows access to a specific port
      # within the machine from a port on the host machine and only allow access
      # via 127.0.0.1 to disable public access
      # config.vm.network "forwarded_port", guest: 80, host: 8080, host_ip: "127.0.0.1"
    
      # Create a private network, which allows host-only access to the machine
      # using a specific IP.
      config.vm.network "private_network", ip: "192.168.33.10"
    
      # Create a public network, which generally matched to bridged network.
      # Bridged networks make the machine appear as another physical device on
      # your network.
      # config.vm.network "public_network"
    
      # Share an additional folder to the guest VM. The first argument is
      # the path on the host to the actual folder. The second argument is
      # the path on the guest to mount the folder. And the optional third
      # argument is a set of non-required options.
      config.vm.synced_folder "D:\\kein\\sourc\\src", "/var/www/html"
    
      # Disable the default share of the current code directory. Doing this
      # provides improved isolation between the vagrant box and your host
      # by making sure your Vagrantfile isn't accessible to the vagrant box.
      # If you use this you may want to enable additional shared subfolders as
      # shown above.
      # config.vm.synced_folder ".", "/vagrant", disabled: true
    
      # Provider-specific configuration so you can fine-tune various
      # backing providers for Vagrant. These expose provider-specific options.
      # Example for VirtualBox:
      #
      # config.vm.provider "virtualbox" do |vb|
      #   # Display the VirtualBox GUI when booting the machine
      #   vb.gui = true
      #
      #   # Customize the amount of memory on the VM:
      #   vb.memory = "1024"
      # end
      #
      # View the documentation for the provider you are using for more
      # information on available options.
      if Vagrant.has_plugin?("vagrant-proxyconf")
        config.proxy.http     = "http://172.26.67.100:80"
        config.proxy.https    = "http://172.26.67.100:80"
        config.proxy.no_proxy = "localhost,127.0.0.1"
      end
    
    
    
      # Enable provisioning with a shell script. Additional provisioners such as
      # Ansible, Chef, Docker, Puppet and Salt are also available. Please see the
      # documentation for more information about their specific syntax and use.
      # config.vm.provision "shell", inline: <<-SHELL
      #   apt-get update
      #   apt-get install -y apache2
      # SHELL
      if Vagrant.has_plugin?("vagrant-vbguest")
        config.vbguest.auto_update = false
      end
    	
      config.vm.box_download_insecure = true
    
    end
    
*注意　ここで　config.vm.network "private_network" とプロキシ　と　ファイルの場所 は　自分で　動くものにしてください。
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image158.png?raw=true)]

ローカルと仮想環境の共有フォルダを設定。
``` 
config.vm.synced_folder "D:\\vm\\source", "/var/www/html"
```
プロキシを設定。
``` 
  if Vagrant.has_plugin?("vagrant-proxyconf")
    config.proxy.http     = "172.26.67.100:80"
    config.proxy.https    = "172.26.67.100:80"
    config.proxy.no_proxy = "localhost,127.0.0.1"
  end

```
GuestAdditionsの自動更新をオフ。
``` 
   if Vagrant.has_plugin?("vagrant-vbguest")
    config.vbguest.auto_update = false
  end
```
SSL証明でエラーが出る場合、以下を追加。
``` 
  config.vm.box_download_insecure = true
```
そしてVagrantを動かせます
``` 
vagrant up
```
そして開発サーバーをログインをします
``` 
vagrant ssh
```

[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image167.png?raw=true)]

## 仮想環境のcentosに接続する
共有フォルダのゲストに移動し、ゲストからホストのファイルが見れるか確認する
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image172.png?raw=true)]

## もし　mountのエラーが出たら
``` 
https://qiita.com/ak-ymst/items/bdc37aaf53f857d37fcc
```
## 仮想環境でソフトウェアをインストールする
``` 
sudo yum update
```
``` 
sudo dnf -y install kernel-devel kernel-headers dkms gcc gcc-c++
```
## PHP 8.2 インストールはここ
``` 
https://computingforgeeks.com/how-to-install-php-8-2-on-centos-rhel-7/
```

## Apacheインストールはここ
``` 
https://weblabo.oscasierra.net/apache-installing-apache24-yum-centos7-1/
```
## PHP 8.2 インストールコード
```
 yum -y install httpd
 httpd -version
 sudo systemctl enable httpd.service
 sudo systemctl start httpd.service
 systemctl status httpd.service
 sudo systemctl stop firewalld
 
```
## PHP 8.2 インストールコード
``` 
sudo su
dnf update -y
dnf install -y mod_ssl dstat bind-utils traceroute telnet sysstat wget s-nail bzip2 rsync
dnf install https://rpms.remirepo.net/enterprise/remi-release-9.rpmdnf module list php
dnf module install -y php:remi-8.2
dnf install -y php-gd php-pgsql php-pdo php-pear php-soap php-devel php-pecl-zip php-intl
dnf update --enablerepo=epel,remi
dnf --enablerepo=epel install ImageMagick ImageMagick-devel
pecl install imagick
echo 'extension=imagick.so' > /etc/php.d/imagick.ini
sudo dnf install php-fpm
```
##PHPの設定

``` 
#modify disable PHP X-Powered-By
cp /etc/php.ini /etc/php.ini.back
sed -i "/^expose_php/cexpose_php = Off" /etc/php.ini
sed -i "/^post_max_size/cpost_max_size = 20M" /etc/php.ini
sed -i "/^upload_max_filesize/cupload_max_filesize = 20M" /etc/php.ini
sed -i "/^max_execution_time/cmax_execution_time = 300" /etc/php.ini

#------PHP-fpm 「PHP 8.1から下」------
cp /etc/php-fpm.d/www.conf /etc/php-fpm.d/www.conf.back
sed -i '/;request_terminate_timeout/ s/0/300/' /etc/php-fpm.d/www.conf
sed -i '/;request_terminate_timeout/ s/;//' /etc/php-fpm.d/www.conf

```


##PHPバージョン確認

``` 
php -v

```
##PostGreSQLをインストールします。

``` 
yum install postgresql-server
postgresql-setup --initdb
systemctl enable postgresql.service
systemctl start postgresql.service

```

##Apacheの設定

``` 
#------HTTPD------
cp /etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf.back
sed -i "/^#ServerName/cServerName labo.ascon.co.jp:80" /etc/httpd/conf/httpd.conf
sed -i "/^    Options Indexes FollowSymLinks$/cOptions FollowSymLinks" /etc/httpd/conf/httpd.conf
sed -i "s/AllowOverride None/AllowOverride All/g" /etc/httpd/conf/httpd.conf
sed -i "/^Options FollowSymLinks$/a <LimitExcept GET POST>\n   Order deny,allow\n   Deny from all\n</LimitExcept>" /etc/httpd/conf/httpd.conf
echo -e '\nServerTokens Prod' >> /etc/httpd/conf/httpd.conf
echo -e 'ServerSignature Off' >> /etc/httpd/conf/httpd.conf
echo -e 'TraceEnable off' >> /etc/httpd/conf/httpd.conf
echo -e 'Header unset X-Powered-By' >> /etc/httpd/conf/httpd.conf
echo -e 'Timeout 300' >> /etc/httpd/conf/httpd.conf

mv -i /etc/httpd/conf.d/autoindex.conf /etc/httpd/conf.d/autoindex.conf.org
mv -i /etc/httpd/conf.d/userdir.conf /etc/httpd/conf.d/userdir.conf.org
mv -i /etc/httpd/conf.d/welcome.conf /etc/httpd/conf.d/welcome.conf.org
touch /etc/httpd/conf.d/autoindex.conf
touch /etc/httpd/conf.d/userdir.conf
touch /etc/httpd/conf.d/welcome.conf

##AllowOverrideの設定を変える
vi /etc/httpd/conf/httpd.conf
以下の項目を変更する
AllowOverride none　→　AllowOverride All

sudo firewall-cmd --add-service=https --permanent 
sudo firewall-cmd --add-service=http --permanent
sudo vi /etc/selinux/config
...
SELINUX=disabled     ← enforcing から disabled に変更
...
#apacheの再起動
systemctl restart httpd.service
```
##PostGreSQLの設定

``` 
#PostGres セットアップ
systemctl start postgresql
systemctl enable postgresql
su - postgres
cp /var/lib/pgsql/data/postgresql.conf /var/lib/pgsql/data/postgresql.conf.bak
sed -i "/^#listen_addresses/clisten_addresses = '*'" /var/lib/pgsql/data/postgresql.conf
sed -i "/^shared_buffers/cshared_buffers = 800MB" /var/lib/pgsql/data/postgresql.conf
sed -i "/^max_connections/cmax_connections = 100" /var/lib/pgsql/data/postgresql.conf
sed -i "/^log_filename/clog_filename = 'postgresql-%Y%m%d.log'" /var/lib/pgsql/data/postgresql.conf
sed -i "/^log_line_prefix/clog_line_prefix = '[%m][%p][%u][%d] '" /var/lib/pgsql/data/postgresql.conf
cp /var/lib/pgsql/data/pg_hba.conf /var/lib/pgsql/data/pg_hba.conf.bak
echo "local    all    postgres peer" >/var/lib/pgsql/data/pg_hba.conf
echo "local    all    all  md5" >>/var/lib/pgsql/data/pg_hba.conf
echo "host    all    all    127.0.0.1/32    md5" >>/var/lib/pgsql/data/pg_hba.conf
echo "host    all    all    192.168.33.10/32    md5" >>/var/lib/pgsql/data/pg_hba.conf
echo "host    all    all    ::1/128    md5" >>/var/lib/pgsql/data/pg_hba.conf
exit
systemctl restart postgresql 
#common DB作成
su - postgres
createuser -d -P adfeeds
#(pass:dr4QHSwI)
createdb -O adfeeds adfeeds_db
psql -d adfeeds_db -c "DROP SCHEMA public CASCADE"
```
##pgAdmin4のインストール
```
rpm -i https://ftp.postgresql.org/pub/pgadmin/pgadmin4/yum/pgadmin4-redhat-repo-2-1.noarch.rpm
dnf install -y pgadmin4
/usr/pgadmin4/bin/setup-web.sh

```
##webページが正常に表示できない場合は

```
vi /etc/httpd/conf/httpd.conf

EnableSendfile On　→　EnableSendfile Off 

NSFでの外部ストレージ(Virtualboxの Synced Folder)で正しく更新を検知出来ない場合があるため
(https://tech-yjhm214.hatenablog.com/entry/vagrant-not-detect-static-file)

```
##pgAdmin4とDBを接続方法
新しいSchemaを作ってからしてください。

[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image190.png?raw=true)]

[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image191.png?raw=true)]

##GitHubアカウントを作成
```
https://qiita.com/ayatokura/items/9eabb7ae20752e6dc79d
```

アカウントを作成後、販促マネージャーのレポジトリに招待してもらう。
槇田さんか天崎さんに招待してもらう。
招待が間に合わない場合は、ツールのインストール迄でOK

##GitHubのGUIツールをインストールする
```
https://www.sourcetreeapp.com/
```
##GitHubアクセストークンの作成方法
```
https://docs.github.com/ja/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token

```
##Sourcetreeの設定
ネットワークの設定
```
ツール>オプション>ネットワーク>プロキシサーバー設定
OSデフォルトの設定を使用を選択
Git/Mercurialにプロキシサーバー設定を追加にチェックを入れる

```
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image196.png?raw=true)]

githubアカウントの追加
```
ツール>オプション>認証>追加
ホスティングサービス→GitHub
優先するプロトコル→HTTPS
認証→Basic
ユーザー名→GitHububに登録したID
パスワードを再読み込み
githubアクセストークンを入力
認証に成功したらOK
```
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image197.png?raw=true)]

リモートリポジトリ追加
```
メニューバー↓の「+」を押す
対象のプロジェクトを選択して「Clone」を押す
```
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image198.png?raw=true)]

```
#それとも
リモートリポジトリのURLと保存するフォルダーを指定する
※リモートリポジトリのURLの間に
アクセスアカウントを追加する
https://アクセスアカウント@github.com/Ascon-Dev/hmgr.git
問題がなければ「クローン」を押す
```

[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image199.png?raw=true)]

##ファイル転送ツールのインストール
WinSCPなどのファイルをサーバに転送するツールをインストールする
```
https://winscp.net/eng/download.php
```
##各サーバ設定

ユーザ名とパスワードは保存しておくと便利

###検証環境
```
#転送プロトコル
SFTP
#ホスト名
172.26.65.95
#ポート番号
22
#ユーザ名
developer
#パスワード
HIPzZHz8tHY$(+Ue
```
###検証環境（BS）
```
#転送プロトコル
SFTP
#ホスト名
172.26.65.95
#ポート番号
22
#ユーザ名
bluesoln
#パスワード
J_0Xh/3BINj6!W+$lH
```
###本番環境
```
#転送プロトコル
SFTP
#ホスト名
172.26.65.37
#ポート番号
22
#ユーザ名
developer
#パスワード
8%96Mb8fi!J3bmG
```
[![](https://github.com/Ascon-Dev/omisemiyell/blob/readme/images/image207.png?raw=true)]

## Authors

- [@Kein Pyi Si[ケインピィーシー]](https://www.github.com/keincon)
- [@Takehara[竹原]](https://github.com/ascon-takehara-2021)

