# GenshinAPI の設定

公式のチュートリアル

https://enka-docs.kazury.me/getting-started/installation/gradle

バージョンが古いためか記述方法が変わっており、この記事のままではエラーを吐いてしまう。

## build.gradle

設定箇所は以下の通り

### repositories

```java
repositories {
    mavenCentral()
    maven {
        url "https://repo.kazury.me/snapshots"
    }
}
```

### dependencies

```java
dependencies {
    compileOnly([group: 'me.kazury', name: 'EnkaNetworkAPI', version: '5.2-SNAPSHOT'])
}
```

### build.gradle 全体のソースコード

```java
plugins {
    id 'java'
}

group = 'org.example'
version = '1.0-SNAPSHOT'

repositories {
    mavenCentral()
    maven {
        url "https://repo.kazury.me/snapshots"
    }
}

dependencies {
    compileOnly([group: 'me.kazury', name: 'EnkaNetworkAPI', version: '5.2-SNAPSHOT'])
}

test {
    useJUnitPlatform()
}
```
