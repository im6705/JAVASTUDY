## 9장

* 1번 문제

  > JLabel 컴포넌트는 Mouse 이벤트를 받을 수 있다. JLabel 컴포넌트의 초기 문자열을 "자기야"라고 출력하고, 레이블에 마우스를 올리면 "사랑해"로, 내리면 "자기야"가 다시 출력되도록 프로그램을 작성하라.
 ```java
 import java.awt.*;
 import javax.swing.*;
 import java.awt.event.*;
 public class t91 extends JFrame
 {
 	class controller extends MouseAdapter {
 			public void mouseEntered(MouseEvent e) {
 				JLabel lb = (JLabel)e.getSource();
 				lb.setText("사랑해");
 			}
 		public void mouseExited(MouseEvent e) {
 			JLabel lb = (JLabel)e.getSource();
 			lb.setText("자기야");
 		}	
 	}
 	public t91() {
 		setTitle("마우스 올리기 실습");
 		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
 		Container c = getContentPane();
 		c.setLayout(new FlowLayout());
 		JLabel la = new JLabel("자기야");
 		la.addMouseListener(new controller());
 		c.add(la);
 		setSize(300,300);
 		setVisible(true);
 	}
 	public static void main(String[] args)
 	{
 		new t91();
 	}
 }
 ```
