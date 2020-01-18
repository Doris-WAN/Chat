1 程序的运行环境、安装步骤
         （1）运行环境：JDK 1.6 / 1.7 
         （2）程序的组成部份：客户端：Chat_Client.jar
					    服务器端：Chat_Server.jar
         （3）安装步骤： 
1）  安装JRE 1.7。
       	    2）将程序jar文件复制到计算机上
    	      3）在资源管理器中双击Chat_Client.jar/ Chat_Server.jar，运行程序
2 程序开发平台
         （1）代码行数：Chat_Client.jar——530；Chat_Server.jar——543
         （2）开发环境：IntelliJ IDEA Community Edition 2019.2.3 x64
3 程序功能说明：
总体说明：
         客户端与服务器端之间传递文字信息以及发送文件。附带画板小工具。
	 应用截图：
	将服务器端的IP填入客户端文本框，依次点击“等待用户连接”、“连接”
	连接成功后，该页面关闭，进入聊天主页面
   
聊天面板如下，四个按钮，“绘图”打开画板；“清除”清除聊天页面内容，不可恢复；“文件”传输文件；“发送”即发送文本消息
 
 
画板及选择文件页面如下：
     

4	程序算法说明及面向对象实现技术方案
（1）	本程序是一个服务端与客户端之间通信的程序，应该先运行服务端，并且监听一个服务端口，等待客户连接。然后客户端通过服务端的ip以及监听的端口号，即socket连接服务端，然后进行通信。
通过socket传递文字信息以及数据包。这个过程中通过多线程提交运行效率并阻塞输入输出流。
最终达到两者间异步通信的目的。
（2）	数据结构和算法的面向对象实现
以Chat_Server为例介绍:
SERVER
extends Component implements ActionListener ,KeyListener
public JFrame connect;
public JFrame jf;
public ServerSocket server;
public Socket scoket;
public JTextArea show;
public JTextField input;
public String msg;
java.lang.String myIp;
public static void main(String[] args) throws IOException
public SERVER() throws IOException
void UI() throws IOException
public void actionPerformed(ActionEvent e)
public void keyPressed(KeyEvent e)

Tool
extends JFrame
implements ActionListener, MouseListener, MouseMotionListener
private JButton current;
private Color color;
private Graphics G;
private JPanel jp;
private Graphics g;
int x1, x2, y1, y2;
int x, y;
void tool_UI()
public void setCurColor(JButton cur)
public void actionPerformed(ActionEvent e)
public void setG(Graphics g)
public void mousePressed/Released/Dragged(MouseEvent e)

 FileThread 
extends Thread
private Socket socket;
private String filename;
private String filepath;
public OutputStream os;
public File sendfile;
public FileInputStream fis;
public FileThread(Socket socket)
public void run()

ChooseFile
public  String FileName;
public  String FilePath;
void choose()

ServerSendThread
extends Thread
private Socket socket;
private  String str;
public ServerSendThread(Socket socket,String str)
public void run()

ServerReceiveThread
extends Thread
private Socket socket;
private JTextArea jta;
public ServerReceiveThread(Socket socket, JTextArea jta)
public void run()

DEMO
extends Thread
private  String str;
private  JTextArea jta;
public DEMO(String str, JTextArea jta)
public void  run()

5 技术亮点、关键点及其解决方案
  技术亮点及关键点
采用了多线程技术以提升程序的性能避免阻塞
在开发过程中大规模地使用了单元测试
UI页面对于使用者更加友好
  遇到的技术难点及对应的解决方案：
问题一描述：在接受字符串数据后，无法在当前工作线程写入UI,造成阻塞 
最终的解决方案：利用多线程完成当前工作，具体通过重写Thread的run方法实现
 问题二描述：聊天页面只能显示16行的文本，超过十六行的信息无法显示
最终的解决方案：“清除”键将聊天页面清空，使之可以继续显示消息 

6 简要开发过程
教学周14周 周五     确定项目方案，简要设计UI画面及基础功能
教学周16周 周三     完成客户端与服务器端连接通信测试
教学周16周 周日   完成登陆页面制作
教学周17周 周三   完成聊天页面制作
教学周17周 周日   完成画板测试，并加入项目
教学周18周 周二   完成页面UI制作
教学周18周 周五   完成多线程测试
教学周18周 周六   利用多线程完成传递文字消息的测试
教学周19周 周一   完成传输文件Demo功能测试，并加入项目
教学周19周 周二      对程序进行集成测试
教学周19周 周三  程序开发工作完毕，编写及整理文档
1 程序的运行环境、安装步骤
         （1）运行环境：JDK 1.6 / 1.7 
         （2）程序的组成部份：客户端：Chat_Client.jar
					    服务器端：Chat_Server.jar
         （3）安装步骤： 
