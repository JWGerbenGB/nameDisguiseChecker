import javax.swing.*;
import java.awt.*;
import java.awt.event.*;
import java.util.regex.Pattern;

public class M {

    public static void main(String[] args){
        int I = 0;
        String p = "Name input";
        Pattern a = Pattern.compile("[^\\x00-\\x7f]");
        Pattern b = Pattern.compile("[^a-zA-Z0-9\\s]");
        JFrame f= new JFrame();
        f.setTitle("Gerben's Name disguise checker");
        f.setSize(600, 400);
        f.setLocation(200, 200);
        f.setLayout(new GridLayout(0,2));

        f.add(new JLabel("Input:"));
        JTextField t = new JTextField();
        f.add(t);
        f.add(new JLabel(""));
        JButton Test = new JButton("Check Name");
        f.add(Test);

        JLabel[] l = new JLabel[6];
        for(int i = 0; i < 6; i++){
            l[i] = new JLabel("");
        }

        Test.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String i = t.getText().trim();
                l[0].setText(i);
                l[1].setText(i.toLowerCase());
                l[2].setText(a.matcher(i).replaceAll(""));
                l[3].setText(a.matcher(i).replaceAll("").toLowerCase());
                l[4].setText(b.matcher(i).replaceAll(""));
                l[5].setText(b.matcher(i).replaceAll("").toLowerCase());
                f.setVisible(true);
            }
        });
        f.add(new JLabel(p+":"));
        f.add(l[I++]);
        f.add(new JLabel(p+" (Lowercase):"));
        f.add(l[I++]);
        f.add(new JLabel(p+" (ASCII only):"));
        f.add(l[I++]);
        f.add(new JLabel(p+" (ASCII only, Lowercase):"));
        f.add(l[I++]);
        f.add(new JLabel(p+" (Letters/nums only):"));
        f.add(l[I++]);
        f.add(new JLabel(p+" (Letters/nums only, lowercase):"));
        f.add(l[I++]);

        f.setVisible(true);
        f.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        f.setResizable(false);
    }
}
