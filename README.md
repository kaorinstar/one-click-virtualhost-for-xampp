#one-click-virtualhost

One Click Virtualhost for Windowsは、  
XAMPPでVirtualHostの設定を簡単に行う為のバッチファイルです。

## 目次
1. 注意
2. インストール
3. アンインストール
4. 設定
5. 使い方
6. ライセンス

## 1. 注意
このプログラムは、Windowsの「hosts」ファイル及び、  
Apacheの「httpd-vhosts.conf」ファイルを変更します。

また、指定したパスにプロジェクト名のフォルダー及び、  
関連するフォルダーまたは、ファイルを作成します。

## 2. インストール
1. ダウンロードします。
2. 「one_click_virtualhost.bat.txt」ファイルを任意のフォルダーに設置します。
3. ファイルをメモ帳または、任意のテキストエディターで開き、  
   設定を自身の環境に合わせて変更します。(設定については、「4. 設定」を参照) 
4. ファイル名の.txt部分を削除します。(one_click_virtualhost.bat)

## 3. アンインストール
「one_click_virtualhost.bat」ファイルを削除します。  
※各プロジェクトを削除する方法は、「5. 使い方>・プロジェクトを削除する」を参照してください。

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
   SSLサーバ証明書の有効期限を指定します。（単位：日）  
   例)3650
   
   * SSL_COUNTRY_NAME  
   組織の[国名コード][ISO_3166-1]を指定します。  
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

## 5. 使い方
###新規プロジェクトの作成
   1. 「one_click_virtualhost.bat」ファイルをダブルクリックして実行します。  
      (コマンドプロンプトが起動します)

   2. プロジェクト名を尋ねられるので、お好きなプロジェクト名を入力します。  
      ※英数字で入力します。  
      ※スペースは入力しないでください。  
      ※プロジェクト名がドメインになります。

   3. 公開フォルダーのパスを変更するか尋ねられるので、  
      変更する場合は「y」、変更しない場合は「n」を入力して、  
      エンターキーを押します。

      デフォルトのパスは、  
      `%DOCUMENT_ROOT_PATH%\プロジェクト名\%WEB_ROOT_PATH%`  
      になります。

     「y」と入力した場合はプロジェクト名以下のパスを入力します。  
      ※開始と終了には、区切り文字( \ )は必要ありません。  
      例)src\public_html

   4. SSLを設定するか尋ねられるので、  
      設定する場合は「y」、設定しない場合は「n」を入力して、  
      エンターキーを押します。

   5. Gitを設定するか尋ねられるので、  
      設定する場合は「y」、設定しない場合は「n」を入力して、  
      エンターキーを押します。
      ※Gitを予めインストールしておく必要があります。

   6. Apacheを再起動します。  
      ※サービスに登録している場合は、自動的に再起動します。

   7. キーボードの何かのキーを押すとコマンドプロンプトが閉じます。

   8. 完了です。

###プロジェクトを削除する
   1. Apacheの「httpd-vhosts.conf」ファイルをメモ帳か、  
      テキストエディターで開きます。

      ・「httpd-vhosts.conf」ファイルのパス  
        %XAMPP_HOME%\apache\conf\extra\httpd-vhosts.conf

   2. 削除するプロジェクト名のコメントを探します。

   3. プロジェクトの設定の開始のコメントから、  
      終了のコメントまでを削除します。

      ・開始のコメント  
      `#`  
      `# Begin プロジェクト名 config.`  
      `#`

      ・終了のコメント  
      `#`  
      `# End プロジェクト名 config.`  
      `#`

   4. ファイルを保存して閉じます。

   5. Windowsの「hosts」ファイルをメモ帳か、  
      テキストエディターで開きます。

      ・「hosts」ファイルのパス  
        C:\Windows\System32\drivers\etc\hosts

   6. 削除するプロジェクトのドメインが記述されている行を削除します。

      ・プロジェクトのドメインが記述されている行  
      `127.0.0.1 プロジェクト名.ocv`

   7. ファイルを保存して閉じます。

   8. Apacheを再起動します。

   9. プロジェクト名のフォルダーを削除します。

      ・「プロジェクト名」フォルダーのパス  
        %DOCUMENT_ROOT_PATH%\プロジェクト名

   10. 完了です。

## 6. ライセンス
Copyright &copy; 2012 Kaoru Ishikura.  
Dual licensed under the [MIT license][MIT] and [GPL license][GPL].

[ISO_3166-1]: http://ja.wikipedia.org/wiki/ISO_3166-1_alpha-2
[MIT]: http://www.opensource.org/licenses/mit-license.php
[GPL]: http://www.gnu.org/licenses/gpl.html
