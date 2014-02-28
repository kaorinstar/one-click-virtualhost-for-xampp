#One Click Virtualhost for XAMPP

One Click Virtualhost for XAMPPは、  
XAMPPでVirtualHostの設定を簡単に行う為のバッチファイルです。

## 目次
[1. 注意](#1-注意)  
[2. インストール](#2-インストール)  
[3. アンインストール](#3-アンインストール)  
[4. 設定](#4-設定)  
[5. 使い方](#5-使い方)  
[6. 開発環境](#6-開発環境)  
[7. 謝辞](#7-謝辞)  
[8. 著作権とライセンス](#8-著作権とライセンス)

## 1. 注意
このプログラムは、以下の動作をします。

1. Windowsの「hosts」ファイル及び、  
   Apacheの「httpd-vhosts.conf」ファイルを変更します。
2. プロジェクトに関連するフォルダーまたは、ファイルを作成します。
3. MySQL環境変数を設定した場合は、データベースを作成します。
4. PostgreSQL環境変数を設定した場合は、データベースを作成します。
5. Git環境変数を設定した場合は、Gitリポジトリーを作成します。

## 2. インストール
1. ダウンロードします。

2. 「one_click_virtualhost_ja.bat.txt」ファイルを任意のフォルダーに設置します。

3. ファイルをメモ帳または、任意のテキストエディターで開き、  
   設定を自身の環境に合わせて変更し、保存します。  
   （設定については、「[4. 設定](#4-設定)」を参照してください。) 

4. ファイル名の.txt部分を削除します。  
   （例：one_click_virtualhost_ja.bat) 

## 3. アンインストール
1. 「one_click_virtualhost_ja.bat」ファイルを削除します。  
   ※各プロジェクトを削除する方法は、「5. 使い方 > [プロジェクトを削除する](#プロジェクトを削除する)」を参照してください。

## 4. 設定
###プロジェクト環境変数
   * XAMPP_HOME(必須)  
   XAMPPをインストールしたフォルダーのパスを指定します。  
   例)C:\xampp
   
   * DOCUMENT_ROOT_PATH(必須)  
   プロジェクトを作成するフォルダーのパスを指定します。  
   例)C:\home\username
   
   * WEB_ROOT_PATH  
   公開フォルダーのパスを指定します。  
   例)src
   
   * HOSTS_FILE_PATH(必須)  
   Windowsのhostsファイルのパスを指定します。  
   例)C:\windows\system32\drivers\etc\hosts
   
   * TOP_LEVEL_DOMAIN  
   トップレベルドメインを指定します。  
   例)ocv
   
   * APACHE_SVC_NAME  
   Apacheのサービス名を指定します。  
   例)apache2.2

###SSL環境変数
   
   * OPENSSL_CONF(必須)  
   Open SSLの設定ファイルのパスを指定します。  
   例)%XAMPP_HOME%\php\extras\openssl\openssl.cnf
   
   * APACHE_CONF_PATH(必須)  
   Apacheの設定フォルダーのパスを指定します。  
   例)%XAMPP_HOME%\apache\conf
   
   * OPENSSL_PATH(必須)  
   Open SSLの実行ファイルのパスを指定します。  
   例)%XAMPP_HOME%\apache\bin\openssl
   
   * TMP_PATH(必須)  
   一時フォルダーのパスを指定します。  
   例)%XAMPP_HOME%\tmp
   
   * SSL_CERTIFICATION_DAYS  
   SSLサーバー証明書の有効期限を指定します。（単位：日）  
   例)3650
   
   * SSL_COUNTRY_NAME  
   組織の[国名コード](http://ja.wikipedia.org/wiki/ISO_3166-1_alpha-2)を指定します。  
   例)JP
   
   * SSL_STATE_OR_PROVINCE_NAME  
   組織の事業所住所の都道府県を指定します。  
   例)Osaka
   
   * SSL_LOCALITY_NAME  
   組織の事業所住所の市区町村を指定します。  
   例)Osaka
   
   * SSL_ORGANIZATION_NAME  
   組織の名称を指定します。  
   例)kaorinstar.com
   
   * SSL_ORGANIZATIONAL_UNIT_NAME  
   部署の名称を指定します。  
   例)Web Department
   
   * SSL_EMAIL_ADDRESS  
   メールアドレスを指定します。  
   例)noreply@kaorinstar.com

###MySQL環境変数
   
   * MYSQL_MYSQLADMIN_PATH  
   mysqladminの実行ファイルのパスを指定します。  
   例)%XAMPP_HOME%\mysql\bin\mysqladmin
   
   * MYSQL_ROOT_PASSWORD  
   rootのパスワードを指定します。  
   例)password
   
   * MYSQL_DBNAME_PREFIX  
   データベースの名前の接頭辞を指定します。  
   例)my_
   
   * MYSQL_DBNAME_SUFFIX  
   データベースの名前の接尾辞を指定します。  
   例)_db
   
   * MYSQL_DEFAULT_CHARACTER_SET  
   データベースの文字コードを指定します。  
   例)utf8

