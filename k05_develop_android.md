スマートデバイスプログラミング 第5回 補足資料
# Android実機テストの方法

この資料では、Unityで開発したアプリケーションをAndroid端末上で動作確認するため方法について解説します

* [事前準備](#setup)
  * [端末の用意](#setup-devices)
  * [Android SDKのインストール](#install-android-sdk)
    * [Windows の場合](#install-android-sdk-windows)
	* [Mac OS X / Linux の場合](#install-android-sdk-unix)
  * [ドライバのインストール](#install-device-driver)
* [アプリを実機にインストールする](#run)
* [参考資料](#links)


## <a name="setup">事前準備</a>

### <a name="setup-devices">端末の用意</a>

Androidでの動作確認には、以下3点のハードウエアが必要です

* 実機（Android OS搭載のスマートデバイス）
* 開発用端末（ホストUSBポートのあるWindows OS、Mac OS X、Linux等搭載のコンピュータ）
* 実機と開発用端末を接続するUSBケーブル

搭載OSが古いと開発できない場合があります。事前にアップデートしておいてください

### <a name="install-android-sdk">Android SDKのインストール</a>

Android SDKは、Androidアプリケーションの開発キットです。Xcodeとは違いWindowsやLinuxなどでも利用することができます

Android Developers WEBサイトのDownload Android Studio and SDK Toolsページにある[Other Download Options](http://developer.android.com/sdk/index.html#Other)の項目から、Android SDK (SDK Tools Only版) を入手しましょう  
たとえばWindowsなら`installer_rXX.X.X-windows.exe`、Macなら`android-sdk_rXX.X.X-macosx.zip`が目的のファイルになります  
（ページ上部のDOWNLOAD ANDROID STUDIOは目的とは違うインストーラーなので、間違えて押すことのないよう注意してください）

※ 以降はOS別になります

#### <a name="install-android-sdk-windows">Windows の場合</a>

ダウンロードしたインストーラーを実行します  
![Android SDK Windows Installer 1](/assets/k05/android_001.png)

JDK(Java Development Kit)がインストールされていない場合、自動でインストールされます  
![Android SDK Windows Installer 2](/assets/k05/android_002.png)

インストール先を聞かれるので、`Install for anyone using computer`を選んだ後、Program Files以下に保存されることを確認します  
![Android SDK Windows Installer 3](/assets/k05/android_003.png)  
![Android SDK Windows Installer 4](/assets/k05/android_004.png)

インストールが完了したら、`Start SDK Manager`にチェックが入っていることを確認して`Finish`ボタンを押します  
![Android SDK Windows Installer 5](/assets/k05/android_005.png)

Android SDK Managerが起動するので、一旦すべてのチェックを外し、下図のようにチェックを入れ直しします  
（Android SDK Build-toolsは、最もRev.番号の大きいものだけにチェックをしてください。画像だと23.0.2が該当します）  
右下のボタンが`Install 4 packages...`になっていることを確認して、クリックします  
![Android SDK Manager 1](/assets/k05/android_006.png)

パッケージのライセンス同意画面が出るので、右下にある`Accept License`を選択してから、`Install`ボタンをクリックします  
![Android SDK Manager 2](/assets/k05/android_007.png)  
![Android SDK Manager 3](/assets/k05/android_008.png)

自動的にパッケージインストールが行われます。すべて完了したら`Close`ボタンを押し、Android SDK Managerも終了します  
![Android SDK Manager 4](/assets/k05/android_009.png)

スタートボタンを右クリックして、`システム`を選択します  
![スタートボタン -> システム](/assets/k05/android_010.png)

システムウィンドウが開くので、画面左から`システムの詳細設定`をクリックします  
![システムウィンドウ](/assets/k05/android_011.png)

システムプロパティの詳細設定タブが開いたら、画面右下の`環境変数`ボタンを押します  
![システムプロパティ 詳細設定タブ](/assets/k05/android_012.png)

環境変数の設定ウィンドウが開きます。画面下半分の`システム環境変数`から変数`Path`を探し出し、それを選択した状態で`編集`ボタンをクリックします  
![環境変数](/assets/k05/android_013.png)

既存の変数値を**消さずに、末尾に追加する形で**、`;C:\Program Files (x86)\Android\android-sdk\platform-tools`の文字列を追加します  
（Windows 32bit環境や、Program Files以外の場所にインストールした場合は入力する文字列が変わります。必ずエクスプローラーで`adb.exe`がインストールされたフォルダのパスを確認してください。そのうえで、その絶対パスの先頭に「`;`」を足したものを文字列としてください）  
![システム変数の編集](/assets/k05/android_015.png)  
![インストール先の確認](/assets/k05/android_014.png)

以上すべてが上手くいけば、コマンドプロンプトを起動して`adb version`と打ってEnterキーを押したときに、ADB(Android Debug Bridge)のバージョン情報が表示されます  
バージョンが表示されない場合は、一旦再起動して、そのあと環境変数が正しく設定されているかどうかを再度確認してみてください  
![コマンドプロンプト](/assets/k05/android_016.png)

#### <a name="install-android-sdk-unix">Mac OS X / Linux の場合</a>

Work in progress...

### <a name="install-device-driver">ドライバのインストール</a>

Windowsのみ、実機を初めてPCにつなぐ時にデバイスドライバをインストールする必要があります  
Mac OS XおよびLinuxの場合は、この項は必要ないので読み飛ばしてください

Work in progress...


## <a name="run">アプリを実機にインストールする</a>

Work in progress...


## <a name="links">参考資料</a>

* [Unity - マニュアル: Android での開発を始める](http://docs.unity3d.com/ja/current/Manual/android-GettingStarted.html)


---
[第5回資料に戻る](/k05.md)  
[目次に戻る](/README.md#授業テキスト)
