# `String[] args`について
Javaのメインプログラムは以下のようになる
```java
class xx {
	public static void main(String[] args) {
		//処理
	}
}
```
`main`関数の引数には`String[] args`と書かれている
これは、コマンドラインで実行するときに、プログラムに渡せる文字列を表している
```powershell
> java xx.java 引数1 引数2
```
`PowerShell`などのコマンドソフトでjavaファイルをコンパイルするときに、文字列の配列としてプログラムに情報を渡す。
要素数に限りはない。