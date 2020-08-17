---
title: hexo quick start
date: 2020-08-17 23:29:05
tags:
---

# 1. 本地环境

* git
* nodejs

```shell
	npm install -g hexo-cli
	npm install -g hexo

```
	
# 2. 测试运行
```shell
mkdir blog
hexo init blog
cd blog
hexo g
hexo server
```
* 打开浏览器查看效果,默认端口4000

# 3. 新建github 项目
    推送刚才新建的目录文件，注意检查.gitignore文件，不要推送public文件夹


# 4. 将 TravisCI 添加到GitHub中
	maketplace中添加 TravisCI
	在GitHub中设置CI可以访问代码仓库
	GitHub中新建一个Token，前往CI，添加新的环境变量
	在项目目录下构建一个CI脚本.travis.yml 
```yml
sudo: false
language: node_js
node_js:
  - 10 # use nodejs v10 LTS
cache: npm
branches:
  only:
    - master # build master branch only
script:
  - hexo generate # generate static files
deploy:
  provider: pages
  skip-cleanup: true
  github-token: $GH_TOKEN
  keep-history: true
  on:
    branch: master
  local-dir: public

```
	推送这个脚本到代码仓库，则CI开始自动构建

# 5. 设置部署分支为gh-pages


# 6. 测试远程访问
  https://<用户名>.github.io

