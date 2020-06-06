Source code below:

import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.regex.Pattern;

public class Main {
    private static final Pattern nonASCII = Pattern.compile("[^\\x00-\\x7f]");
    private static final Pattern nonLETNUM = Pattern.compile("[^a-zA-Z0-9\\s]");
    static GraphicsConfiguration gc;

    public static void main(String[] args){
        JFrame frame= new JFrame(gc);
        frame.setTitle("Gerben's Name disguise checker");
        frame.setSize(600, 400);
        frame.setLocation(200, 200);
        frame.setLayout(new GridLayout(0,2));

        frame.add(new JLabel("Input:"));
        JTextField textField = new JTextField();
        frame.add(textField);
        frame.add(new JLabel(""));
        JButton Test = new JButton("Check Name");
        frame.add(Test);

        JLabel Label_1 = new JLabel("");
        JLabel Label_2 = new JLabel("");
        JLabel Label_3 = new JLabel("");
        JLabel Label_4 = new JLabel("");
        JLabel Label_5 = new JLabel("");
        JLabel Label_6 = new JLabel("");
        Test.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String Input = textField.getText().trim();
                Label_1.setText(Input);
                Label_2.setText(Input.toLowerCase());
                Label_3.setText(nonASCII.matcher(Input).replaceAll(""));
                Label_4.setText(nonASCII.matcher(Input).replaceAll("").toLowerCase());
                Label_5.setText(nonLETNUM.matcher(Input).replaceAll(""));
                Label_6.setText(nonLETNUM.matcher(Input).replaceAll("").toLowerCase());
                frame.setVisible(true);
            }
        });
        frame.add(new JLabel("Name input:"));
        frame.add(Label_1);
        frame.add(new JLabel("Name input (Lowercase):"));
        frame.add(Label_2);
        frame.add(new JLabel("Name input (ASCII only):"));
        frame.add(Label_3);
        frame.add(new JLabel("Name input (ASCII only, Lowercase):"));
        frame.add(Label_4);
        frame.add(new JLabel("Name input (Letters/nums only):"));
        frame.add(Label_5);
        frame.add(new JLabel("Name input (Letters/nums only, lowercase):"));
        frame.add(Label_6);

        frame.setVisible(true);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setResizable(false);
    }
}
