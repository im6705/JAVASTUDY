## 8장

* OpenChallenge

  > 다음 그림과 같은 간단한 스윙 프로그램을 작성하라. 이 프로그램은 컨텐트팬이 BorderLayout 배치관리자를 가지며, NORTH 영역과 CENTER 영역에 각각 JPanel을 상속받은 패널을 붙인다. NORTH 영역의 패널에는 3개의 버튼 커포넌트를, CENTER 영역의 패널에는 "Hello Java!" 문자열을 가진 JLabel 컴포넌트를 100*20 크기로, (100,50) 위치에 붙인다.
  
  * 소스코드
  
    ```java
    import java.awt.*;
    import javax.swing.*;
    
    class NorthPanel extends JPanel{
    	public NorthPanel() {
    		setBackground(Color.GRAY); 
    		setLayout(new FlowLayout());
    		add(new JButton("Open"));
    		add(new JButton("Read"));
    		add(new JButton("Close")); 
    	}
    }
    
    class CenterPanel extends JPanel{
    	public CenterPanel() {
    		setLayout(null);
    		JLabel label = new JLabel("Hello Java!");
    		label.setSize(100,20);
    		label.setLocation(100, 50);
    		add(label);
    	}
    }
    
    public class oc8 extends JFrame
    {
    	
    	public oc8() {
    		super("Open Challenge 8");
    		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    		add(new NorthPanel(), BorderLayout.NORTH);
    		add(new CenterPanel(), BorderLayout.CENTER);
    		setSize(500,300);
    		setVisible(true);
    	}
    
    	public static void main(String[] args)
    	{
    		new oc8();
    	}
    
    }
    ```
  
  * 실행 결과
  
      ![image-20210512184440600](https://user-images.githubusercontent.com/10539689/117964942-31934e80-b35d-11eb-9024-df057fb31a5f.png)
  
* 1번 문제

  > 다음 그림과 같이 "Let's study"
  
  * 소스코드
  
    ```java
    import java.awt.*;
    import javax.swing.*;
    
    public class t81 extends JFrame
    {	
    	public t81() {
    		this.setTitle("Let's study Java");
    		this.setSize(400, 200);
    		this.setVisible(true);
    		this.setLocationRelativeTo(this.getParent());
    		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    		}
    
    	public static void main(String[] args)
    	{
    		new t81();
    	}
    }
    ```
  
  * 실행 결과
  
    ![image-20210512185532851](https://user-images.githubusercontent.com/10539689/117964945-322be500-b35d-11eb-89a5-61c91aa02a55.png)
  
* 2번 문제

  > BorderLayout을 사용하여 컴포넌트 사이의 수평 간격이 50픽셀, 수직 간격이 5픽셀이 되도록 다음 그림과 같은 스윙 응용프로그램을 작성하라.

  * 소스코드

    ```java
    import java.awt.*;
    import javax.swing.*;
    
    public class t82 extends JFrame
    {	
    	public t82() {
    		this.setTitle("BorderLayout Practice");
    		this.setLayout(new BorderLayout(50,5));
    		this.setSize(400, 200);
    		JButton bn = new JButton("NORTH");
    		JButton bw = new JButton("WEST");
    		JButton bs = new JButton("SOUTH");
    		JButton be = new JButton("EAST");
    		JButton bc = new JButton("CENTER");
    	
    		this.add(bn,BorderLayout.NORTH);
    		this.add(bw,BorderLayout.WEST);
    		this.add(bs,BorderLayout.SOUTH);
    		this.add(be,BorderLayout.EAST);
    		this.add(bc,BorderLayout.CENTER);
    		this.setVisible(true);
    		this.setLocationRelativeTo(this.getParent());
    		this.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    		}
        
    	public static void main(String[] args)
    	{
    		new t82();
    	}
    }
    ```
    
  * 실행 결과
  
    ​    ![image-20210512190324324](https://user-images.githubusercontent.com/10539689/117964946-32c47b80-b35d-11eb-8006-b699056b7277.png)
  
* 3번 문제

  > 컨텐트팬에 FlowLayout 배치관리자를 지정하고 그림과 같이 JLabel과 JButton 컴포넌트를 이용하여 산술문을 출력하는 스윙 프로그램을 작성하라.
  
  * 소스코드
  
    ```java
    import java.awt.*;
    import javax.swing.*;
    
    public class t83 extends JFrame
    {	
    	public t83() {
    		this.setTitle("FlowLayout Practice");
    		Container contentPane = getContentPane();
    		contentPane.setLayout(new FlowLayout());
    		setSize(400, 200);
    		JButton bcal = new JButton("=");
    		contentPane.add(new JLabel("100"));
    		contentPane.add(new JLabel("+"));
    		contentPane.add(new JLabel("200"));
    		contentPane.add(bcal);
    		contentPane.add(new JLabel("300"));
    		setVisible(true);
    		setLocationRelativeTo(this.getParent());
    		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    		}
    	public static void main(String[] args)
    	{
    		new t83();
    	}
    }
    ```
  
  * 실행 결과
  
       ![image-20210512191339177](https://user-images.githubusercontent.com/10539689/117964948-32c47b80-b35d-11eb-9266-72e6fe6f6d81.png)
  
* 4번 문제

  > 예제 8-5의 소스 코드를 수정하여 각 버튼의 배경색을 다음 그림과 같이 설정하라.
  
  ```java
  contentPane.setLayout(new GridLayout(row,col));
  ```
  
  ```java
  Color [] color = {Color.RED, Color.ORANGE, Color.YELLOW, Color.GREEN, Color.CYAN, Color.BLUE, Color.MAGENTA, Color.GRAY, Color.PINK, Color.LIGHT_GRAY};
  ```
  
  ```java
  for(int i=0; i<10; i++){
      JButton button = new JButton(Integer.toString(i));
      button.setOpaque(true);
      button.setBackground(color[i]);
      contentPane.add(button);
  }
  ```
  
  
  
  * 소스코드
  
    ```java
    import java.awt.*;
    import javax.swing.*;
    
    public class t84 extends JFrame
    {
    	Color[] color = {Color.RED, Color.ORANGE, Color.YELLOW, Color.GREEN, 
    			Color.CYAN, Color.BLUE, Color.MAGENTA, Color.GRAY, Color.PINK,
    			Color.LIGHT_GRAY};
    	public t84() {
    		super("Ten Color Buttons Frame");
    		
    		Container con = getContentPane();
    		con.setLayout(new GridLayout(1,10));
    		for(int i = 0; i < 10; i++) {
    			JButton button = new JButton(Integer.toString(i));
    		    button.setOpaque(true);
    		    button.setBackground(color[i]);
    		    con.add(button);
    		}
    		setVisible(true);
    		setSize(1000,500);
    		setLocationRelativeTo(this.getParent());
    		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    	}
    
    	public static void main(String[] args)
    	{
    		new t84();
    	}
    }
    ```
  
  * 실행 결과
  
    ![image-20210512192647722](https://user-images.githubusercontent.com/10539689/117964949-32c47b80-b35d-11eb-8ab2-37895b889379.png)
  
* 5번 문제

  > Math.random()의 난수 발생기를 이용하여 사용자와 컴퓨터가 하는 가위바위보 게임을 만들어보자. 가위, 바위, 보는 각각 1, 2, 3 키이다. 사용자가 1, 2, 3, 키 중 하나를 입력하면 동시에 프로그램에서 난수 발생기를 이용하여 1, 2, 3 중에 한 수를 발생시켜 컴퓨터가 낸 것을 결정한다. 그리고 사용자와 컴퓨터 둘 중 누가 이겼는지를 판별하여 승자를 출력한다.

  * 소스코드

    ```java
    import java.awt.*;
    import javax.swing.*;
    
    public class t85 extends JFrame
    {
    	Color[] color = {Color.RED, Color.ORANGE, Color.YELLOW, Color.GREEN, 
    			Color.CYAN, Color.BLUE, Color.MAGENTA, Color.GRAY, Color.PINK,
    			Color.LIGHT_GRAY, Color.WHITE, Color.DARK_GRAY, Color.BLACK,
    			Color.BLUE, Color.MAGENTA, Color.GRAY};
    	public t85() {
    		super("4X4 Color Frame");
    		
    		Container con = getContentPane();
    		con.setLayout(new GridLayout(4,4));
    		for(int i = 0; i < 16; i++) {
    			JLabel lbl = new JLabel(Integer.toString(i));
    			lbl.setOpaque(true);
    			lbl.setBackground(color[i]);
    		    con.add(lbl);
    		}
    		setVisible(true);
    		setSize(1000,500);
    		setLocationRelativeTo(this.getParent());
    		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    	}
    
    	public static void main(String[] args)
    	{
    		new t85();
    	}
    }
    ```
    
  * 실행 결과

      ![image-20210512193449465](https://user-images.githubusercontent.com/10539689/117964950-335d1200-b35d-11eb-9853-5199a40ced5d.png)


* 6번 문제

  > 0~19까지의 정수 20개를 프레임 내의 (30, 30)에서 (250, 250) 영역 내 랜덤한 위치에 출력하는 스윙 프로그램을 작성하라. 프레임의 크기를 300X300으로 하고, 정수는 JLabel을 이용하여 출력하고 크기는 20X20으로 한다.

  * 소스코드

    ```java
    import java.awt.*;
    import javax.swing.*;
    
    
    public class t86 extends JFrame
    {
    	public t86() {
    		super("Random Labels");
    		Container con = getContentPane();
    		con.setLayout(null);
    		
    		for(int i = 0; i < 20;i++) {
    			JLabel lbl = new JLabel(Integer.toString(i));
    			int x = (int)(Math.random()*220) +30;
    			int y = (int)(Math.random()*220) +30;
    			lbl.setLocation(x,y);
    			lbl.setForeground(Color.MAGENTA);
    			lbl.setSize(20, 20);
    			con.add(lbl);
    		}
    		setSize(300,300);
    		setVisible(true);
    		setLocationRelativeTo(this.getParent());
    		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    	}
    	public static void main(String[] args)
    	{
    		new t86();
    	}
    }
    ```

  * 실행 결과

    ![image-20210512194218780](https://user-images.githubusercontent.com/10539689/117964952-33f5a880-b35d-11eb-9f31-9bfa7fd7f0b4.png)

* 7번 문제

  > Open Challenge의 힌트나 정답을 참고하여 컨텐트팬에 3개의 패널을 부착한 프로그램을 작성하라. CenterPanel에는 10개의 JLabel을 이용하여 10개의 '*'를 랜덤한 위치에 출력하라.
  
  * 소스코드
  
    ```java
    import java.awt.*;
    import javax.swing.*;
    
    class NorthPanel extends JPanel{
    	public NorthPanel() {
    		setBackground(Color.YELLOW); 
    		setLayout(new FlowLayout());
    		add(new JButton("새로 배치"));
    		add(new JButton("종료"));
    	}
    }
    
    class CenterPanel extends JPanel{
    	public CenterPanel() {
    		setLayout(null);
    		for(int i = 0; i < 10;i++) {
    			JLabel lbl = new JLabel("*");
    			int x = (int)(Math.random()*220) + 30;
    			int y = (int)(Math.random()*200) + 30;
    			lbl.setLocation(x,y);
    			lbl.setForeground(Color.MAGENTA);
    			lbl.setSize(20, 20);
    			add(lbl);
    		}
    	}
    }
    
    class BottomPanel extends JPanel{
    	public BottomPanel() {
    		setLayout(new FlowLayout(FlowLayout.LEFT));
    		setBackground(Color.GRAY);
    		JButton button = new JButton("별 개수 수정"); 
    		JTextField field = new JTextField(10);
    		add(button);
    		add(field);
    	}
    }
    
    public class t87 extends JFrame
    {
    	
    	public t87() {
    		super("3 PANEL");
    		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
    		add(new NorthPanel(), BorderLayout.NORTH);
    		add(new CenterPanel(), BorderLayout.CENTER);
    		add(new BottomPanel(), BorderLayout.SOUTH);
    		setSize(500,300);
    		setVisible(true);
    	}
    
    	public static void main(String[] args)
    	{
    		new t87();
    	}
    }
    ```
    
  * 실행 결과
  
      ![image-20210512195838772](https://user-images.githubusercontent.com/10539689/117964953-33f5a880-b35d-11eb-9b95-fe0c471781cb.png)
---