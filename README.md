# CP9
## Set up and learn using Google Cloud Flatform
## Explore more about GUI on Eclipse
java
//class events
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JPanel;

public class Events extends JFrame{

	/*
	 * |button| -> |event| -> |listener|
	 */
	
	public Events() {
		JButton sayYesButton = new JButton("Say yes");
		JButton dependsButton = new JButton("It depends");
		JButton wrongButton = new JButton("So wrong");
		
		JPanel panel = new JPanel();
		panel.add(sayYesButton);
		panel.add(dependsButton);
		panel.add(wrongButton);
		
		add(panel);
		
		// create listeners
		YesListenerClass yes = new YesListenerClass();
		sayYesButton.addActionListener(yes);
		
		DependsListenerClass depends = new DependsListenerClass();
		dependsButton.addActionListener(depends);
		
		wrongButton.addActionListener(depends);
		
	}
	
	public static void main(String[] args) {
		JFrame frame = new Events();
		frame.setTitle("Events");
		frame.setLocationRelativeTo(null);
		frame.setSize(200,200);
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.setVisible(true);
		
		
	}
}

//class dependsListener
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class DependsListenerClass implements ActionListener{

	@Override
	public void actionPerformed(ActionEvent e) {
		
		System.out.println("It depends");
		System.out.println(e.getClass());
		System.out.println("When: " + e.getWhen());
		System.out.println(e.getSource());
		System.out.println("Modifier: " + e.getModifiers());
	
	}
}

//class circlePanel
import javax.swing.JPanel;
import java.awt.Graphics;

public class CirclePanel extends JPanel {
	private int radius = 5;
	private boolean flag = true;

	@Override
	protected void paintComponent(Graphics g) {
		super.paintComponent(g);
		if (flag) {
		g.drawOval(getWidth()/2 - radius, getHeight()/2 - radius, 2 * radius, 2 * radius);
		flag = false;
		} else {
			g.drawOval(getWidth()/2 - radius, getHeight()/2 - radius, 2 * radius, 2 * radius);
			flag = true;
	}
			
	}
	
	public void makeBigger() {
		++radius;
		repaint();
	}
}

//class Round
import javax.swing.JButton;
import java.awt.BorderLayout;
import javax.swing.JFrame;
import javax.swing.JPanel;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class Round extends JFrame{

	private JButton makeBigger = new JButton("Bigger");
	private JButton makeSmaller = new JButton("Smaller");
	private CirclePanel canvas = new CirclePanel();
	
	public Round() {
		
		JPanel panel = new JPanel();
		panel.add(makeBigger);
		panel.add(makeSmaller);
		
		add(panel, BorderLayout.SOUTH);
		add(canvas, BorderLayout.CENTER);
		
		makeBigger.addActionListener(new MakeBiggerListener());
		
		/**
		// create listeners
		YesListenerClass yes = new YesListenerClass();
		sayYesButton.addActionListener(yes);
		
		DependsListenerClass depends = new DependsListenerClass();
		dependsButton.addActionListener(depends);
		
		wrongButton.addActionListener(depends);
		*/
	}
	
	public static void main(String[] args) {
		JFrame frame = new Round();
		frame.setTitle("Circles");
		frame.setLocationRelativeTo(null);
		frame.setSize(200,200);
		frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		frame.setVisible(true);
		
		
	}
	
	class MakeBiggerListener implements ActionListener {

		@Override
		public void actionPerformed(ActionEvent e) {
			// TODO Auto-generated method stub
			canvas.makeBigger();
		}
		
	}
}

//class YesListener
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;


public class YesListenerClass implements ActionListener{

	@Override
	public void actionPerformed(ActionEvent e) {
		
		System.out.println("Say yes to CS");
		
	}
	
}
