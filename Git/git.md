# 1 git与github或gitee

## 1.1 生成添加ssh密钥

```bash
// 后面填写git配置的邮箱地址
ssh-keygen -t rsa -C "your_email@example.com"
```

## 1.2 使用模板仓库初始化为本地项目

使用degit [ 类似于git clone 更好用 ]

```shell
// 全局下载degit
npm install -g degit
```

```bash
// 通过模板创建项目
// ssh
degit git@github.com:eazywuu/xxx.git project-name
// https
degit https://github.com/eazywuu/xxx.git project-name
```

## 1.3 将本地项目上传到github仓库

vscode快速打开本地项目

```bash
code project-name/
```

初始化本地仓库 生成.git文件

```bash
git init
```

在github或gitee创建远程仓库(略)

关联本地仓库和远程仓库

```bash
// ssh
git remote add origin git@github.com:eazywuu/xxx.git

// https
git remote add origin https://github.com/eazywuu/xxx.git

// 查看远端名称，默认是origin，取决于远端服务器设置
git remote [-v]
```

先拉取远程仓库(防止冲突)

```bash
git pull
```

推送本地仓库至远程仓库

``` bash
// 将项目添加到暂存区
git add .

// 查看状态 (可不做)
git status

// 将暂存区里的文件提交,并描述
git commit -m "xxx"

// 查看日志 (可不做)
git log

// 推送到远端仓库
git push
```

## 1.4 git分支管理

