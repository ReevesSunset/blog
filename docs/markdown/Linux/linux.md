## linux常用命令

> lesson1

1. locale -a 查看支持的语言
2. . 表示当前目录 .. 表示上一q级目录 
3.  mv 重命名  和  移动文件
4. stat 查看问件状态
5. touch 可以创建新文件,可以更改时间戳
6. man 查看命令的菜单
7. rm 删除
8. cp copy复制
9. cat 查看文件内容

> lesson2

1. echo 输出
2. cat 查看文件内容
   cat -s(参数) demo.txt(文件名)
   cat -s 去重空行
3. tac 也是打开,但是是从最后开始,倒着显示
4. wc 统计字数/行数/字节数等输出在屏幕上,换行符也会加上 /n 换行算是两个字符
   wc -c(参数) demo.txt(文件名)
   -c 统计字节数
   -l 统计行数
   -m 统计字符数 不能与-c一起使用
   -w 统计字数 一个字被定义为空白,跳格或者换行字符的字符串
   不推荐用来统计文本字数,中文存问题.还是用python来数
5. sort 排序
   语法: sort -b(参数) demo.txt(文件名) 
   -r 翻转
   -n 数字大小
   -t 分隔符,默认是tab
6. uniq 忽略和报告重读行,重复的会过滤
   -i 忽略大小写
   -c 进行计数
   -u 只显示唯一的行
7. cut 可以从一个文本文件或者一个文件流中提取文本列
8. tee 读取标准输入的数据,并输出成文件
9. more 也是查看文件,但是可以慢慢打开 空格下一页. 百分比显示
10. less 显示的比more少
11. head 默认显示钱10行
    head -n 20 设置显示前20行 
12. tail 默认显示最后的部分.可实时查看文件变化.可以查看日志   
13. which命令搜索 查命令的位置,前提是命令可执行
14. chmod 可以更改权限
    用法: chomd 755 文件名/路径
    chomd u=rw
          g=rx
          o=rwx
    权限对应数字:
          r : 4
          w : 2
          x : 1
    u 代表所有者
    g 所有者所在群组
    o 其他人
    a 代表全部的人 
    目录:
    r : 可以查看目录下的文件
    w : 是否可以创建修改文件
    x : 表示目录是否可以被搜索
15. 用户
    1. etc/passwd 保存用户信息
    2. sudo useradd user1 添加user1用户
    3. su - user1 切换到user1用户(推荐的切换用户的方法)
    4. id 查看当前用户
    5. userdel 删除用户，只会删除用户，用户文件夹还是存在
       userdel -r 连同用户主目录一起删掉
    6. usermod 用户信息
    7. groupadd 添加组
    8. groupdel 删除组
    9. linux 是通过uid识别用户的 gid: 是分组的依据
    10.环境配置文件 ls -a .bash*
    11. sudo 一般情况下,是以root的权限去执行
        但是不一定
        sudo 配置文件 /etc/sudoers `
16. 别名
    alias 给命令起别名18301456316
17. 
        
    
    
     
   

   