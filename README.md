# ansible-role-demo
ansible role demo

## 安装ansible
```
sudo yum install -y epel-release
sudo yum install -y ansible
```

## 运行role demo
### 配置hosts
添加一个local
```
/bin/echo -e "[local]\nlocalhost ansible_connection=local" >> /etc/ansible/hosts
```
### 编写剧本
创建配置文件ansible-role-demo.yaml
```
hosts: local
  roles:
    - role: ansible-role-demo
```

### 下载安装
[下载地址](https://galaxy.ansible.com/handsomestwei/ansible_role_demo)
```
ansible-galaxy install handsomestwei.ansible_role_demo
```

### 运行剧本
```
ansible-playbook ansible-role-demo.yaml
```

### 查看结果
运行结果输出到/tmp/ansible-output
```
cat /tmp/ansible-output
```

## 其他
### 简短指令ad hoc
```
ansible all -m command -a "echo Hello World"
```

### 初始化role
```
ansible-galaxy init [role name]
```

### 外部role安装
#### 整理依赖 
requirements.yml
```
- src: git@github.com:handsomestWei/ansible-role-demo.git
  scm: git
  version: master
  name: ansible-role-demo
```
#### 安装
通常安装到用户的~/.ansible/roles目录
```
ansible-galaxy install -r roles/requirements.yml -p ./
```

## 参考
[Ansible自动化运维教程](https://www.w3cschool.cn/automate_with_ansible/)
