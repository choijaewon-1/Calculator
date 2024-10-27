# Calculator
import java.awt.BorderLayout;
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
	  JPanel p1 = new JPanel();
	  
	  JTextField result = new JTextField();
	  result.setEditable(false);
	  
	  p1.add(result);
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
