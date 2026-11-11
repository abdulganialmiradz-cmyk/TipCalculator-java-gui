 TipCalculator-java-gui

import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class TipCalculator {
    public static void main(String[] args) {
        JFrame frame = new JFrame("Seatwork 2: Tip Calculator");
        frame.setSize(300, 250);
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setLayout(null);

        JLabel lblBill = new JLabel("Bill Amount:");
        lblBill.setBounds(20, 20, 100, 25);
        frame.add(lblBill);

        JTextField txtBill = new JTextField();
        txtBill.setBounds(120, 20, 140, 25);
        frame.add(txtBill);

        JLabel lblTip = new JLabel("Tip %:");
        lblTip.setBounds(20, 50, 100, 25);
        frame.add(lblTip);

        JTextField txtTip = new JTextField();
        txtTip.setBounds(120, 50, 140, 25);
        frame.add(txtTip);

        JButton btnCalculate = new JButton("Calculate");
        btnCalculate.setBounds(20, 90, 240, 30);
        frame.add(btnCalculate);

        JLabel lblResult = new JLabel("Tip: $0.00 | Total: $0.00");
        lblResult.setBounds(20, 130, 250, 25);
        frame.add(lblResult);

        btnCalculate.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                try {
                    double bill = Double.parseDouble(txtBill.getText());
                    double tipPercent = Double.parseDouble(txtTip.getText());

                    if (bill < 0 || tipPercent < 0) {
                        lblResult.setText("Invalid input: Numbers must be >= 0");
                        return;
                    }

                    double tipAmount = bill * (tipPercent / 100.0);
                    double totalAmount = bill + tipAmount;

                    lblResult.setText(String.format("Tip: $%.2f | Total: $%.2f", tipAmount, totalAmount));
                } catch (NumberFormatException ex) {
                    lblResult.setText("Invalid input! Enter valid numbers.");
                }
            }
        })
 
