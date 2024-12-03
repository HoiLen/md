# Enka.Network API wrapper


https://enka-docs.kazury.me/getting-started/installation/gradle


https://repo.kazury.me/snapshots
もしかしたら
https://repo.kazury.me/#/snapshots
`#`がいるかも

https://repo.kazury.me/#/snapshots/me/kazury/EnkaNetworkAPI/5.2-SNAPSHOT

## UI Pathから画像の取得
このAPIにはアイコン（画像）の識別子を返すメソッドがある
```java
final String identifier = "UI_AvatarIcon_Furina";

api.getGenshinIcon(identifier); // returns the png from the ui path. 
```
