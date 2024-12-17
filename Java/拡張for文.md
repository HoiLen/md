# 拡張for文


### 書き方
```java
for(受け取りたい型 好きな変数名 : 繰り返し対象の配列)
```
#### 例
```java
int[] arr = new int[4];{
    arr[0]=1;
    arr[1]=2;
    arr[2]=3;
    arr[3]=4;
}

for(int number:arr){
    System.out.println(number)
}
```
#### 出力結果：
```console
1
2
3
4
```

## 多次元配列の場合
```java
int[][] arr = new int[2][2];{
    arr[0][0]=1;
    arr[0][1]=2;
    arr[1][0]=3;
    arr[1][1]=4;
}

for(int[] numArr:arr){
    for(int number:numArr){
        System.out.println(number);
    }
}
```
１つ目のfor文では、`2x2`の２次元配列から１行ずつを取り出している。

２つ目のfor文では、配列`numArr`から`int`型で１つずつ取り出している