# 第一天

## 前提

安装 gitops operator 和 pipeline operator
只支持 github 和 gitlab 两种代码仓库形式。

## kam下载

https://github.com/redhat-developer/kam/releases/tag/v0.0.39

## 创建项目

首先需要一个应用仓库，这里从网上克隆
https://gitlabbj.uniontech.com/ut002948/taxi-app

执行命令，创建gitops仓库 gitops-kam-journal ：  
```shell
kam bootstrap    --service-repo-url https://gitlabbj.uniontech.com/ut002948/taxi-app    --gitops-repo-url https://gitlabbj.uniontech.com/ut002948/gitops-kam-journal --git-host-access-token glpat-ry7ZRNqeu-NfT1ZWM6Pw    --image-repo harbor.chinauos.com/jzy-test/gitops-kam-journal:latest    --private-repo-driver gitlab
```

推送 gitops 下的内容。

## 创建argocd
```shell
oc create -k gitops-kam-journal/config/argocd/
application.argoproj.io/argo-app created
application.argoproj.io/cicd-app created
application.argoproj.io/dev-app-taxi-app created
application.argoproj.io/dev-env created
application.argoproj.io/stage-env created
```
注意默认gitops服务账户在其他命名空间里无权限需要添加

## 检查

+ gitops

<img src="./image/day1/1677569921445.png">
