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
  JTextField result;
	
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
	  JPanel p1 = new JPanel(new BorderLayout());       // @see ChatGPT  p1에 BorderLayout을 적용함
                                                            // 텍스트 필드를 p1 CENTER에 배치하여 p1 내부에서 전체 너비 채우기 가능 
	  result = new JTextField();
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
	  
	  String[] buttons = {"%", "CE", "C", "<-", "1/x", "x²", "√x", "÷",
              "7", "8", "9", "×", "4", "5", "6", "-", 
              "1", "2", "3", "+", "+/-", "0", ".", "="};         // 교재177p 참조
	  
	  for (String text : buttons) {
          JButton button = new JButton(text);			 // 교재185p 참조import java.awt.BorderLayout;
import java.awt.Dimension;
import java.awt.Font;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextField;

public class Test extends JFrame{
  JTextField result;
	
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
	  JPanel p1 = new JPanel(new BorderLayout());       // @see ChatGPT  p1에 BorderLayout을 적용함
                                                        // 텍스트 필드를 p1 CENTER에 배치하여 p1 내부에서 전체 너비 채우기 가능 
	  result = new JTextField();
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
	  
	  String[] buttons = {"x²", "÷", "C", "<-",
              "7", "8", "9", "×", "4", "5", "6", "-",
              "1", "2", "3", "+", "+/-", "0", ".", "="}; // 교재177p 참조
	  
	  for (String text : buttons) {
          JButton button = new JButton(text);			 // 교재185p 참조
          button.addActionListener(new ButtonClickListener());
          panel.add(button);
      }
      add(panel, BorderLayout.CENTER);
    }
	 class ButtonClickListener implements ActionListener {//액션리스너 만들어서 버튼에 추가 유튜브 참조
	     public void actionPerformed(ActionEvent e) {
	         String operation = e.getActionCommand();
	         if(operation.equals("C")){
	        	result.setText("");
	         }else if (operation.equals("=")) {
	        	 
	         }else {
	        	result.setText(result.getText() + e.getActionCommand());
	         }
	     }
	 }

	public static void main(String[] args) {
		new Test();
	}
}

          
          panel.add(button);
      }
      add(panel, BorderLayout.CENTER);
    }

	public static void main(String[] args) {
		new Test();
	}
}
