# 系统概述
## 运行与编译环境 
本次实验在Windows11下运行和编译，使用Python3.9编译器。
## 使用方法
使用任意PythonIDLE打开TCPServer.py/UDPServer.py并运行，等待控制台中提示信息出现后，运行TCPClient.py/UDPClient.py，之后按照弹窗提示输入用户名与密码即可进入房间，客户端可复制多份独立运行。
## 实验环境
实验在PyCharmIDLE中进行，借助Python3.9内置的socket与threading模块完成各项实验任务。
## 程序文件列表
- TCPServer.py；
- TCPClient.py；
- UDPServer.py；
- UDPClient.py.
# 主要数据结构
实验过程中所使用的数据结构包含字符串、列表、元组以及字典四种，以下我将分类别介绍各 类数据结构的运用场景。
1. **字符串**：程序中服务端与客户端的地址、客户的用户名、密码、客户端与服务器间互相发送的信息全部使用字符串储存。这种数据结果也使得客户端和服务端能更加便捷地直接在用户发送的信息前添加所需要的首部信息。
2. **列表**：列表在本程序中用于存储已连接客户的用户名，方便服务器通过序号快速索引得到用户的具体用户名。比如在TCP服务器中存储用户的套接字以及UDP服务器中存储用户的具体地址，以便于能够及时向所有用户广播信息。
3. **元组**：元组仅在UDP的服务器端涉及。由于UDP协议在发送信息时必须将目的地地址附在信息中一起发送，因此UDP服务器中除了需要将用户的地址也与用户名一一对应。本程序将密码与地址装入一个元组中，并将这个整体作为用户字典的值存储。
4. **字典**：字典有着靠索引快速查找的优点，在本程序中用于构建客户的用户名与其密码或是密码、 地址元组间的一一对应关系（如元组中所述）。服务器发现有新用户注册时会向用户字典中增加新的键值对。需要注意的是用户即使断开连接，用户字典中的信息并不会改变（保留账号密码），而是对用户列表进行调整。
# 主要算法描述
本程序最核心的部分为服务端和客户端各自的监听循环，其中主要有以下这些板块（以UDP为例）：
- 服务端：用户注册+校验密码+回应客户端请求
```Python
if message[:4] == 'con:':  
   print("[管理员后台]:用户登录中，用户名为{}。".format(message[4:]))  
   print("[管理员后台]:判断该用户名是否合法……")  
   self.userLogin(message[4:], clientAddress)  
  
elif message[:3] == '***':  
   print("[管理员后台]:用户输入密码中，密码为{}。".format(message[message.find(':') + 1:]))  
   print("[管理员后台]:判断该密码是否正确……")  
   self.passwordJudge(message[3:message.find(':')], message[message.find(':') + 1:], clientAddress)  
  
elif message[:3] == '>>>':  
   # 响应请求  
elif message[:3] == '...':  
   print('[管理员]:用户', message[3:], '退出房间')  
   self.Broadcast(message='[管理员]:用户 ' + message[3:] + ' 退出房间')  
   self.userLogout(message[3:])
```
- 客户端：登入+处理服务端信息+发送消息
```Python
self.name = self.login()  
self.score = 0  
self.initUI()  
print("开启子线程用于接受数据")  
thread = threading.Thread(target=self.__receive_message_thread, daemon=True)  
thread.start()
```
# 用户使用手册
由于TCP与UDP的服务器端与客户端的操作完全一致，仅在实现方式上有所区别。因此在使用方法的演示部分以TCP的服务器端与客户端为例进行演示。
## 服务器端使用手册
- 运行TCPServer.py，等待控制台中弹出服务器端成功启动的消息。
![[Pasted image 20240918221635.png]]
<center>图1-服务端启动成功消息</center>
- 启动后服务端会根据用户信息的类型自动进行登陆验证与广播消息。
![[Pasted image 20240918221817.png]]
<center>图2-服务端处理新用户</center>
![[Pasted image 20240918221920.png]]
<center>图3-服务端处理客户端登入成功</center>
![[Pasted image 20240918222011.png]]
<center>图4-服务端处理用户请求</center>
## 客户端使用手册
- 运行TCPClient.py，出现弹窗提示用户登录。
![[Pasted image 20240918222126.png]]
<center>图5-客户端请求输入用户名</center>
- 若为首次登录用户，服务器将会提示用户创建密码；若为老用户则直接输入密码登录即可。
![[Pasted image 20240918222221.png]]
<center>图6-客户端请求输入密码</center>
![[Pasted image 20240918222312.png]]
<center>图7-客户端登入成功（老用户）</center>
![[Pasted image 20240918222400.png]]
<center>图8-客户端注册成功（新用户）</center>
- 如输错密码，则客户端会提示重新输入密码。
 ![[Pasted image 20240918222507.png]]
 <center>图9-客户端密码错误</center>
 - 成功登录后即可进入房间，上方方框中将会显示来自服务器的消息。