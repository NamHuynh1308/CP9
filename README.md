# CP9
# Set up and learn using Google Cloud Flatform
# Explore more about GUI on Eclipse
java
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
