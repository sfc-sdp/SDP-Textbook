スマートデバイスプログラミング 第2回 補足資料
# C#の記法

## 変数
JavaやJavaScriptと、おおむね同じ使い方で使えます。  
JavaScriptでは型を省略しても動いてくれますが、C#ではbuild時にエラーが出ることが多いので注意しましょう。

### ＜覚えておいて欲しい型＞

    int a = 0; //整数
    float b = 0.3f; //浮動小数点数型：数値の後にfを付けます。
    string s = "time"; //文字列：「"」でくくります。
    bool b = true; //ブーリアン型。trueかfalseが入ります

### ＜場合によっては使うかもしれない型＞

    char c = 'a'; //文字。半角文字列を扱います。「'」でくくります。
    double d = 0.01; //倍精度浮動小数点数型。

## 条件分岐

### if文

条件式を満たしている時は aaa を実行します。

    if(条件式) {
        aaa;
    }

条件式を満たしている時は aaa を、満たしていないときは bbb を実行します。
    
    if(条件式) {
        aaa;
    } else {
        bbb;
    }

### switch文

値によって処理を切り替えたい場合は、switch文が使えます。

変数の値が「1」だったら aaa を、「2」だったら bbb を、それ以外の値だったら ccc を実行します。  
break;を忘れると次の命令も実行してしまうので忘れないよう注意しましょう。(aaaの次の行のbreakを忘れると、bbbも実行されます）

    switch(変数名){
        case 1:
            aaa;
            break;
        case 2:
            bbb;
            break;
        default:
            ccc;
            break;
    }

## 反復処理

### for文

まず aaa を実行します。条件 bbb を満たす限り、 ddd が繰り返し実行されます。  
1回実行するごとに ccc が呼ばれ、 bbb が満たされているか再度判断されます。

    for(aaa; bbb; ccc){
        ddd;
    }
    
具体的に以下は、 aaa の処理を3回繰り返します
    
    for(int i=0; i<3; i++){
        aaa;
    }

### while文

条件 aaa が満たされる限り、 bbb を繰り返し実行します。

    while(aaa){
        bbb;
    }

## 配列

### 固定長配列

    int[] aaa = new int[3];
    string[] bbb = new string[5];
    string[] ccc = new string[]{"abc","def","ghi"};
    
    aaa[0] = 1;
    bbb[1] = "test";
    
    for(int i=0;i<3;i++){
        aaa[i] = i;
    }

### リスト（可変長配列）

要素数が変わる場合はリストも使えます。

    using System.Collections.Generic; //プログラムの冒頭に１行追加が必要
    
    List aaa = new List();
    List bbb = new List();
    aaa.Add("abc");
    aaa.Add("def");
    aaa.Add("ghi");
    
    int size = aaa.Count; //要素の数が分かる
    
    aaa[0] = "ghi"; //上書き
---
[第2回資料に戻る](/k02.md)  
[目次に戻る](/README.md#授業テキスト)
