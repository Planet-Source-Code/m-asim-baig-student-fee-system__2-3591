<div align="center">

## Student Fee System


</div>

### Description

This is a Filing Base Data Base, which actually hold the informations about the student fee.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[M\. Asim Baig](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/m-asim-baig.md)
**Level**          |Intermediate
**User Rating**    |3.8 (15 globes from 4 users)
**Compatibility**  |Java \(JDK 1\.1\), Java \(JDK 1\.2\)
**Category**       |[Databases/ JDBC](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/databases-jdbc__2-61.md)
**World**          |[Java](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/java.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/m-asim-baig-student-fee-system__2-3591/archive/master.zip)





### Source Code

```
import java.io.*;
import java.awt.*;
import java.awt.event.*;
import javax.swing.*;
public class FeeSystem extends Frame implements ActionListener
{
	TextField textId;
	TextField textName;
	TextField textFname;
	TextField textClass;
	TextField textAddress;
	TextField textFee;
	TextField textDue;
	Button newRecord;
	Button search;
	Button save;
	Button delete;
	Button exit;
	File file = new File("c:/fee.txt");
	FeeSystem()
	{
		super("Student Fee System");
		setResizable(false);
	}
	FeeSystem(String title)
	{
		super(title);
		setLayout(null);
		setBounds(150,50,500,480);
		setFont(new Font("Georgia",3,14));
		setBackground(new Color(194,200,252));
		setResizable(false);
		Label mainTitle = new Label("Fee Information System");
		Label id = new Label("Enter Student ID :");
		Label name = new Label("Student Name :");
		Label fname = new Label("Student Father Name :");
		Label clas = new Label("Student Class :");
		Label address = new Label("Student Address :");
		Label fee = new Label("Fee submitted / 28,600 in Rs. :");
		Label due = new Label("Fee Due on the Student in Rs. :");
		textId = new TextField();
		textName = new TextField();
		textFname = new TextField();
		textClass = new TextField();
		textAddress = new TextField();
		textFee = new TextField();
		textDue = new TextField();
		mainTitle.setBounds(150,30,250,20);
		id.setBounds(80,70,150,20);
		name.setBounds(80,140,150,20);
		fname.setBounds(80,180,150,20);
		clas.setBounds(80,220,150,20);
		address.setBounds(80,260,150,20);
		fee.setBounds(80,330,200,20);
		due.setBounds(80,370,200,20);
		textId.setBounds(300,70,100,22);
		textId.setBackground(new Color(149,157,236));
		textName.setBounds(300,140,100,22);
		textName.setBackground(new Color(149,157,236));
		textFname.setBounds(300,180,100,22);
		textFname.setBackground(new Color(149,157,236));
		textClass.setBounds(300,220,100,22);
		textClass.setBackground(new Color(149,157,236));
		textAddress.setBounds(300,260,100,22);
		textAddress.setBackground(new Color(149,157,236));
		textFee.setBounds(300,330,100,22);
		textFee.setBackground(new Color(149,157,236));
		textDue.setBounds(300,370,100,22);
		textDue.setBackground(new Color(149,157,236));
		newRecord = new Button("New");
		search = new Button("Search");
		save = new Button("Save");
		delete = new Button("Delete");
		exit = new Button("Exit");
		newRecord.setBounds(40,440,70,20);
		newRecord.setFont(new Font("Georgia",3,12));
		search.setBounds(130,440,70,20);
		search.setFont(new Font("Georgia",3,12));
		save.setBounds(220,440,70,20);
		save.setFont(new Font("Georgia",3,12));
		delete.setBounds(310,440,70,20);
		delete.setFont(new Font("Georgia",3,12));
		exit.setBounds(400,440,70,20);
		exit.setFont(new Font("Georgia",3,12));
		add(newRecord);
		add(search);
		add(save);
		add(delete);
		add(exit);
		newRecord.addActionListener(this);
		search.addActionListener(this);
		save.addActionListener(this);
		delete.addActionListener(this);
		exit.addActionListener(this);
		add(mainTitle);
		add(id);
		add(name);
		add(fname);
		add(clas);
		add(address);
		add(fee);
		add(due);
		add(textId);
		add(textName);
		add(textFname);
		add(textClass);
		add(textAddress);
		add(textFee);
		add(textDue);
		delete.setEnabled(false);
		setVisible(true);
	}
	public void actionPerformed(ActionEvent ae)
	{
		Object source = new Object();
		source = ae.getSource();
		if(source == exit)
		{
			System.exit(0);
		}
		if(source == search)
		{
			String id;
			String name;
			String fname;
			String clas;
			String address;
			String fee;
			String due;
			id = textId.getText();
			id = "~" + id + "~";
			if(id.equals(""))
			{
				JOptionPane.showMessageDialog(this,"   You must enter the ID number ! ! ! ","Invalid ID",JOptionPane.INFORMATION_MESSAGE);
			}
			else
			if(!id.equals(""))
			{
				save.setEnabled(false);
				delete.setEnabled(true);
				textName.setEditable(false);
				textFname.setEditable(false);
				textClass.setEditable(false);
				textAddress.setEditable(false);
				textFee.setEditable(false);
				textDue.setEditable(false);
				String st[] = new String[8];
				int index = 0;
				int in = 0;
				try
				{
					FileInputStream fis = new FileInputStream(file);
					BufferedInputStream bis = new BufferedInputStream(fis);
					DataInputStream dis = new DataInputStream(bis);
					String str = dis.readLine();
					index = str.indexOf(id);
					System.out.println(id);
					if(index == -1)
					{
						JOptionPane.showMessageDialog(this,"   No Record Found ! ! ! ","Record Information",JOptionPane.INFORMATION_MESSAGE);
					}
					in = str.indexOf("&",index+1);
					str = str.substring(index , in);
					//	System.out.println(str);
					index = 0;
					in = 0;
					index = str.indexOf("~");
					for(int i=0 ; i<st.length ; i++)
					{
						in = str.indexOf("~",index+1);
						st[i] = str.substring(index , in);
						index = in + 1;
						//	System.out.println(st[i]);
						//	textId.setText(st[0]);
						textName.setText(st[1]);
						textFname.setText(st[2]);
						textClass.setText(st[3]);
						textAddress.setText(st[4]);
						textFee.setText(st[5]);
						textDue.setText(st[6]);
					}
				}
				catch(Exception e)
				{ }
			}
		}
		if(source == save)
		{
			String id;
			String name;
			String fname;
			String clas;
			String address;
			String fee;
			String due;
			id = textId.getText();
			name = textName.getText();
			fname = textFname.getText();
			clas = textClass.getText();
			address = textAddress.getText();
			fee = textFee.getText();
			due = textDue.getText();
			System.out.println(id);
			if(id.equals(""))
			{
				JOptionPane.showMessageDialog(this,"   You must enter the ID number ! ! ! ","Invalid ID",JOptionPane.INFORMATION_MESSAGE);
			}
			if(!id.equals(""))
			{
				try
				{
					FileOutputStream fos = new FileOutputStream("c:/fee.txt",true);
					BufferedOutputStream bos = new BufferedOutputStream(fos);
					DataOutputStream dos = new DataOutputStream(bos);
					String str = "~" + id + "~" + name + "~" + fname + "~" + clas + "~" + address + "~" + fee + "~" + due + "~&";
					dos.writeBytes(str);
					dos.flush();
					dos.close();
				}
				catch(Exception e)
				{ }
			}
		}
		if(source == newRecord)
		{
			setVisible(false);
			delete.setEnabled(true);
			new FeeSystem("Student Fee System");
		}
		if(source == delete)
		{
			String id;
			id = textId.getText();
			id = "~" + id + "~";
			save.setEnabled(false);
			int index = 0;
			int in = 0;
			try
			{
				FileInputStream fis = new FileInputStream(file);
				BufferedInputStream bis = new BufferedInputStream(fis);
				DataInputStream dis = new DataInputStream(bis);
				String str = dis.readLine();
				StringBuffer sb = new StringBuffer(str);
				//System.out.println(sb);
				index = str.indexOf(id);
				if(index == -1)
				{
					JOptionPane.showMessageDialog(this,"   No Record Found ! ! ! ","Record Information",JOptionPane.INFORMATION_MESSAGE);
				}
				else
				{
					int con = JOptionPane.showConfirmDialog(this,"   Are you sure to delete the record ! ! ! ","Confirmation",JOptionPane.YES_NO_OPTION);
					System.out.println(con);
					if(con == 0)
					{
						in = str.indexOf("&",index+1);
						sb = sb.replace(index , in+1 , "");
						//System.out.println(sb);
						str = sb.substring(0);
						//System.out.println(str);
						FileOutputStream fos = new FileOutputStream(file);
						DataOutputStream dos = new DataOutputStream(fos);
						dos.writeBytes(str);
					}
				}
			}
			catch(Exception e)
			{
				JOptionPane.showMessageDialog(this,"   Couldn't delete the Record ! ! ! ","Confirmation",JOptionPane.INFORMATION_MESSAGE);
			}
		}
	}
	public void paint(Graphics g)
	{
		g.drawLine(20,115,480,115);
		g.drawLine(20,304,480,304);
	}
	public static void main(String args[])
	{
		FeeSystem fs = new FeeSystem("Student Fee System");
	}
}
```

