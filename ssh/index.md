# rsa密钥的使用
### 本地操作
#### 查看是否已经生成了公钥 `cat ~/.ssh/id_rsa.pub`
  - `~` 表示当前登陆用户的主目录
  - 如果没有则 `ssh-keygen -m PEM -t rsa -b 4096 -C "your_email@example.com"`  
    - 执行过程过程中提示 `Enter passphrase (empty for no passphrase): `按 enter 跳过
    - 参数说明：  
      -t：指定生成密钥的类型，默认使用SSH2d的rsa, 
      ```
      -t rsa -b length (the default)
      -t ed25519 -b length,
      -t ecdsa -b 256
      -t ecdsa -b 384
      -t ecdsa -b 521
      ``` 
      ecdsa-sha2-nistp256
      ecdsa-sha2-nistp384
      ecdsa-sha2-nistp521
      -f：指定生成密钥的文件名，默认id_rsa（私钥id_rsa，公钥id_rsa.pub）  
      -P：提供旧密码，空表示不需要密码（-P ‘’）  
      -N：提供新密码，空表示不需要密码(-N ‘’)  
      -b：指定密钥长度（bits），RSA最小要求768位，默认是2048位；DSA密钥必须是1024位（FIPS 1862标准规定）  
      -C：提供一个新注释  
      -R: hostname：从known_hosta（第一次连接时就会在主目录.ssh目录下生产该密钥文件）文件中删除所有属于hostname的密钥  
      -m: 指定密钥格式 RSA 和PEM
  - 按enter之后 `Enter passphrase (empty for no passphrase):` 不用输入值，直接enter，不然每次使用私钥都需要输入
#### 验证 SHA256 算法指纹 `ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key`
#### 验证 MD5 算法指纹 `ssh-keygen -E md5 -lf /etc/ssh/ssh_host_rsa_key`
### 配置免密码登陆服务器 
`ssh-copy-id root@ip` ip:远程服务器IP，输入密码确认
  - 成功提示
  ```
    Number of key(s) added:        1
    Now try logging into the machine, with:   "ssh 'root@xx.xxx.xxx.xxx'"
    and check to make sure that only the key(s) you wanted were added.
  ```
再连接远程服务器即可免密登陆

### spring cloud config server使用git保存配置文件
- [git配置生成的公钥](https://github.com/settings/keys)
  - `settings -> SSH and GPG keys -> click button [new SHH key]`
  - `cat ~/.ssh/id_rsa.pub` 查看，复制粘贴
  - 确认，输入密码
  - 本地服务器配置ssh账号
    - 查看ssh是否运行 `ssh-agent -s`, 正常显示
    ```
    SSH_AUTH_SOCK=/var/folders/y3/_3_xh4hj5y1dp0gx5_4wnbp00000gn/T//ssh-rhZI3zZp67W2/agent.67332; export SSH_AUTH_SOCK;
    SSH_AGENT_PID=67333; export SSH_AGENT_PID;
    echo Agent pid 67333;
    ```
    - 添加 `ssh-add ~/.ssh/id_rsa`,添加成功
    ```
    Identity added: /Users/xx/.ssh/id_rsa (xx8@qq.com)
    ```
    如果失败
    ```
    Could not open a connection to your authentication agent.
    ```
    先执行 `ssh-agent bash`再执行`ssh-add ~/.ssh/id_rsa`
    - 测试`ssh -T git@github.com`  
    - 如果成功 `Hi your name! You've successfully authenticated, but GitHub does not provide shell access.`

### 错误：密钥已被使用
查找已使用密钥的位置  `ssh -T -ai ~/.ssh/id_rsa git@github.com` 
结果
```
Warning: Permanently added the ECDSA host key for IP address '20.205.243.166' to the list of known hosts.
Hi muxianliangqin! You've successfully authenticated, but GitHub does not provide shell access.
```
移除远程服务区缓存的 key
`ssh-keygen -R 192.168.1.123`

### errors
```
The authenticity of host 'github.com (20.205.243.166)' can't be established.
ECDSA key fingerprint is SHA256:p2QAMXNIC1TJYWeIOttrVc98/R1BUFWu3/LiyKgUfQM.
Are you sure you want to continue connecting (yes/no/[fingerprint])?
```
fix by `ssh-keyscan github.com >> ~/.ssh/known_hosts`