1）  安装JRE 1.7。
       	    2）将程序jar文件复制到计算机上
    	      3）在资源管理器中双击Chat_Client.jar/ Chat_Server.jar，运行程序
2 程序开发平台
         （1）代码行数：Chat_Client.jar——530；Chat_Server.jar——543
         （2）开发环境：IntelliJ IDEA Community Edition 2019.2.3 x64
3 程序功能说明：
总体说明：
         客户端与服务器端之间传递文字信息以及发送文件。附带画板小工具。
	 应用截图：
	将服务器端的IP填入客户端文本框，依次点击“等待用户连接”、“连接”
	连接成功后，该页面关闭，进入聊天主页面
   
聊天面板如下，四个按钮，“绘图”打开画板；“清除”清除聊天页面内容，不可恢复；“文件”传输文件；“发送”即发送文本消息
 
 
画板及选择文件页面如下：
     

4	程序算法说明及面向对象实现技术方案
（1）	本程序是一个服务端与客户端之间通信的程序，应该先运行服务端，并且监听一个服务端口，等待客户连接。然后客户端通过服务端的ip以及监听的端口号，即socket连接服务端，然后进行通信。
通过socket传递文字信息以及数据包。这个过程中通过多线程提交运行效率并阻塞输入输出流。
最终达到两者间异步通信的目的。
（2）	数据结构和算法的面向对象实现
以Chat_Server为例介绍:
SERVER
extends Component implements ActionListener ,KeyListener
public JFrame connect;
public JFrame jf;
public ServerSocket server;
public Socket scoket;
public JTextArea show;
public JTextField input;
public String msg;
java.lang.String myIp;
public static void main(String[] args) throws IOException
public SERVER() throws IOException
void UI() throws IOException
public void actionPerformed(ActionEvent e)
public void keyPressed(KeyEvent e)

Tool
extends JFrame
implements ActionListener, MouseListener, MouseMotionListener
private JButton current;
private Color color;
private Graphics G;
private JPanel jp;
private Graphics g;
int x1, x2, y1, y2;
int x, y;
void tool_UI()
public void setCurColor(JButton cur)
public void actionPerformed(ActionEvent e)
public void setG(Graphics g)
public void mousePressed/Released/Dragged(MouseEvent e)

 FileThread 
extends Thread
private Socket socket;
private String filename;
private String filepath;
public OutputStream os;
public File sendfile;
public FileInputStream fis;
public FileThread(Socket socket)
public void run()

ChooseFile
public  String FileName;
public  String FilePath;
void choose()

ServerSendThread
extends Thread
private Socket socket;
private  String str;
public ServerSendThread(Socket socket,String str)
public void run()

ServerReceiveThread
extends Thread
private Socket socket;
private JTextArea jta;
public ServerReceiveThread(Socket socket, JTextArea jta)
public void run()

DEMO
extends Thread
private  String str;
private  JTextArea jta;
public DEMO(String str, JTextArea jta)
public void  run()

5 技术亮点、关键点及其解决方案
  技术亮点及关键点
采用了多线程技术以提升程序的性能避免阻塞
在开发过程中大规模地使用了单元测试
UI页面对于使用者更加友好
  遇到的技术难点及对应的解决方案：
问题一描述：在接受字符串数据后，无法在当前工作线程写入UI,造成阻塞 
最终的解决方案：利用多线程完成当前工作，具体通过重写Thread的run方法实现
 问题二描述：聊天页面只能显示16行的文本，超过十六行的信息无法显示
最终的解决方案：“清除”键将聊天页面清空，使之可以继续显示消息 

6 简要开发过程
教学周14周 周五     确定项目方案，简要设计UI画面及基础功能
教学周16周 周三     完成客户端与服务器端连接通信测试
教学周16周 周日   完成登陆页面制作
教学周17周 周三   完成聊天页面制作
教学周17周 周日   完成画板测试，并加入项目
教学周18周 周二   完成页面UI制作
教学周18周 周五   完成多线程测试
教学周18周 周六   利用多线程完成传递文字消息的测试
教学周19周 周一   完成传输文件Demo功能测试，并加入项目
教学周19周 周二      对程序进行集成测试
教学周19周 周三  程序开发工作完毕，编写及整理文档
7 个人小结及建议
 对本项目的一些总结：		
完成后回顾整个项目，自己面对对象的编程思想还不够成熟，在制作过程中更多考虑面对过程解决问题，导致最后整个项目碎片化。
通过这个小工具，虽然简单，但是由此训练了关于布局、socket、线程、监听等内容，对通信协议文件传输等有了一定的了解与实践。
有一个遗憾，最初想要实现同步画板的功能，但是在实现简单数据传输后发现剩余时间不足以完成这部分内容，也没有很好的思路能够实现这部分的功能，可以在以后把这个遗憾补上
