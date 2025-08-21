# ssh

ssh 配置免密登录：

SSH免密登录通常通过SSH密钥对来实现，其中一个是私钥，另一个是公钥。以下是一些步骤来设置SSH免密登录：\
1、生成SSH密钥对：首先，在本地计算机上生成SSH密钥对，如果没有的话，可以使用以下命令生成：\
`ssh-keygen -t rsa -b 2048`\
这将生成一个RSA密钥对，包括一个私钥（通常保存在 \~/.ssh/id\_rsa）和一个公钥（通常保存在 \~/.ssh/id\_rsa.pub）。\
2、将公钥复制到远程服务器：接下来，你需要将你的公钥复制到要免密登录的远程服务器。你可以使用ssh-copy-id命令来执行此操作：\
`ssh-copy-id username@remote_server`\
将 username 替换为你的远程服务器用户名，将 remote\_server 替换为远程服务器的地址或IP地址。命令执行后，它会要求你输入远程服务器的密码。\
3、如果 ssh-copy-id 命令不可用，你可以手动将公钥的内容复制到远程服务器的 \~/.ssh/authorized\_keys 文件中。使用以下命令来完成：\
`cat ~/.ssh/id_rsa.pub | ssh username@remote_server 'cat >> /.ssh/authorized_keys''`\
这将将你的公钥追加到远程服务器的授权密钥文件中。\
测试SSH免密登录：完成上述步骤后，你应该能够无需输入密码即可SSH登录到远程服务器：\
`ssh username@remote_server`\
这将免密登录到远程服务器，而不需要密码验证。\
请注意，为了保持安全性，确保你的私钥文件（/.ssh/id\_rsa）具有适当的权限，通常是600（只有所有者可以读和写）：\
`chmod 600 ~/.ssh/id_rsa`\
这将确保你的私钥不会被未经授权的用户访问。
