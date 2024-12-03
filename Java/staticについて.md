# staticについて
静的といった意味

同じクラスから複数のインスタンスを作成したとしても、同一のデータで保存する

**設計クラス**
```java
class Method {
	int number;
	String name;
	static int val = 5;
}
```
**メインクラス**
```java
class Main {
	public static void main(String[] args){
		Method m1 = new Method();
		Method m2 = new Method();
		m1.number = 1;
		m2.number = 2;

		System.out.println(m1.number+","+m1.val);
		System.out.println(m2.number+","+m2.val);
	}
}
```
**出力**
```bash
1,5
2,5
```
といったように、`m1` と `m2` の `val` は共通のデータとなっている。


## staticオブジェクトの呼び出し
`Method`クラスで書いた`static`変数の`val`は、`Main`クラスでインスタンス化しなくても呼び出すことができる

**設計クラス**
```java
class Method {
	static int val = 100;
}
```
**実行クラス**
```java
class Main {
	public static void main(String[] args){
		System.out.println(Method.val);
	}
}
```
出力結果
```bash
100
```