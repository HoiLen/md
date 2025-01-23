# MVC Model
* Model : Beans
  * Beans自体は入力フォームの画面遷移時にデータを一時的に保存するためのもの
  * 設計クラス
* View : JSP
  * クライアント側にUIを表示する
* Controller : Servlet
  * クライアントの入力を受け取って`Model`に処理の指示をする
  * View側に処理の結果を表示するように指示をする
  * 要は実行クラス