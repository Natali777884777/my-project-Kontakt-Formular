package contactForm;

import javax.swing.*;
import java.awt.*;

import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class Form extends JFrame {

    private JTextField name_field;
    JTextField email_field;

    JRadioButton male, female;

    JCheckBox check;


    public Form() {
        super("Kontakt-Formular");
        super.setBounds(200,100, 300,230);
        super.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        Container container = super.getContentPane();
        container.setLayout(new GridLayout(5,2,2,10));


        JLabel name = new JLabel("Geben Sie einen Namen ein: ");
        name_field = new JTextField("", 1);
        JLabel email = new JLabel("Geben Sie einen E-Mail ein: ");
        email_field = new JTextField("@", 1);

        container.add(name);
        container.add(name_field);
        container.add(email);
        container.add(email_field);

        male = new JRadioButton("männlich");
        female = new JRadioButton("female");
        check = new JCheckBox("Einverstanden?", false);
        JButton send_button = new JButton("Senden");

        male.setSelected(true);
        container.add(male);
        container.add(female);

        ButtonGroup group = new ButtonGroup();
        group.add(male);
        group.add(female);

        container.add(check);
        container.add(send_button);

        send_button.addActionListener(new ButtonEventManager());
    }
    class ButtonEventManager implements ActionListener {

        @Override
        public void actionPerformed(ActionEvent e) {
            String name = name_field.getText();
            String email = email_field.getText();

            String isMale = "Männlich";
            if (!male.isSelected())
                isMale = "Weiblich";

            boolean checkBox = check.isSelected();

            JOptionPane.showMessageDialog(null, "Ihre E-Mail: " + email +
                            "\nIhres Geschlecht: " + isMale + "\nEinverstanden? " + checkBox, "Hallo, " +
                            name, JOptionPane.PLAIN_MESSAGE);
        }
    }
}
