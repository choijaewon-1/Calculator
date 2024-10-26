# Calculator
import java.awt.BorderLayout;

import javax.swing.JFrame;
import javax.swing.JTextArea;

public class Test extends JFrame{
  
	
	Test(){
	  setTitle("계산기");
	  setLayout(new BorderLayout());
	  setDefaultCloseOperation(EXIT_ON_CLOSE);
	  setSize(350,450);
	  setVisible(true);
	  
	  JTextArea result = new JTextArea();
	  result.setEditable(false);
	  add(result, BorderLayout.NORTH);
	  
  }
	

	public static void main(String[] args) {
		new Test();
	}

}