###PostgreSQL環境変数
   
   * PGSQL_CREATEDB_PATH  
   createdbの実行ファイルのパスを指定します。  
   例)%XAMPP_HOME%\pgsql\bin\createdb
   
   * PGSQL_POSTGRES_PASSWORD  
   postgresのパスワードを指定します。  
   例)password
   
   * PGSQL_OWNER  
   データベースのオーナーを指定します。  
   例)owner
   
   * PGSQL_DBNAME_PREFIX  
   データベースの名前の接頭辞を指定します。  
   例)my_
   
   * PGSQL_DBNAME_SUFFIX  
   データベースの名前の接尾辞を指定します。  
   例)_db
   
   * PGSQL_ENCODING  
   データベースの文字コードを指定します。  
   例)UTF8

###Git環境変数
   
   * GIT_PATH  
   Gitの実行ファイルのパスを指定します。  
   例)C:\Program Files\Git\bin\git

## 5. 使い方
###新規プロジェクトの作成
   1. 「one_click_virtualhost_ja.bat」ファイルをダブルクリックして実行します。  
      (コマンドプロンプトが起動します)  
      ※Windows Vista以降で「ユーザー・アカウント制御（UAC）」を有効にしている場合は、  
        右クリックでメニューを開き、「管理者として実行」をクリックして実行します。

   2. プロジェクト名を尋ねられるので、お好きなプロジェクト名を入力します。  
      ※半角英数字（a～z、0～9）とハイフン（-）とドット（.）で入力してください。  
      ※プロジェクト名がドメインになります。

   3. 公開フォルダーのパスを変更するか尋ねられるので、  
      変更する場合は「y」、変更しない場合は「n」を入力して、  
      エンターキーを押します。

      公開フォルダーのパス：  
```
%DOCUMENT_ROOT_PATH%\プロジェクト名\%WEB_ROOT_PATH%
```

     「y」と入力した場合はプロジェクト名以下のパスを入力します。  
      ※開始と終了には、区切り文字（ \ ）は必要ありません。  
      例)src\public_html

   4. SSLを設定するか尋ねられるので、  
      設定する場合は「y」、設定しない場合は「n」を入力して、  
      エンターキーを押します。

   5. MySQLのデータベースを作成するか尋ねられるので、  
      作成する場合は「y」、作成しない場合は「n」を入力して、  
      エンターキーを押します。  
      「y」を選択した場合はデータベース名を尋ねられるので、  
      お好きなデータベース名を入力します。  
      ※入力がない場合はプロジェクト名になります。

   6. PostgreSQLのデータベースを作成するか尋ねられるので、  
      作成する場合は「y」、作成しない場合は「n」を入力して、  
      エンターキーを押します。  
      「y」を選択した場合はデータベース名を尋ねられるので、  
      お好きなデータベース名を入力します。  
      ※入力がない場合はプロジェクト名になります。

   7. Gitリポジトリーを作成するか尋ねられるので、  
      作成する場合は「y」、作成しない場合は「n」を入力して、  
      エンターキーを押します。  
      ※Gitを予めインストールしておく必要があります。

   8. Apacheを再起動します。  
      ※サービスに登録している場合は、自動的に再起動します。

   9. キーボードの何かのキーを押すとコマンドプロンプトが閉じます。

   10. 完了です。

###プロジェクトを削除する
   1. Apacheの「httpd-vhosts.conf」ファイルをメモ帳か、  
      テキストエディターで開きます。

      「httpd-vhosts.conf」ファイルのパス：  
```
%XAMPP_HOME%\apache\conf\extra\httpd-vhosts.conf
```

   2. 削除するプロジェクト名のコメントを探します。

   3. プロジェクトの設定の開始のコメントから、  
      終了のコメントまでを削除します。

      開始のコメント：  
```
#  
# Begin プロジェクト名 config.  
#
```

      終了のコメント：  
```
#  
# End プロジェクト名 config.  
#
```

   4. ファイルを保存して閉じます。

   5. Windowsの「hosts」ファイルをメモ帳か、  
      テキストエディターで開きます。

      「hosts」ファイルのパス：  
```
C:\Windows\System32\drivers\etc\hosts
```

   6. 削除するプロジェクトのドメインが記述されている行を削除します。

      プロジェクトのドメインが記述されている行：  
```
127.0.0.1 プロジェクト名.ocv
```

   7. ファイルを保存して閉じます。

   8. Apacheを再起動します。

   9. プロジェクト名のフォルダーを削除します。

      「プロジェクト名」フォルダーのパス：  
```
%DOCUMENT_ROOT_PATH%\プロジェクト名
```

   10. MySQLのデータベースを作成している場合は、  
       phpMyAdminにアクセスして、プロジェクトのデータベースを削除します。

      「phpMyAdmin」のデフォルトのURL：  
```
http://localhost/phpmyadmin/
```

   11. PostgreSQLのデータベースを作成している場合は、  
       phpPgAdminにアクセスして、プロジェクトのデータベースを削除します。

      「phpPgAdmin」のデフォルトのURL：  
```
http://localhost/phppgadmin/
```

   12. 完了です。

## 6. 開発環境
* プログラムのソースは、 [GitHub](https://github.com/kaorinstar/one-click-virtualhost-for-xampp) にホストされています。 
* プログラムの問題・質問・機能要求は、 [GitHub Issues](https://github.com/kaorinstar/one-click-virtualhost-for-xampp/issues) へご投稿ください。

## 7. 謝辞
インスピレーションを与えていただいた、多くのブロガーに感謝します。

## 8. 著作権とライセンス
Copyright &copy; 2014 Kaoru Ishikura.  
[MIT license](https://github.com/kaorinstar/one-click-virtualhost-for-xampp/blob/master/LICENSE) の下にリリースされています。
