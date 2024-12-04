# Swing
ボタンの配置までのひな型
```java
import java.awt.BorderLayout;
//import java.awt.Container;
import javax.swing.JButton;
import javax.swing.JFrame;

public class JFrameTest extends JFrame {

	public static void main(String[] args) {
		JFrameTest frame = new JFrameTest("MyTitle");
		frame.setVisible(true);

	}
	
	JFrameTest(String title){
		setTitle(title);
		setBounds(100,100,720,480);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		
		JButton btn = new JButton("MyButton");
		
		//省略できるようになった
		//Container contentPane = getContentPane();
		//contentPane.add(btn,BorderLayout.SOUTH);
		add(btn,BorderLayout.SOUTH);
		
	}

}

```

実行クラスで `JFrame` を継承し、コンストラクタでウィンドウの描画を行っている。

```java
//省略できるようになった
//Container contentPane = getContentPane();
//contentPane.add(btn,BorderLayout.SOUTH);
```
この部分は、`add()` は省略できるが、`setBackground()` などのメソッドでは `Container` クラスが必要になるので注意。