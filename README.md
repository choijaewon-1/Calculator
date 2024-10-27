# Calculator
import java.awt.BorderLayout;
import java.awt.Dimension;
import java.awt.Font;
import java.awt.GridLayout;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextField;

public class Test extends JFrame{
  
	
	Test(){
	  setTitle("계산기");
	  setLayout(new BorderLayout());
	  showNorth(); showCenter();
	  
	  setDefaultCloseOperation(EXIT_ON_CLOSE);
	  setSize(350,450);
	  setVisible(true);
	}
	
	void showNorth() {
		/** 
	 	  * JPanel p1 = new JPanel();
		  *
		  *	JTextField result = new JTextField();
		  *	result.setEditable(false);
		  *
		  *	p1.add(result);
		  *	add(p1, BorderLayout.NORTH);
		  *	
		  * 이 부분에서 텍스트 필드 크기가 딱 맞지않아 남는공간에 맞추고 싶어 ChatGPT 사용
		  */
		JPanel p1 = new JPanel(new BorderLayout()); // @see ChatGPT  p1에 BorderLayout을 적용함 이렇게 하면 텍스트 필드가 p1 패널 내부에서 전체 너비를 차지하게 됩니다.
                                                    // 텍스트 필드를 p1 CENTER에 배치하여 p1 내부에서 전체 너비 채우기 가능 
   
		JTextField result = new JTextField("0");
		result.setEditable(false);
		result.setFont(new Font("Arial", Font.BOLD, 30)); // @see ChatGPT 글꼴과 크기 설정
		result.setHorizontalAlignment(JTextField.RIGHT);  // @see ChatGPT 오른쪽 정렬
		result.setPreferredSize(new Dimension(0, 80));    // @see ChatGPT 높이 설정

		p1.add(result, BorderLayout.CENTER);
		add(p1, BorderLayout.NORTH);
	}
	
	void showCenter() {
		JPanel panel = new JPanel();
		panel.setLayout(new GridLayout(0,4));
		
		JButton b1 = new JButton("%");
		JButton b2 = new JButton("ce");
		JButton b3 = new JButton("c");
		JButton b4 = new JButton("<-");
		JButton b5 = new JButton("1/x");
		JButton b6 = new JButton("x²");
		JButton b7 = new JButton("²√x");
		JButton b8 = new JButton("÷");
		JButton b9 = new JButton("7");
		JButton b10 = new JButton("8");
		JButton b11 = new JButton("9");
		JButton b12 = new JButton("×");
		JButton b13 = new JButton("4");
		JButton b14 = new JButton("5");
		JButton b15 = new JButton("6");
		JButton b16 = new JButton("-");
		JButton b17 = new JButton("1");
		JButton b18 = new JButton("2");
		JButton b19 = new JButton("3");
		JButton b20 = new JButton("+");
		JButton b21 = new JButton("+/-");
		JButton b22 = new JButton("0");
		JButton b23 = new JButton(".");
		JButton b24 = new JButton("=");
		
		panel.add(b1); panel.add(b2); panel.add(b3); panel.add(b4);
		panel.add(b5); panel.add(b6); panel.add(b7); panel.add(b8);
		panel.add(b9); panel.add(b10); panel.add(b11); panel.add(b12);
		panel.add(b13); panel.add(b14); panel.add(b15); panel.add(b16);
		panel.add(b17); panel.add(b18); panel.add(b19); panel.add(b20);
		panel.add(b21); panel.add(b22); panel.add(b23); panel.add(b24);
		
		add(panel, BorderLayout.CENTER);
		
		
	}
	

	public static void main(String[] args) {
		new Test();
	}

}
