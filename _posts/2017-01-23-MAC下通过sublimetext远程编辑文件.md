---
layout:     post
title:      MAC下通过sublimetext远程编辑文件
subtitle:   MAC系统系实现Editplus在windows下的远程访问linux服务器编辑文件的功能
date:       2018-01-23
author:     HOLISUN
header-img: img/post-bg-re-vs-ho03.jpg
catalog: true
tags:
    - Blog
---


**1. 准备工作：到sublimetext官网下载软件，并完成安装。**

**2. Package Control安装插件，按下Ctrl+Shift+P调出命令面板，输入install 调出 Install Package 选项并回车，然后输入ftp，下拉列表中会出现一些相关的插件，选中sftp进行安装就行了，装好后还需配置如下：选菜单栏中的File->SFTP/FTP->Set up Server，然后出现一个配置窗口如下：**

```
{
    // The tab key will cycle through the settings when first created
    // Visit http://wbond.net/sublime_packages/sftp/settings for help
    
    // sftp, ftp or ftps
    "type": "sftp",

    "sync_down_on_open": true,
    "sync_same_age": true,
    
    "host": "192.168.166.146",//此处是远程服务器地址
    "user": "root",//此处是远程访问用户名
    "password": "itcast",//此处是远程访问用户密码
    //"port": "22",
    
    "remote_path": "/root",//此处是远程访问的目录
    //"file_permissions": "664",
    //"dir_permissions": "775",
    
    //"extra_list_connections": 0,

    "connect_timeout": 30,
    //"keepalive": 120,
    //"ftp_passive_mode": true,
    //"ftp_obey_passive_host": false,
    //"ssh_key_file": "~/.ssh/id_rsa",
    //"sftp_flags": ["-F", "/path/to/ssh_config"],
    
    //"preserve_modification_times": false,
    //"remote_time_offset_in_hours": 0,
    //"remote_encoding": "utf-8",
    //"remote_locale": "C",
    //"allow_config_upload": false,
}

```
**3. 我们只需要配置下这四项参数即可：远程服务器地址、远程访问的用户名、密码以及要进入的目录地址（我这里设置的是/root根目录）即可。**

**4. 配置完成之后保存,可配置多个，然后File->SFTP/FTP->Browse Server，选择对应服务器目标文件即可。**

**5. 经常编辑linux下配置文件的同学都希望能对代码进行格式化（类似eclipse中的ctrl+shift+f），在sublimetext也拥有类似的功能，Edit-Line-Reindent即可对选中的代码进行格式化了，注意必须选中代码。**

**6. 默认sublimetext中国这项功能是没有快捷键的，我自定义它的快捷键：偏好设置（preferences）-Key Bindings，然后子啊打开的窗口右侧window加入下面代码：**

```
[
    // 郝占江自定义的代码格式化快捷键
    {"keys":["alt+shift+f"],"command":"reindent"}
]
```

**因为ctrl+shift+f已被软件中的查找命令占用，所以这里我们用alt+shift+f来作为格式化的快捷键，然后保存即可。**

**7. 当然sunlinmetext还有太多太多丰富的功能，这里只是针对远程编辑文件功能进行简要的讲解，希望对大家有所帮助。**
