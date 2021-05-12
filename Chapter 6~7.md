# 명품 자바프로그래밍 6, 7장

## 6장

* 1번 문제

  > 다음 main()의 실행 결과 클래스명과 점 값을 연결하여 “MyPoint(3,20)”이 출력되도록 MyPoint 클래스를 작성하라.

  * 소스코드

    ```java
    class MyPoint{
    	int x, y;
    	public MyPoint(int x, int y) {
    		this.x = x;
    		this.y = y;
    	}
    	public String toString() {
    		return getClass().getName() + "(" + x+", "+y+")";
    	}
    }
    public class ex61
    {
    	public static void main(String[] args)
    	{
    		MyPoint a = new MyPoint(3,20);
    		System.out.println(a);
    	}
    }
    ```

  * 실행 결과

      ![](https://user-images.githubusercontent.com/10539689/117139959-c3dca500-ade7-11eb-98f5-7880ec985a1f.jpg)  

* 2번 문제

  > Scanner를 이용하여 한 라인을 읽고, 공백으로 분리된 어절이 몇 개인지 출력을 반복하는 프로그램을 작성하라. “exit”이 입력되면 종료한다.
  >

  * 소스코드

    ```java
    import java.util.Scanner;
    import java.util.StringTokenizer;
    
    public class ex62
    {
    	public static void main(String[] args)
    	{
    		String t;
    		Scanner s = new Scanner(System.in);
    		while(true) {
    			t = s.nextLine();
    			if(t.equals("exit"))
    				break;
    			StringTokenizer st = new StringTokenizer(t," ");
    			int n = st.countTokens();
    			System.out.printf("어절 개수는 %d\n",n);
    		}
    		System.out.println("종료합니다.");
    		s.close();
    	}
    }
    ```

  * 실행 결과

    ![](https://user-images.githubusercontent.com/10539689/117139952-c3440e80-ade7-11eb-81a7-4d0dae04d2af.jpg)  

* 3번 문제

  > 1에서 3까지의 난수를 3개 생성한 뒤 나란히 한 줄에 출력하라. 모두 같은 수가 나올때까지 반복 출력하고, 모두 같은 수이면 “성공”을 출력하고 종료하는 프로그램을 작성하라.

  * 소스코드

    ```java
    public class ex63
    {
    	public static void main(String[] args)
    	{
    		int x,y,z;
    		while(true) {
    			x = (int) (Math.random() * 3 + 1); 
    			y = (int) (Math.random() * 3 + 1); 
    			z = (int) (Math.random() * 3 + 1);
    			System.out.printf("%d\t%d\t%d\n", x,y,z);
    			if(x == y && y == z)
    				break;
    		}
    		System.out.printf("성공");
    	}
    }
    ```
    
  * 실행 결과
  
    ​    ![](https://user-images.githubusercontent.com/10539689/117139956-c3440e80-ade7-11eb-8efa-5cdc99ee304a.jpg)  
  
* 4번 문제

  > 다음과 같이 +로 연결된 덧셈식을 입력받아 덧셈 결과를 출력하는 프로그램을 작성하라. StringTokenizer와 Integer.parseInt().String의 trim()을 활용하라.
  >

  * 소스코드

    ```java
    import java.util.Scanner;
    import java.util.StringTokenizer;
    
    public class ex64
    {
    	public static void main(String[] args) {
    		int re = 0;
    		String t;
    		Scanner s = new Scanner(System.in);
    		t = s.nextLine();		
    		StringTokenizer st = new StringTokenizer(t,"+");
    		
    		while(st.hasMoreTokens()) { //토큰 존재시 true 리턴
    			String temp = st.nextToken();
    			String num = temp.trim(); // 공백제거
    			re += Integer.parseInt(num);
    		}
    		System.out.printf("합은 %d",re);
    
    	}
    }
    ```

  * 실행 결과

       ![](https://user-images.githubusercontent.com/10539689/117139950-c2ab7800-ade7-11eb-898e-c9e66707c545.jpg)  

* 5번 문제

  > 다음 코드를 수정하여 Adder 클래스는 util 패키지에, Main 클래스는 app 패키지에 작성하여 응용프로그램을 완성하고 실행시켜라.
  >

  * 소스코드

    ```java
    package util;
    public class Adder
    {
    	private int x, y;
    	public Adder(int x, int y) {this.x = x; this.y = y;}
    	public int add() { return x + y; }
    }
    ```

    ```java
    package app;
    import util.Adder;
    public class ex65
    {
    	public static void main(String[] args)
    	{
    		Adder adder = new Adder(2,5);
    		System.out.println(adder.add());
    	}
    }
    ```

  * 실행 결과

    ​    ![](https://user-images.githubusercontent.com/10539689/117139957-c3dca500-ade7-11eb-948f-bcbc9cc9c785.jpg)  

* 6번 문제

  > Math.random()의 난수 발생기를 이용하여 사용자와 컴퓨터가 하는 가위바위보 게임을 만들어보자. 가위, 바위, 보는 각각 1, 2, 3 키이다. 사용자가 1, 2, 3, 키 중 하나를 입력하면 동시에 프로그램에서 난수 발생기를 이용하여 1, 2, 3 중에 한 수를 발생시켜 컴퓨터가 낸 것을 결정한다. 그리고 사용자와 컴퓨터 둘 중 누가 이겼는지를 판별하여 승자를 출력한다.
  >
  
  * 소스코드
  
    ```java
    import java.util.Scanner;
    
    class Computer{
    	private int selection;
    	public Computer() {
    		selection = (int) (Math.random()*3+1);
    	}
    	public void reroll() {
    		selection = (int) (Math.random()*3+1);
    	}
    	public int show() {return selection;}
    }
    
    public class ex66
    {
    	public static void main(String[] args) {
    		int p;
    		Computer c = new Computer();
    		Scanner s = new Scanner(System.in);
    		while(true) {
    			System.out.printf("가위(1) 바위(2) 보(3) 끝내기(4)>>");
    			p = s.nextInt();
    			if(p==4)
    				break;
    			c.reroll();
    			switch (c.show()) {
    			case 1:
    				if(p == 1) {
    					System.out.printf("사용자 가위 : 컴퓨터 가위\n비겼습니다.\n");
    				}
    				else if(p == 2) {
    					System.out.printf("사용자 바위 : 컴퓨터 가위\n이겼습니다.\n");
    				}
    				else if(p == 3) {
    					System.out.printf("사용자 보 : 컴퓨터 가위\n졌습니다.\n");
    				}
    				break;
    			case 2:
    				if(p == 1) {
    					System.out.printf("사용자 가위 : 컴퓨터 바위\n이겼습니다.\n");
    				}
    				else if(p == 2) {
    					System.out.printf("사용자 바위 : 컴퓨터 바위\n비겼습니다.\n");
    				}
    				else if(p == 3) {
    					System.out.printf("사용자 보 : 컴퓨터 바위\n졌습니다.\n");
    				}
    				break;
    			case 3:
    				if(p == 1) {
    					System.out.printf("사용자 가위 : 컴퓨터 보\n이겼습니다.\n");
    				}
    				else if(p == 2) {
    					System.out.printf("사용자 바위 : 컴퓨터 보\n졌습니다.\n");
    				}
    				else if(p == 3) {
    					System.out.printf("사용자 보 : 컴퓨터 보\n비겼습니다.\n");
    				}
    				break;
    			}
    		}
    		System.out.println("게임을 종료합니다..");
    		
    	}
    }
    ```
  
  * 실행 결과
  
      ![](https://user-images.githubusercontent.com/10539689/117139960-c4753b80-ade7-11eb-8e64-e91376275707.png)
---
## 7장

* 1번 문제

  > Scanner를 사용하여 5개의 실수 값을 사용자로부터 입력받아 벡터에 저장하라. 그러고 나서 벡터를 검색하여 가장 큰 수를 출력하는 프로그램을 작성하라.

  * 소스코드

    ```java
    import java.util.*;
    public class vectormax
    {
    
    	public static void main(String[] args)
    	{
    		double max = 0;
    		Vector<Double> v = new Vector<Double>();
    		Scanner s = new Scanner(System.in);
    		for(int i=1; i <= 5;i++) {
    			v.add(s.nextDouble()); 
    			
    		}
    		for(int i = 0; i < 4; i++) {
    			if(v.get(i) > v.get(i+1))
    				max = v.get(i);
    		}
    		System.out.println("가장 큰 수 : " + max);
    	}
    
    }
    ```

  * 실행 결과

    ![image-20210505165917554](https://user-images.githubusercontent.com/10539689/117139962-c4753b80-ade7-11eb-8e8d-7e6ed7221058.png)

* 2번 문제

  > Scanner를 사용하여 학점('A','B','C','D','F')을 5개만 문자로 입력받아 ArrayList에 저장하라. 그러고 나서 다시 ArrayList를 검색하여 5개의 학점을 점수 (A=4.0,B=3.0,C=2.0,D=1.0,F=0.0)로 변환하여 출력하는 프로그램을 작성하라.

  * 소스코드

    ```java
    import java.util.ArrayList;
    import java.util.Scanner;
    
    public class Grade
    {
    	public static void main(String[] args)
    	{
    		ArrayList<Character> arraylist = new ArrayList<Character>();
    		Scanner s = new Scanner(System.in);
    		System.out.print("빈 칸으로 분리하여 5 개의 학점을 입력(A/B/C/D/F)>>");
    		for(int i = 0; i <= 4; i++) {
    			String st = s.next();
    			char ch = st.charAt(0);
    			arraylist.add(ch);
    		}
    		for(int i = 0; i <= 4; i++) {
    			switch(arraylist.get(i)) {
    			case 'A':
    				System.out.print("4.0 ");
    				break;
    			case 'B':
    				System.out.print("3.0 ");
    				break;
    			case 'C':
    				System.out.print("2.0 ");
    				break;
    			case 'D':
    				System.out.print("1.0 ");
    				break;
    			case 'F':
    				System.out.print("0.0 ");
    				break;
    			}
    		}
    	}
    }
    ```

  * 실행 결과

    ![image-20210505210749135](https://user-images.githubusercontent.com/10539689/117139938-c0e1b480-ade7-11eb-9011-525ec6a1e2d9.png)

* 3번 문제
  
  > HashMap<String, Integer> 컬렉션을 생성하고 “에스프레소”는 2000, “아메리카노”는 2500, “카푸치노”는 3000, “카페라테”는 3500을 저장하라. 그리고 다음과 같이 음료수 이름을 입력받으면 HashMap에서 검색하여 가격을 출력하라.
  
  * 소스코드
  
    ```java
    import java.util.*;
    
    public class hashcafe
    {
    	public static void main(String[] args)
    	{
    		Scanner s = new Scanner(System.in);
    		//C# 딕셔너리? 
    		HashMap<String, Integer> menu = new HashMap<String, Integer>();
    		
    		menu.put("에스프레소", 2000);
    		menu.put("아메리카노", 2500);
    		menu.put("카푸치노", 3000);
    		menu.put("카페라떼", 3500);
    		String order;
    		System.out.println("에스프레소, 아메리카노, 카푸치노, 카페라떼 있습니다.");
    		while(true) {
    		System.out.print("주문>> ");
    		order = s.next();
    		if(order.equals("그만"))
    			break;
    		System.out.println(order+"는 "+menu.get(order)+"입니다.");
    		}
    	}
    }
    ```
  
  * 실행 결과
  
    ![image-20210505210820032](https://user-images.githubusercontent.com/10539689/117139939-c0e1b480-ade7-11eb-90ab-98f54c505a11.png)
  
* 4번 문제
  
  > 한 어린이의 키를 2000년부터 2009년 사이에 1년 단위로 입력받아 벡터에 저장하라. 그리고 가장 키가 많이 자란 연도를 출력하라.
  
  * 소스코드
  
    ```java
    import java.util.Scanner;
    import java.util.Vector;
    
    public class grow
    {
    	public static void main(String[] args)
    	{
    		Scanner s = new Scanner(System.in);
    		Vector<Double> data = new Vector<Double>();
    		double max = 0;
    		int index = 0;
    	
    		System.out.println("2000~2009년까지 1년 단위로 키(cm) 입력");
    		System.out.print(">> ");
    		for(int i = 0;i <= 9;i++) {
    			data.add(s.nextDouble());
    		}
    		for(int i = 0; i < 9; i++) {
    			if(max < (data.get(i+1) - data.get(i))){
    				max = data.get(i+1) - data.get(i);
    				index = i;
    			}
    		}	
    		System.out.println("가장 키가 많이 자란 년도는 200"+index+"년"+max+"cm");
    	}
    }
    ```
  
  * 실행 결과
  
    ![image-20210505211010068](https://user-images.githubusercontent.com/10539689/117139940-c17a4b00-ade7-11eb-8484-adf2069a5736.png)
  
* 5번 문제
  
  > 5개 나라 이름과 인구를 입력받아 해시맵에 저장하고, 가장 인구가 많은 나라를 검색하여 출력하는 프로그램을 작성하라. 이때 다음 해시맵을 이용하라.
  
  * 소스코드
  
    ```java
    import java.util.*;
    public class pdata
    {
    	public static void main(String[] args)
    	{
    		Scanner s = new Scanner(System.in);
    		int max = 0;
    		String maxflag = null;
    		HashMap<String, Integer> flag = new HashMap<String, Integer>();
    		System.out.println("나라 이름과 인구를 5개 입력하세요.(예 Korea 5000)");
    		for(int i = 0; i < 5;i++) {
    			System.out.print("나라 이름, 인구 >> ");
    			flag.put(s.next(), s.nextInt());
    		}
    		Set<String> keys = flag.keySet();
    		Iterator<String> t = keys.iterator();
    		//왜 이거 안하고 직접 지정하면 오류...?
    		while(t.hasNext()) {
    			String key = t.next();
    			int v = flag.get(key);
    			if(max < v) {
    				max = v;
    				maxflag = key;
    			}
    		}
    		System.out.print("제일 인구가 많은 나라는 (" + maxflag +","+ max+")");
    		s.close();
    	}
    }
    ```
  
  * 실행 결과
  
    ![image-20210505211107196](https://user-images.githubusercontent.com/10539689/117139942-c17a4b00-ade7-11eb-8576-000627481981.png)
  
* 6번 문제
  
  > 고객의 이름과 포인트 점수를 관리하는 프로그램을 해시맵을 이용하여 작성하라. 이 프로그램은 고객의 이름과 포인트를 누적하여 관리한다. 한 고객의 입력이 끝나면 현재까지의 모든 고객의 포인트 점수를 출력한다.
  
  * 소스코드
  
    ```java
    import java.util.*;
    public class pointm
    {
    	public static void main(String[] args)
    	{
    		Scanner s = new Scanner(System.in);
    		String user = null;
    		HashMap<String, Integer> point = new HashMap<String, Integer>();
    		System.out.println("** 포인트 관리 프로그램입니다 **");
    		
    		while(true) {
    			System.out.print("\n이름과 포인트 입력>> ");
    			user = s.next();
    			if(user.equals("exit"))
    				break;
    			int temp_point = s.nextInt();
    			
    			if(point.containsKey(user)) {
    				point.put(user, point.get(user) + temp_point);
    				//수정법이 좀 특이하네...
    			}
    			else
    			{
    				point.put(user, temp_point);
    			}
    			Set<String> keys = point.keySet();
    			Iterator<String> t = keys.iterator();
    			while(t.hasNext()) {
    				String k = t.next();
    				int v = point.get(k);
    				System.out.print("("+ k + ", " + v + ")");
    			}
    		}
    		System.out.println("종료합니다...");
    	}
    }
    ```
  
  * 실행 결과
  
    ![image-20210505211348263](https://user-images.githubusercontent.com/10539689/117139948-c212e180-ade7-11eb-8f45-10fc8238bbb4.png)
  
* 7번 문제
  
  > Location 클래스는 2차원 평면에서 하나의 위치(x, y)를 표현한다. Location 객체로 쥐가 이동한 각 위치를 저장하고 이들로부터 총 이동 거리를 구하고자 한다. ArrayList 컬렉션에 쥐의 위치(Location 객체)를 5개 입력받아 삽입한 후 총 길이를 구하여라. 시작 위치는 (0, 0)이며, (0, 0) 위치로 돌아온다.
  
  * 소스코드
  
    ```java
    import java.util.*;
    class Location{
    	private int x,y;
    	public Location(int x, int y) {
    		this.x = x;
    		this.y = y;
    	}
    	public double calc(Location b) {
    		double dis = Math.pow((x - b.x),2) + Math.pow((y - b.y),2);
    		return Math.sqrt(dis); //뺀거 제곱 + 제곱 제급근 거리 공식
    	}
    }
    public class dist
    {
    	public static void main(String[] args)
    	{
    		ArrayList<Location> mouse = new ArrayList<Location>();
    		Scanner s = new Scanner(System.in);
    		mouse.add(new Location(0,0));
    		System.out.println("쥐가 이동한 위치(x,y)를 5개 입력하라.");
    		for(int i=0; i<5; i++) {
    			System.out.print(">> ");
    			int x = s.nextInt();
    			int y = s.nextInt();
    			mouse.add(new Location(x,y));
    		}
    		mouse.add(new Location(0,0));
    		
    		double sum = 0.0;
    		for(int i = 0; i<mouse.size()-1;i++) {
    			double t = mouse.get(i).calc(mouse.get(i+1));
    			sum += t;
    	}
    		System.out.println("총 이동 거리는 " + sum);
    	}
    }
    ```
  
  * 실행 결과
  
    ![image-20210505211419653](https://user-images.githubusercontent.com/10539689/117139949-c2ab7800-ade7-11eb-8e1b-37cf7c928a0e.png)