* 실행 결과
![](https://user-images.githubusercontent.com/10539689/119646881-9faa3c00-be5a-11eb-82b9-627964b98f9e.png)![](https://user-images.githubusercontent.com/10539689/119646883-9faa3c00-be5a-11eb-83cb-5ecd3a51b965.png)



* 2번 문제

	> 프레임의 컨텐트팬의 초기 색을 Color.CYAN으로 하고, R 키를 누르는 순간 배경색이 Color.RED 색으로 변했다가. 키를 떼면 다시 초기 색으로 돌아오는 프로그램을 작성하라.
```java
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;
public class t92 extends JFrame
{
	Container c = getContentPane();
	public t92() {
		c.setBackground(Color.CYAN);
		setSize(300,300);
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		c.addKeyListener(new KeyEventController());
		setVisible(true);
		c.setFocusable(true);
		c.requestFocus();
	}
	class KeyEventController extends KeyAdapter{
		public void keyPressed(KeyEvent e) {
			if(e.getKeyChar() == 'R') {
				c.setBackground(Color.RED);
			}
		}
		public void keyReleased(KeyEvent e) {
			c.setBackground(Color.CYAN);
		}
	}
	public static void main(String[] args)
	{
		new t92();
	}
}
```

* 실행 결과

![](https://user-images.githubusercontent.com/10539689/119646884-a042d280-be5a-11eb-8a41-cfab961b99b5.png)![](https://user-images.githubusercontent.com/10539689/119646885-a042d280-be5a-11eb-9e1e-3929605680a5.png)

* 3번 문제

	> 컨텐트팬의 배경색은 초록색(Color.GREEN)으로 하고, 마우스의 드래깅 동안만 노란색(Color.YELLOW)으로 나타나는 프로그램을 작성하라. 드래깅을 멈추면 초록색이 된다.
```java
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;
public class t93 extends JFrame
{
	Container c = getContentPane();
	public t93() {
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		c.setBackground(Color.GREEN);
		c.addMouseListener(new MouseCon());
		c.addMouseMotionListener(new MouseCon());
		setVisible(true);
		setSize(300,300);
	}
	class MouseCon extends MouseAdapter {
		public void mouseReleased(MouseEvent e) {
			c.setBackground(Color.GREEN);
		}
		public void mouseDragged(MouseEvent e) {
			c.setBackground(Color.YELLOW);
		}
	}
	public static void main(String[] args)
	{
		new t93();
	}
}
```

* 실행 결과

![](https://user-images.githubusercontent.com/10539689/119646887-a0db6900-be5a-11eb-8893-4931179a73f7.png)![](https://user-images.githubusercontent.com/10539689/119646888-a0db6900-be5a-11eb-96d3-7c834bd896f3.png)

* 4번 문제

	> JLabel 컴포넌트를 이용하여 "Love Java"를 출력하고, + 키를 치면 폰트 크기를 5픽세릿ㄱ 키우고, - 키를 치면 폰트 크기를 5픽셀씩 줄이는 스윙 응용프로그램을 작성하라. 5픽셀 이하로 작아지지 않도록 하라.
```java
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;

public class t94 extends JFrame
{
	JLabel la = new JLabel("Love Java");
	Container c = getContentPane();
	public t94() {
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		c.setLayout(new FlowLayout());
		c.addKeyListener(new keyCon());
		setSize(300,300);
		setVisible(true);
		c.add(la);
		c.setFocusable(true);
		c.requestFocus();
	}
	class keyCon extends KeyAdapter {
		public void keyPressed(KeyEvent e) {
        	Font f = la.getFont();
			int s = f.getSize();
			if(e.getKeyChar() == '+') {
				la.setFont(new Font("Arial", Font.PLAIN, s + 5));
			}
			else if(e.getKeyChar() == '-' && s > 5) {
				la.setFont(new Font("Arial", Font.PLAIN, s - 5));
			}
		}
	}
	public static void main(String[] args)
	{
		new t94();

	}
}
```

* 실행 결과

![](https://user-images.githubusercontent.com/10539689/119646890-a0db6900-be5a-11eb-9b02-b837f2a8d60f.png)![](https://user-images.githubusercontent.com/10539689/119646891-a173ff80-be5a-11eb-8f08-9206affcba4f.png)

* 5번 문제

	> 클릭 연습용 스윙 응용프로그램을 작성하라. JLabel을 이용하여 문자열 "C"인 레이블을 하나 만들고 초기 위치를 (50,50)으로 하라. 문자열을 클릭할 때마다 레이블은 프레임 내의 랜덤한 위치로 움직인다.
```java
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;
public class t95 extends JFrame
{
	JLabel la = new JLabel("C");
	public t95() {
		Container c = getContentPane();
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		c.setLayout(null);
		la.setBounds(50,50,50,50);
		la.addMouseListener(new clickevent());
		c.add(la);
		setSize(300, 300);
		setVisible(true);
	}
	class clickevent extends MouseAdapter{
		public void mouseClicked(MouseEvent e) {
			Container c2 = la.getParent();
			int x_max = c2.getWidth() - la.getWidth();
			int y_max = c2.getHeight() - la.getHeight();
			int x = (int)(Math.random()*x_max);
			int y = (int)(Math.random()*y_max);
			la.setLocation(x,y);
		}
	}
	public static void main(String[] args)
	{
		new t95();
	}
}
```

* 실행 결과

![](https://user-images.githubusercontent.com/10539689/119646895-a173ff80-be5a-11eb-8cd7-2363668075c8.png)![](https://user-images.githubusercontent.com/10539689/119646897-a20c9600-be5a-11eb-95c4-348e5c058061.png)

* 6번 문제

  > GridLayout을 이용하여 컨텐트팬에 숫자를 담은 JLabel을 12개를 부착하고, 초기바탕색을 모두 Color.WHITE 색으로 한다. 그리고 각 레이블 위에 마우스로 클릭하면 랜덤한 색으로 채워지도록 프로그램을 작성하라. 랜덤한 색을 만드는 방법은 예제 9-6의 코드를 참고하라.
```java
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;
public class t96 extends JFrame
{
	private int r, g, b;
	public t96(){
		JLabel la[] = new JLabel[12];
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		Container c = getContentPane();
		c.setLayout(new GridLayout(4, 3)); //4*3 = 12
		for(int i = 0; i<12; i++) {
			la[i] = new JLabel(Integer.toString(i));
			la[i].setBackground(Color.WHITE);
			la[i].addMouseListener(new changeColor());
			c.add(la[i]);
		}
		setSize(300,300);
		setVisible(true);
	}
	class changeColor extends MouseAdapter{
		public void mouseClicked(MouseEvent e) {
			JLabel temp = (JLabel)e.getSource();
			temp.setOpaque(true);
			temp.setBackground(randomColor());
		}
	}
	Color randomColor() {
		r = (int)(Math.random()*256);
		g = (int)(Math.random()*256);
		b = (int)(Math.random()*256); // from ex96
		return new Color(r,g,b);
	}
	public static void main(String[] args)
	{
		new t96();
	}
}
```

* 실행 결과

![](https://user-images.githubusercontent.com/10539689/119646899-a20c9600-be5a-11eb-8033-84d2c4fac9ff.png)![](https://user-images.githubusercontent.com/10539689/119646869-9d47e200-be5a-11eb-8ae1-c88409208440.png)

* 7번 문제

	> 임의의 정수에 주어진 연산을 조합하여 0을 만드는 게임을 작성해보자. 화면에는 1에서 60 사이의 임의의 정수가 출력되고, 그 밑에 "+2" 버튼, "-1" 버튼, "%4" 버튼의 세 버튼을 출력하라. 그리고 이들 버튼을 누르면 정수에 '더하기 2', '빼기 2', '4로 나눈 나머지'를 각각 계산하여 정수를 수정하라. 사용자가 각 버튼을 한 번씩만 누를수 있도록 누른 버튼은 모두 비활성화시켜라. 버튼을 눌러서 정수가 0이 되면 처음부터 시작하도록 하라.
```java
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;
public class t97 extends JFrame
{
	private int num = 0;
	JButton bt[] = new JButton[3];
	JLabel la;
	public t97() {
		setTitle("0으로 만들기");
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		Container c = getContentPane();
		c.setLayout(new BorderLayout());
		c.add(new NumPanel(),BorderLayout.NORTH);
		c.add(new ButtonPanel(),BorderLayout.SOUTH);
		setSize(300, 200);
		setVisible(true);
	}
	class ButtonPanel extends JPanel{
		public ButtonPanel() {
			setLayout(new FlowLayout());
			bt[0] = new JButton("+2");
			bt[1] = new JButton("-1");
			bt[2] = new JButton("%4");
			for(int i = 0; i<3; i++) {
				bt[i].addActionListener(new btAction()); // 개인적으로 익명클래스 나중에 수정할때에 불편할듯...
				add(bt[i]);
			}

		}
	}
	class btAction implements ActionListener{
		public void actionPerformed(ActionEvent e) {
			JButton temp = (JButton)e.getSource();
			if(temp == bt[0]) {
				num += 2;
				la.setText(Integer.toString(num));
				bt[0].setEnabled(false);
				if(bt[1].isEnabled() == false && bt[2].isEnabled() == false)
					setTitle("실패"); // +2라서 마지막에 이거면 무조건 실패
			}
			else if(temp == bt[1]) {
				num -= 1;
				la.setText(Integer.toString(num));
				bt[1].setEnabled(false);
				if(bt[0].isEnabled() == false && bt[2].isEnabled() == false) {
					if(num == 0) {
						num = (int)((Math.random()*59)+1);
						la.setText(Integer.toString(num));
						for(int i =0;i<3;i++)
							bt[i].setEnabled(true);
					}
					else {
						setTitle("실패");
					}
				}
			}
			else { //남은거 bt[2]
				num %= 4;
				la.setText(Integer.toString(num));
				bt[2].setEnabled(false);
				if(bt[0].isEnabled() == false && bt[1].isEnabled() == false) {
					if(num == 0) {
						num = (int)((Math.random()*59)+1);
						la.setText(Integer.toString(num));
						for(int i =0;i<3;i++)
							bt[i].setEnabled(true);
					}
					else {
						setTitle("실패");
					}
				}
			}
		}
	}
	class NumPanel extends JPanel{
		public NumPanel() {
			setLayout(new FlowLayout());
			num = (int)((Math.random()*59)+1); // 1~60
			la = new JLabel(Integer.toString(num));
			add(la);
		}
	}
	public static void main(String[] args)
	{
		new t97();
	}
}
```

* 실행 결과

![](https://user-images.githubusercontent.com/10539689/119646873-9de07880-be5a-11eb-958c-63a55f7d7f50.png)![](https://user-images.githubusercontent.com/10539689/119646876-9e790f00-be5a-11eb-9a65-01637e43055e.png)

* Bonus 1

	> JLabel을 활용하여 "Love Java"를 출력하고, "Love Java" 글자 위에 마우스를 올려 마우스 휠을 위로 굴리면 글자가 작아지고, 아래로 굴리면 그랒가 커지도록 프로그램을 작성하라. 폰트 크기는 한 번에 5픽셀씩 작아지거나 커지도록 하고, 5픽셀 이하로 작아지지 않도록 하라.
```java
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;

public class t9b1 extends JFrame
{
	JLabel la = new JLabel("Love Java");
	Container c = getContentPane();
	public t9b1() {
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		c.setLayout(new FlowLayout());
		c.addMouseWheelListener(new mwcon());
		setSize(300,300);
		setVisible(true);
		c.add(la);
		c.setFocusable(true);
		c.requestFocus();
	}
	class mwcon implements MouseWheelListener {
		public void mouseWheelMoved(MouseWheelEvent e) {
        	Font f = la.getFont();
			int s = f.getSize();
			if(e.getWheelRotation() < 0) {
				if(s <= 5) {
					
				} else {
					la.setFont(new Font("Arial", Font.PLAIN, s - 5));
				}
				
			}
			else {
				la.setFont(new Font("Arial", Font.PLAIN, s + 5));
			}
		}
	}
	public static void main(String[] args)
	{
		new t9b1();
	}
}
```

* 실행 결과

![](https://user-images.githubusercontent.com/10539689/119646877-9e790f00-be5a-11eb-972a-9bd5decb1012.png)![](https://user-images.githubusercontent.com/10539689/119646878-9f11a580-be5a-11eb-8a2d-17e11373aa4d.png)

* Bonus 2
	
	> 간단한 계산기를 만들어보자. 아래 그림과 같이 여러 버튼들이 있고 숫자 버튼과 연산자 버튼을 눌러 계산식을 만든 후 계산 버튼을 누르면 결과를 출력한다. 코딩읜 난이도를 낮추기 위해 한 번에 하나의 연산만 처리하도록 작성하라. 예를 들어 2+3*4와 같이 두 개 이상의 연산자가 들어 있는 계산은 처리하지 않아도 된다.
```java
import java.awt.*;
import javax.swing.*;
import java.awt.event.*;
import java.util.StringTokenizer;

public class t9b2 extends JFrame {
  JButton bt[] = new JButton[16];
  JTextField inputtf = new JTextField(20);
  JTextField outputtf = new JTextField(20);
  String input ="";
  String num1 = "0";
  String num2 = "0";
  String oper = "";
  public t9b2() {
    setTitle("계산기");
    setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    Container c = getContentPane();
    c.setLayout(new BorderLayout());
    c.add(new NumPanel(), BorderLayout.NORTH);
    c.add(new ButtonPanel(), BorderLayout.SOUTH);
    setSize(800, 200);
    setVisible(true);
  }

  class ButtonPanel extends JPanel {
    public ButtonPanel() {
      setLayout(new GridLayout(4, 4, 4, 4));
      for (int i = 0; i < 10; i++) {
        bt[i] = new JButton(Integer.toString(i));
        bt[i].addActionListener(new btAction()); 
        add(bt[i]);
      }
      bt[10] = new JButton("CE");
      bt[11] = new JButton("계산");
      bt[12] = new JButton("+");
      bt[13] = new JButton("-");
      bt[14] = new JButton("x");
      bt[15] = new JButton("/");
      for (int i = 10; i < 16; i++) {
        bt[i].addActionListener(new btAction());
        add(bt[i]);
      }
    }
  }

  class btAction implements ActionListener {
    public void actionPerformed(ActionEvent e) {
      JButton btn = (JButton) e.getSource();
      if(btn.getText() == "CE") {
    	  input=""; 
    	  inputtf.setText(input);
      }
      else if(btn.getText() == "계산") {
    	  StringTokenizer st=new StringTokenizer(input, "+-x%", true); 
    	  int num1=Integer.parseInt(st.nextToken());
    	  String op=st.nextToken(); 
    	  int num2=Integer.parseInt(st.nextToken()); 
    	  switch(op) { 
    	  case "+" : outputtf.setText(num1+num2+""); 
    	  break; 
    	  case "-" : outputtf.setText(num1-num2+""); 
    	  break; 
    	  case "x" : outputtf.setText(num1*num2+""); 
    	  break; 
    	  case "%" : outputtf.setText(num1/num2+""); 
    	  break; 
    	  } 
      }
      else {
    	  String temp = btn.getText();
    	  input += temp;
    	  inputtf.setText(input);
      }
    }
  }

  class NumPanel extends JPanel {
    public NumPanel() {
      setLayout(new FlowLayout());
      setBackground(Color.GRAY);
      add(new JLabel("수식"));
      add(inputtf);
      add(new JLabel("결과"));
      add(outputtf);
    }
  }
  public static void main(String[] args) {
    new t9b2();
  }
}
```

* 실행 결과

![](https://user-images.githubusercontent.com/10539689/119646880-9f11a580-be5a-11eb-856c-f9aa142166f2.png)