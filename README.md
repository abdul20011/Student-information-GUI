# Student-information-GUI
package work;

import java.awt.EventQueue;


import javax.swing.JFrame;
import javax.swing.JPanel;
import javax.swing.border.EmptyBorder;
import javax.swing.JLabel;
import javax.swing.JOptionPane;

import java.awt.Font;
import java.io.File;
import java.util.ArrayList;
import java.util.Scanner;

import javax.swing.JTextField;
import javax.swing.JComboBox;
import javax.swing.JToggleButton;
import javax.swing.JButton;
import java.awt.event.ActionListener;
import java.awt.event.ActionEvent;

public class studentinformation extends JFrame {

	private JPanel contentPane;
	private JTextField txtID;
	private JTextField txtfFirst;
	private JTextField txtLast;
	private JTextField txtGrade;
	private static ArrayList<Sudent> list = new ArrayList<Sudent>();
	private static int index=0;

	/**
	 * Launch the application.
	 */
	public static void main(String[] args) {
		EventQueue.invokeLater(new Runnable() {
			public void run() {
				try {
					studentinformation frame = new studentinformation();
					frame.setVisible(true);
					Scanner scan= new Scanner(new File("student.txt"));
					while (scan.hasNextLine())
					{
						String line = scan.nextLine();
						String[]arr=line.split(" ");
							String id = arr[0];
							String first= arr[1];
							String last = arr[2];
							int gr =  Integer.parseInt(arr[3]);
							String level = arr[4];
							Sudent s= new Sudent(id,first,last,gr,level);
							list.add(s);
					}
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		});
	}

	/**
	 * Create the frame.
	 */
	public studentinformation() {
		setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
		setBounds(100, 100, 614, 483);
		contentPane = new JPanel();
		contentPane.setBorder(new EmptyBorder(5, 5, 5, 5));

		setContentPane(contentPane);
		contentPane.setLayout(null);
		
		JLabel lblNewLabel = new JLabel("STUDENT INFORMATION");
		lblNewLabel.setFont(new Font("Lucida Grande", Font.PLAIN, 21));
		lblNewLabel.setBounds(158, 28, 303, 16);
		contentPane.add(lblNewLabel);
		
		JLabel lblStudentID = new JLabel("STUDENT ID");
		lblStudentID.setBounds(41, 91, 190, 16);
		contentPane.add(lblStudentID);
		
		JLabel lblFirstname = new JLabel("FIRSTNAME");
		lblFirstname.setBounds(41, 140, 190, 16);
		contentPane.add(lblFirstname);
		
		JLabel lblLastname = new JLabel("LASTNAME");
		lblLastname.setBounds(41, 185, 190, 16);
		contentPane.add(lblLastname);
		
		JLabel lblgrade = new JLabel("GRADE");
		lblgrade.setBounds(41, 232, 190, 16);
		contentPane.add(lblgrade);
		
		JLabel lblgradelevel = new JLabel("GRADELEVEL");
		lblgradelevel.setBounds(41, 283, 190, 16);
		contentPane.add(lblgradelevel);
		
		txtID = new JTextField();
		txtID.setBounds(160, 86, 130, 26);
		contentPane.add(txtID);
		txtID.setColumns(10);
		
		txtfFirst = new JTextField();
		txtfFirst.setColumns(10);
		txtfFirst.setBounds(158, 135, 130, 26);
		contentPane.add(txtfFirst);
		
		txtLast = new JTextField();
		txtLast.setColumns(10);
		txtLast.setBounds(158, 180, 130, 26);
		contentPane.add(txtLast);
		
		txtGrade = new JTextField();
		txtGrade.setColumns(10);
		txtGrade.setBounds(160, 227, 130, 26);
		contentPane.add(txtGrade);
		
		String [] levels = {"Select one:","freshman","Sophomore","junior","Senior"};
		JComboBox comboBox = new JComboBox(levels);
		comboBox.setBounds(160, 279, 133, 27);
		contentPane.add(comboBox);
		
		JButton btndirst = new JButton("FIRST");
		btndirst.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				index=0;
				String id = list.get(index).getStudentID();
				String first= list.get(index).getFirstName();
				String last= list.get(index).getLastname();
				int grade= list.get(index).getGrade();
				String level= list.get(index).getGradeLevel();
				txtID.setText(id);
				txtfFirst.setText(first);
				txtLast.setText(last);
				txtGrade.setText(""+grade);
				comboBox.setSelectedItem(level);
			}
		});
		btndirst.setBounds(30, 376, 78, 29);
		contentPane.add(btndirst);
		
		
		JButton btnext = new JButton("NEXT");
		btnext.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				index=index+1;
				if (index>3) {
					JOptionPane.showMessageDialog(null, "out of bounds");
				}
				String id = list.get(index).getStudentID();
				String first= list.get(index).getFirstName();
				String last= list.get(index).getLastname();
				int grade= list.get(index).getGrade();
				String level= list.get(index).getGradeLevel();
				txtID.setText(id);
				txtfFirst.setText(first);
				txtLast.setText(last);
				txtGrade.setText(""+grade);
				comboBox.setSelectedItem(level);
			}
		});
		btnext.setBounds(120, 376, 86, 29);
		contentPane.add(btnext);
		
		JButton btnPrevious = new JButton("PREVIOUS");
		btnPrevious.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				index=index-1;
				if(index<0) {					
					JOptionPane.showMessageDialog(null, "out of bounds");
  
					
				}
				String id = list.get(index).getStudentID();
				String first= list.get(index).getFirstName();
				String last= list.get(index).getLastname();
				int grade= list.get(index).getGrade();
				String level= list.get(index).getGradeLevel();
				txtID.setText(id);
				txtfFirst.setText(first);
				txtLast.setText(last);
				txtGrade.setText(""+grade);
				comboBox.setSelectedItem(level);
			}
		});
		btnPrevious.setBounds(228, 376, 86, 29);
		contentPane.add(btnPrevious);
		
		JButton btnLast = new JButton("LAST");
		btnLast.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				index=2;
				String id = list.get(index).getStudentID();
				String first= list.get(index).getFirstName();
				String last= list.get(index).getLastname();
				int grade= list.get(index).getGrade();
				String level= list.get(index).getGradeLevel();
				txtID.setText(id);
				txtfFirst.setText(first);
				txtLast.setText(last);
				txtGrade.setText(""+grade);
				comboBox.setSelectedItem(level);
			}
		});
		btnLast.setBounds(326, 376, 86, 29);
		contentPane.add(btnLast);
		
		JButton btnNew = new JButton("NEW");
		btnNew.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
				txtID.setText("");
				txtfFirst.setText("");
				txtLast.setText("");
				txtGrade.setText("");
				comboBox.setSelectedItem(0);
			}
		});
		btnNew.setBounds(424, 376, 78, 29);
		contentPane.add(btnNew);
		
		JButton btnSave = new JButton("SAVE");
		btnSave.addActionListener(new ActionListener() {
			public void actionPerformed(ActionEvent e) {
			}
		});
		btnSave.setBounds(238, 420, 117, 29);
		contentPane.add(btnSave);
	}
}
