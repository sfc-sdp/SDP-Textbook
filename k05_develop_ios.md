スマートデバイスプログラミング 第5回 補足資料
# iOS実機テストの方法

この資料では、Unityで開発したアプリケーションをiOS端末上で動作確認するため方法について解説します。


## はじめに

### 端末とアカウントの用意

iOSでの動作確認には、以下3点のハードウエアが必要です。

* 実機（iOS 8 以降搭載の iPhone または iPad）
* 開発用端末（OS X Yosemite あるいは OS X El capitan が動作するコンピューター）
* 実機と開発用端末を接続するUSBケーブル

搭載OSが古いと開発できない場合があります。事前にアップデートしておいてください。  
なお、Windows OSとiOSの組み合わせは不可能なので、その場合は諦めて[Android端末でテスト](/k05_develop_android.md)してください。

初回ビルド時に以下のアカウント情報が必要になります。もし無い方は事前に用意しておいてください。

* Apple ID

### Xcodeのインストール

[<img alt="xcode" src="https://developer.apple.com/library/ios/documentation/ToolsLanguages/Conceptual/Xcode_Overview/Art/XcodeIcon_2x.png" width="268px" />](https://itunes.apple.com/us/app/xcode/id497799835)

Unityに限らず、iOSアプリケーションのビルドにはXcodeと呼ばれる統合開発環境が必要になります。  
必ず公式のMac App Storeから最新のXcodeを入手し、インストールしましょう。[参考: Xcode ghost事件](http://www.apple.com/cn/xcodeghost/#english)

* [Xcode By Apple](https://itunes.apple.com/us/app/xcode/id497799835)

Xcode 7.1は容量が4GB強あるため、安定した通信環境でもインストールに長い時間がかかります。

インストールが完了したら、Xcodeを起動し、表示される利用規約を読んで承認してください。


## UnityからXcodeプロジェクトを書き出す

`File -> Build Settings...`を選択します  
![Build Settings](/assets/k05/ios_001.png)

ビルド設定ウィンドウが開くので、`iOS`を選択して`Switch Platform`ボタンをクリックします

Run in Xcode asを`Release`にし、DevelopmentBuildにチェックを入れて、`Build`ボタンを押します  
（スクリプトデバッグを行いたい場合はRun in Xcode asを`Build`に設定しますが、ここでの説明は割愛します）  
![iOS Build Settings](/assets/k05/ios_003.png)

保存先フォルダを聞かれるので、Save Asに`Xcode`と入力し、`Save`ボタンをクリックしましょう  
![Save windows](/assets/k05/ios_004.png)

しばらく待つと、プロジェクトフォルダに`Xcode`フォルダが作られます。その直下に`Unity-iPhone.xcodeproj`があれば、書き出しは成功です  
![Xcode directory](/assets/k05/ios_005.png)

## アプリを実機にインストールする

開発端末に iPhone または iPad の実機をUSB接続しましょう

先ほど出力した`Unity-iPhone.xcodeproj`をクリックします

Xcodeが起動したら、画面左の`Unity-iPhone`を選択します  
![Unity-iPhone settings](/assets/k05/ios_006.png)

中央にプロジェクト設定が現れるので、中央上部の`General`タブが選択されていることを確認します  
![General Tab](/assets/k05/ios_007.png)

Bundle Identifierには、アプリごとに固有のIDを指定します  
（アプリIDは固有であれば何でもいいのですが、慣例として、自身が所有するドメイン名を反転させたもの＋アプリ名が使われます。たとえばSFCの学生であればsfc.keio.ac.jpドメインのメールアドレスを持っているでしょうから、`jp.ac.keio.sfc`から始まるIDにすることをオススメします。さらに具体的には、SFC-SFSアカウント名がt12000aaだったとして、アプリ名がhogehogeであれば、`jp.ac.keio.sfc.t12000aa.hogehoge`がアプリIDとして相応しいです）  
![Bundle Identifier](/assets/k05/ios_008.png)

続いてTeamには、普段使用しているApple IDを設定します  
この時、もしも`None`と`Add an Account`しか表示されない場合は、後者を選択してXcodeにApple IDを登録します

Accountsウィンドウが開くので、Apple IDとPasswordを入力して`Add`ボタンをクリックします  
![Add Account](/assets/k05/ios_009.png)

無事に追加されたら、Accountsウィンドウを閉じてください。先ほどのTeamに`名前 苗字 (Personal Team) (Apple ID)`が追加されているので、それを選択します

Teamの真下にNo matching provisioning profiles foundと表示されている場合は、その直下の`Fix Issue`ボタンを押してください。TeamにBundle Identifierが紐づけられます

Deployment Targetをインストールする端末のiOSバージョンと同じものに変えます。たとえばiOS 9.1の端末でテストする場合は`9.1`を選択しましょう

以上の設定が済んだら、画面上の`Unity-iPhone`を選択し、Deviceの項目にある端末名をクリックします  
（たとえば`わたしのiPhone`という名前のiPhoneを繋いでいれば、項目もその名前になります。もしもDeviceに`No devices connected to '開発端末名'`と表示されている場合は、USB接続が上手くいっていません。再度USBをさしなおすか、両端末を再起動してみてください）  
![Target device select](/assets/k05/ios_010.png)

画面左上の`▶`ボタンをクリックすれば、端末にアプリがインストールされます  
（ここで何かしらのエラーが出た場合は、端末シンボルのコピーに時間がかかっているか、設定が間違っている可能性があります。前者は時間がたてば解決します。そうでない場合はSAを呼んでください）

インストール後、自動でアプリケーションが起動します  
ただし初回は「信頼されていない開発元」のエラーが出る場合があります。この場合、以下に記すプロファイルの認証作業が必要です  
![信頼されていない開発元](/assets/k05/ios_011.png)

実機の設定アプリを起動し、`一般 -> プロファイル`でプロファイルの一覧を表示します  
![一般 -> プロファイル](/assets/k05/ios_012.png)

デベロッパAPPの項目に、自身のApple IDがあるので、それをタップします  
![プロファイルの一覧](/assets/k05/ios_013.png)

`"Apple ID"を信頼`ボタンを押します  
![開発元を信頼する](/assets/k05/ios_014.png)

ポップアップで再度聞かれるので、もう一度`信頼`ボタンを選択します  
![開発元を信頼する2](/assets/k05/ios_015.png)

ホーム画面に戻り、先ほどインストールしたアプリのアイコンをタップすると、無事にアプリが起動します

## 参考資料

* [Unity - マニュアル: iOS 開発を始める](http://docs.unity3d.com/ja/current/Manual/iphone-GettingStarted.html)


---
[第5回資料に戻る](/k05.md)  
[目次に戻る](/README.md#授業テキスト)
