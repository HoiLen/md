# サーブレットのjavaファイルとhtmlの連携

## サーブレット全体のソースコード
### `Confirm.java`
```java
// ４つのパッケージをインポート
import java.io.IOException;
import java.io.PrintWriter;

import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

@WebServlet("/register") // マッピング名を指定
public class Confirm extends HttpServlet {// HttpServletクラスを継承

	public void doGet(HttpServletRequest req, HttpServletResponse res)
			throws IOException, ServletException {
		doPost(req, res);
	}

	public void doPost(HttpServletRequest req, HttpServletResponse res)
			throws IOException, ServletException {
		req.setCharacterEncoding("UTF-8"); //受け取り(Request)のエンコーディング
		res.setContentType("text/html;charset=utf-8");//書き出し(Response)のエンコーディング
		
		PrintWriter out = res.getWriter(); // PrintWriterを取得
		out.println("<html>");
		out.println("<head>");
		out.println("<title>確認画面</title>"); // PrintWriterで出力
		out.println("</head>");
		out.println("<body>");
		out.println("<h1>入力情報を確認してボタンを押してください</h1>");

		out.println("名前:<strong>" + req.getParameter("name") + "</strong><br/>");

		out.println("パスワード:<strong>" + req.getParameter("pass") + "</strong><br/>");

		if (req.getParameter("age") == "child")
			out.println("年齢:<strong>子供</strong><br/>");
		else if (req.getParameter("age") == "adult")
			out.println("年齢:<strong>大人</strong><br/>");
		else
			out.println("年齢:<strong>その他</strong><br/>");

		//チェックボックスから情報を取得
		String[] exLang = req.getParameterValues("lang");
		out.print("開発経験:");
		for (String lang : exLang) {
			out.print("<strong>" + lang + "</string> ");
		}
		out.println();

		out.println("住所:<strong>" + req.getParameter("address") + "</strong><br/>");

		out.println("ご意見・お問い合わせ:\n" + req.getParameter("msg"));

		out.println("<input type=\"submit\" value=\"登録\" />");
		out.println("<input type=\"reset\" value=\"戻る\" /><br/>");

		out.println("</body>");
		out.println("</html>");
	}
}

```
### `register.html`
```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8">
    <title>登録画面</title>
  </head>
  <body>
    <h1>登録情報を入力してください</h1>
    <form action="/webj/register" method="post">
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
        <option value="中部">中部</option>
        <option value="近畿">近畿</option>
        <option value="中国">中国</option>
        <option value="四国">四国</option>
        <option value="九州">九州</option>
        <option value="沖縄">沖縄</option>
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







## 必須の記述

* `doGet`と`doPost`の宣言
  
    どちらかのメソッドに処理を書き、処理を書いたメソッドを再利用する
```java
public void doGet(HttpServletRequest req, HttpServletResponse res)
			throws IOException, ServletException {
		doPost(req, res);
	}
```

```java
public void doPost(HttpServletRequest req, HttpServletResponse res)
			throws IOException, ServletException {
		//~~処理の記述~~
	}
```

* 今回は`doPost`に処理を記述
```java
req.setCharacterEncoding("UTF-8"); //受け取り(Request)のエンコーディング
res.setContentType("text/html;charset=utf-8");//書き出し(Response)のエンコーディング
```
`req.setCharacterEncoding("UTF-8")` は、`html`からのリクエストを受け取るときのエンコード設定

`res.setContentType("text/html;charset=utf-8")` は、受け取った情報を書き出すときなどのエンコード設定


* アノテーションをそろえる
  ```java
  @WebServlet("/register") // マッピング名を指定
  ```
  ```html
  <form action="/webj/register"></form>
  ```