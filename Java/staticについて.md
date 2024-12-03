# staticについて
設計クラス
```java
class Method {
	static int val = 100;
}
```
実行クラス
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
`Method`クラスで書いた`static`変数の`val`は、`Main`クラスでインスタンス化しなくても呼び出すことができる