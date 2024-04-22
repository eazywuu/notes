# 部署vite前端+express后端项目

## 1. 服务器安装node.js

下载

```shell
curl -sL https://rpm.nodesource.com/setup_17.x | bash -
```

安装

```shell
yum -y install nodejs
```

检查

```shell
node -v

npm -v
```

## 2. 准备项目

github地址

```bash
git clone git@github.com:eazywuu/yiqing.git
```

## 3. 部署前端项目

首先进入vue-demo文件夹

```shell
cd vue-demo/
```

使用npm打包(使用其他包管理工具也可)

```shell
npm run build
```

云服务器控制台防火墙开放端口

云服务器防火墙开放端口

```shell
开启防火墙端口：firewall-cmd --zone=public --add-port=9200/tcp --permanent

命令含义：
	–zone #作用域
	–add-port=9200/tcp #添加端口，格式为：端口/通讯协议
	–permanent #永久生效，没有此参数重启后失效
	
重新加载配置：firewall-cmd --reload

查看防火墙状态：firewall-cmd --list-port
```

使用xftp将dist文件夹上传到云服务器(略)

使用nginx进行反向代理(略)

npm全局下载serve并后台运行dist

```shell
npm i serve -g

# cd至dist所在文件夹
# 后台运行
serve -s -p 3003 dist &

# 或者使用nohup和&
nohup serve -s -p 3003 dist &

# 注意:
# 第一次退出终端时使用exit命令,而不能直接点击X
# 否则可能会出现退出终端程序被杀死的情况
```

## 4. 部署后端项目

将后端项目直接上传至服务器

npm全局下载ts-node

```shell
npm i ts-node -g
```



进入node-demo文件夹

```shell
cd node-demo/
```

开发端口(略)

使用npm后台运行

```shell
npm run dev &
```

