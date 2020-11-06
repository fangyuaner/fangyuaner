---
title: "IDEA First"
date: 2020-11-02T23:18:48+08:00
draft: false
---
# IDEA中建一个Springoot项目并运行访问

## 项目的创建

1. 通过网页https://start.spring.io/创建好项目，解压到本地后导入
2. 使用IDEA直接创建项目

## 项目的运行

### 运行方式

1. 直接运行Main方法
2. 使用Maven进行启动
    - 在终端使用命令 ./mvnw spring-boot:run 方法
    - 在IDEA中右侧的Maven中，plugins -> spring-boot -> spring-boot:run 方法，双击
    - 创建一个启动项，调用spring-boot:run方法
    - 将项目编译打包，运行jar包 java -jar + jar地址

## 如何在项目中添加一个Controller

> 在项目src下的java的最后一个目录下创建一个Controller类  
> + 注意点：添加后需要先给类加一个注解@Controller。
> 1. Controller的返回值类型暂且使用Modelndiew 
> 2. 使用ModelAndView时，需要返回一个具体对象  
     ModelAndView的参数有两个(viewName，params)
> 3. 在resources下的templates创建一个名为viewName的模板对象
<hr>

> 问题一：直接启动项目，访问localhost:8080,会提示404错误，原因是需要有一个Controller提供访问路由  
问题二：添加好Controller后，再次访问localhost:8080，会提示500错误，原因是由于没有对应的界面模板template  
问题三：添加好对应的template,但是访问依旧时提示template不存在，错误500，原因是由于添加的HTML文件名称与Controller中的viewName不匹配

## 今日份的注意点

> Maven的作用
1. 管理jar包
2. 管理jar包之间的依赖
3. 将项目模块儿化
4. 能够对项目进行编译、单元测试、打包、部署到本地maven仓/远程maven私服仓等

> IDEA项目创建好后，这几个文件是有什么用途？
mvnw：记录所需要的jar包
mvnw.cmd：用于windows运行maven
.mvn：存放mvnw中记录的jar包

```
现在的阿里云镜像仓库中的地址不是最新的了，已经不使用http了更换https
<!-- 最新阿里maven镜像库 https-->
<mirror>
    <id>aliyunmaven</id>
    <mirrorOf>*</mirrorOf>
    <name>阿里云公共仓库</name>
    <url>https://maven.aliyun.com/repository/public</url>
</mirror>

在IDEA中需要进行一个配置以避免进行SSL验证
Seetings -> Maven -> Importing ->  -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true


```
