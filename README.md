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
	  add(result, BorderLayout.NORTH);
	}
	
	void showCenter() {
		setLayout(new GridLayout(0,4));
		add(new JButton("%"));
		add(new JButton("ce"));
		add(new JButton("c"));
		add(new JButton("<-"));
		add(new JButton("1/x"));
		add(new JButton("x²"));
		add(new JButton("²√x"));
		add(new JButton("÷"));
		add(new JButton("7"));
		add(new JButton("8"));
		add(new JButton("9"));
		add(new JButton("×"));
		add(new JButton("4"));
		add(new JButton("5"));
		add(new JButton("6"));
		add(new JButton("-"));
		add(new JButton("1"));
		add(new JButton("2"));
		add(new JButton("3"));
		add(new JButton("+"));
		add(new JButton("+/-"));
		add(new JButton("0"));
		add(new JButton("."));
		add(new JButton("="));
		
	}
	

	public static void main(String[] args) {
		new Test();
	}

}
