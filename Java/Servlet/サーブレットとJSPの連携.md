# HTML・サーブレット・JSPの連携

* HTML
```html
<form action="/プロジェクト名/サーブレットのアノテーション" method="post">
    入力フォームの記述
</form>
```

* サーブレット
```java
doGet(request,response){
    doPost(request,response);
}

doPost(request,response) throw ~~ {
    // HTMLの入力フォームからの情報を取得
    int age = request.getParameter("age");

    // 年齢によって分岐
    if(age>=20) String ageStr = "大人";
    else String ageStr = "子供";

    // リクエストオブジェクトに"age"という名前でageStrを保存
    request.setAttribute("age",ageStr);

    //JSPを起動し、requestとresponseの情報をJSPに渡す
    RequestDispatcher rd = request.getRequestDispatcher("/JSPのURL");
    rd.forward(request,response);

}
```

* JSP
```jsp
<div>
    年齢 : 
    //リクエストオブジェクトから"age"のデータを取得
    <%= request.getAttribute("age") %>
</div>
```

