# javaで画像ファイルなどのresourceを参照する
ファイルパスを文字列で入力するだけでは正しく認識されない場合がある。

## 問題
以下のコードはウィンドウのアイコンを設定するプログラム。

`ImageIcon`の引数にファイルパスを書いているが、これだとアイコンに設定されない。
```java
ImageIcon icon = new ImageIcon("./icon.png");//認識されない
setIconImage(icon.getImage());
```

## 解決策
ファイルパスの指定に`クラス名.class.getResource("ファイルパス")`を使う。
```java
//class名: Test
ImageIcon icon = new ImageIcon(Test.class.getResource("./icon.png"));
setIconImage(icon.getImage());
```
