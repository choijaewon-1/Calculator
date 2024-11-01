# Calculator
import java.awt.BorderLayout;
import java.awt.Dimension;
import java.awt.Font;
import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.ArrayList;

import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.JTextField;

public class Test extends JFrame{
  private JTextField result;
  private String num = "";   // 계산식을 담을 변수
  private String prevOperation = "";
  private ArrayList<String> equation = new ArrayList<String>();
	
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
	        	    String end = Double.toString(calculate(result.getText()));
	        	    result.setText(end);
	        	    num = "";
	         }else if (operation.equals("+/-")) {
	                double symbol = Double.parseDouble(result.getText());
	                result.setText(Double.toString(-symbol));
	         }else if (operation.equals("<-")) {
	                String back = result.getText();
	                if (back.length() > 0) {
	                result.setText(back.substring(0, back.length() - 1));
	                }
	         }else if (operation.equals("x²")) {
	                double square  = Double.parseDouble(result.getText());
	                result.setText(Double.toString(square  * square ));
	         }else if(operation.equals("+") || operation.equals("-")  // 유튜브 참조 계산식이 비어있을 때 연산자 중복 입력과 연산자 처리와 비어있지 않을 때 처리
	        		 || operation.equals("×") || operation.equals("÷")
	        		 || operation.equals("x²") || operation.equals("+/-")) {
	        	 if(result.getText().equals("") && operation.equals("-")) {
		        	result.setText(result.getText() + e.getActionCommand());
	        	 } else if(!result.getText().equals("") && !prevOperation.equals("+") && !prevOperation.equals("-")
	        		&& !prevOperation.equals("×") && !prevOperation.equals("÷")
		        	&& !prevOperation.equals("x²") && !prevOperation.equals("+/-")) {
	        		result.setText(result.getText() + e.getActionCommand());
	        	 }
	         }else {
	        	result.setText(result.getText() + e.getActionCommand());
	         }
	         prevOperation = e.getActionCommand();
	     }
	 }
	 private void calculator(String result) {
		 equation.clear();
		 
		 for(int i = 0; i < result.length(); i++) { // 유튜브 참조
			 char ch = result.charAt(i);
			 
			 if(ch == '-' | ch == '+' | ch == '×' | ch == '÷' ) {
				equation.add(num);
				num = "";
				equation.add(ch + "");
			 } else {
				 num = num + ch;
			 }
		 }
		 equation.add(num);
		 equation.remove("");
	 }
    public double calculate(String result) {
    	calculator(result);
    	
    	double prev = 0;
    	double current = 0;
    	String mode = "";
    	
    	for (String s : equation) {
    		if(s.equals("+")) {
    			mode = "add";
    		} else if(s.equals("-")){
    			mode = "sub";
    		} else if(s.equals("×")){
    			mode = "mul";
    		} else if(s.equals("÷")){
    			mode = "div";
    		} else {
    			current = Double.parseDouble(s);
    			if(mode ==  "add") {
    			   prev += current;       
    			} else if (mode == "sub") {
    			   prev -= current;
    			} else if (mode == "mul") {
    			   prev *= current;
    			} else if (mode == "div") {
    				if (current == 0) {
    	                return 0;
    	            } else {
    	                prev /= current;
    	            }
    			} else {
    				prev = current;
    			}
    		}
    		prev = Math.round(prev * 100000) / 100000.0; // 소숫점 반올림
    	}
		return prev;
	}
	public static void main(String[] args) {
		new Test();
	}
}
