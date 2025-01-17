# JSP Servlet HTMLの関係性
## JSPの機能
* HTMLとJavaとを組み合わせた記述ができる
* HTMLを書き出すためのJavaのコードを記述する
* JSPはサーブレットの機能も内包しているため、新たにサーブレットを用意する必要はないが、サーブレットとJSPを連携させると応用的な機能を実現できる
  
## HTML/Servlet との比較
* `HTML`
  
    いったん記述すると、変更は直接HTMLを書き換える
* `Servlet`
  
  `request.getWrighter()`を用いてHTMLを書き出すことができる
* `JSP`
  
  通常の`HTML`の記述に加えて
  `JSP`タグで`Java`を記述でき、
  `HTML`にロジックを埋め込むことができる
  また、`JSP`を用いると`Servlet`が必要なくなる
  
## 実際に使ってみる
* HTMLとJSPをつなげる
  * 繋げ方は、`html`側の`form:action`でjspのファイル名を指定するだけ
* `doGet`や`doPost`を宣言する必要はなく、`html`側の`form:method`で`"post"`か`"get"`を指定できる
  * 何も指定しなければデフォルトで`"get"`となる
  
### `register_jsp.html`
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>登録画面</title>
  </head>
  <body>
    <h1>登録情報を入力してください</h1>
    <form action="/webj/ConfirmRegistration.jsp" method="post">
      名前： <input type="text" name="name" size="10" /><br />

      パスワード： <input type="password" name="pass" size="10" /><br />

      年齢： <input type="radio" name="age" value="child" />18歳未満
      <input type="radio" name="age" value="adult" />18歳以上
      <input type="radio" name="age" value="other" />それ以外
      <br />
      開発経験：<input type="checkbox" name="lang" value="Java" />Java
      <input type="checkbox" name="lang" value="Python" />Python
      <input type="checkbox" name="lang" value="JavaScript" />JavaScript<br />
      住所：<select name="address" size="1">
        <option value="北海道">北海道</option>
        <option value="東北">東北</option>
        <option value="関東">関東</option>
      </select>
      <br />
      ご意見・お問い合わせ：<br />
      <textarea name="msg" rows="5" cols="50">入力欄</textarea><br />
      <input type="submit" value="送信" />
      <input type="reset" value="取消" />
    </form>

    <img
      src="https://w7.pngwing.com/pngs/343/12/png-transparent-linux-logo-tux-penguin-linux-gnu-penguin-animals-vertebrate-bird.png"
      alt=""
    />
  </body>
</html>
```

### `ConfirmRegistration.jsp`
```java
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title>確認画面</title>
	</head>

	<body>
		<!--スクリプトレット-->
		<%
		request.setCharacterEncoding("utf-8");
    	%>
		<h2>入力情報を確認して登録ボタンを押してください</h2>
	
		<!--式タグ--> 
		<P>名前：<strong><%= request.getParameter("name") %></strong></P>
			
		<P>パスワード：<strong><%= request.getParameter("pass") %></strong></P>

		<!--スクリプトレット-->
		<%
  			String age = request.getParameter("age");
			if(age == null){
				age = "nullだったよ";
			}
			else if(age.equals("child")){
    			age = "18歳未満";
  			} else {
    			age = "18歳以上";
  			}
		%>
		<!--式タグ-->	
		<P>年齢：<strong><%= age %></strong></P>


		<!--スクリプトレット-->
		<P>開発経験：<strong>
		<%
			String[] langs = request.getParameterValues("lang");
			if(langs == null) out.println("null");
			else
  				for(int i = 0; i < langs.length; i++){
  					out.println(langs[i] + " "); 
  				}
		%>
  		</strong><P>
  		
  		<P>住所：<strong><%= request.getParameter("address") %></strong><P>

  		
  		ご意見・お問い合わせ：<br/><strong><%= request.getParameter("msg") %></strong><br/><br/>
		<input type="submit" value="登録" />
		<input type="reset" value="戻る" />
		
		（この画面はJSPで出力しています）
	</body>
</html>
```