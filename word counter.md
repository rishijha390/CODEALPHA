# CODEALPHA

    import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class demo extends JFrame {
    private JTextArea textArea;
    private JLabel resultLabel;

    public demo() {
        setTitle("Word Counter");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        textArea = new JTextArea();
        JScrollPane scrollPane = new JScrollPane(textArea);
        add(scrollPane, BorderLayout.CENTER);

        JButton countButton = new JButton("Count Words");
        countButton.addActionListener(new ActionListener() {
            public void actionPerformed(ActionEvent e) {
                String text = textArea.getText();
                int wordCount = text.split("\\s+").length;
                resultLabel.setText("Word count: " + wordCount);
            }
        });

        resultLabel = new JLabel("Word count: 0");

        JPanel bottomPanel = new JPanel();
        bottomPanel.add(countButton);
        bottomPanel.add(resultLabel);

        add(bottomPanel, BorderLayout.SOUTH);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            public void run() {
                new demo().setVisible(true);
            }
        });
    }
}
