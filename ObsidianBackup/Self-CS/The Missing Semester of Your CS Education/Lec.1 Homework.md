1. ZSH+Oh-My-Zsh+powerlevel10k安装[Ubuntu用Terminator+ZSH打造好用的终端开发环境 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/346665734)&https://github.com/romkatv/powerlevel10k
2. 略
3. touch - 更改文件的时间戳
4. 略
5. Quoting即转义，改变特殊字符的含义
6. permission denied: ./semester，没有权限
7. chmod 的功能之一可以用 mode file参数改变权限，~~mode的三个位可以是0~7中的一个，代表着The first digit selects the set user ID (4) and set group ID (2) and restricted deletion or sticky  (1)  attributes.   The  second digit  selects permissions for the user who owns the file: **read (4), write (2), and execute (1)**; the third selects permissions for other users in the file's group, with the same values;  and  the fourth for other users not in the file's group, with the same values.但是我不理解第一位是什么意思，~~好的没事了原来三个数是对应了Owner、Group、Other的权限~~，那手册里说的四个数又是啥？~~ok是指执行中权限（4），对目录下权限设置（2），防止删除（1），*不是这man里也没有说明白啊*
8. ![[Pasted image 20240922235739.png]]
9. ![[Pasted image 20240922235852.png]]
10. 在sys/class/下找到了powercap，但是里面是空的，可能是虚拟机问题？又找了CPU相关温度信息，但是教程里都是需要安装Lm_Sensors？（看完solution）好吧，真没有