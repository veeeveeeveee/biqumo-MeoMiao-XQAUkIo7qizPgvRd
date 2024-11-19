
工作电脑为一体机。所有的USB接口都在屏幕的后面。插拔U盘极不方便。于是搜索USB小物件，看能不能通过小物件将USB的接口延长到屏幕前


寻觅一番，找到一个中意的小物件——**ELEKS MAKER 极客桌面控制器**


![](https://img2024.cnblogs.com/blog/93227/202411/93227-20241118142345636-372474571.png)


 


如上图所示，小物件有着朋克风，充满现代感。带有3个USB2\.0接口，日常工作使用足够。另外还有三个小按键，以及一个大旋钮。大旋钮可以旋转，也可以当按钮用。


按照使用说明，大旋钮的旋转是控制系统的音量，大旋钮的按键是切换系统是否静音。


也可以通过控制程序，来自定义大旋钮按键的功能。


 


于是，有了个想法，**将大旋钮的的按键，自定义为锁屏**。当我离开工位，按一下大旋钮，就将工作电脑锁屏了。


 


于是，打开控制程序，如下图


![](https://img2024.cnblogs.com/blog/93227/202411/93227-20241118143208009-1433183805.png)


 可以看出，控制程序分别对**三个按钮**和**一个大旋钮**的功能进行了设定的功能


 **但是**！对“按下按钮”的这个动作，只能指定多媒体键，也就是在若干个指定的多媒体键中间选择一个。并不能选择其他的快捷键。比如，锁屏的快捷键是Win\+L，却是没法设定。


 


于是，在网上搜索一番。找到了两篇有用的文章


[【转载】修改Windows下键盘按键对应功能的一些方案](https://github.com)


[Win10 64位电脑如何以桌面快捷方式创建一个一键锁屏程序?](https://github.com):[wgetCloud机场](https://longdu.org)


 


第一篇文章，讲解了，如何修改**多媒体键**对应的功能


如下面所示，通过注册表，将**计算器多媒体键**的功能改为指向记事本（notepad.exe）


Windows Registry Editor Version 5\.00\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Explorer\\AppKey\\18]"ShellExecute"\="notepad.exe"


 


其中，ShellExecute字段指向其他程序。


也可以用Association字段指向扩展名，调用该扩展名对应的程序。


例如：


"Association"\="mailto"，表示调用默认的邮件程序


"Association"\=".doc"，表示调用默认的doc的程序，一般是Word


 


第二篇文章，讲解了，如何通过快捷方式，设定锁屏


在快捷方式下，通过


rundll32\.exe user32\.dll,LockWorkStation


调用系统的锁频程序


 


于是，灵光一闪，将上面两篇文章的内容合二为一


1、将按下按钮的多媒体快捷键改为“计算器”


2、编写注册表，将计算器多媒体键的对应的内容改为指向锁屏。


Windows Registry Editor Version 5\.00\[HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Explorer\\AppKey\\18]"ShellExecute"\="rundll32\.exe user32\.dll,LockWorkStation"


 


将注册表导入到系统内之后


此时，按小物件的大按钮，电脑立刻锁屏！


 


