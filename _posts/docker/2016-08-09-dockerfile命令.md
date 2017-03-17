---
layout: post
title:  "dockerfile命令"
date:   2016-08-09
categories: [docker]
---

# dockerfile
&nbsp;&nbsp;Dockfile是一种被Docker程序解释的脚本，Dockerfile由一条一条的指令组成，每条指令对应Linux下面的一条命令。Docker程序将这些Dockerfile指令翻译真正的Linux命令。Dockerfile有自己书写格式和支持的命令，Docker程序解决这些命令间的依赖关系.通过dockerfile生产自定义的image镜像

## run
&nbsp;&nbsp;执行linux命令,RUN命令是Dockerfile执行命令的核心部分。它接受命令作为参数并用于创建镜像。不像CMD命令，RUN命令用于创建镜像（在之前commit的层之上形成新的层）

```python
# Print "Hello docker!"
RUN echo "Hello docker!"
# Usage: RUN [command]
RUN aptitude install -y riak
```

## ADD
&nbsp;&nbsp;ADD命令有两个参数，源和目标。它的基本作用是从源系统的文件系统上复制文件到目标容器的文件系统。如果源是一个URL，那该URL的内容将被下载并复制到容器中。

```python
# Usage: ADD [source directory or URL] [destination directory]
ADD /my_app_folder /my_app_folder 
```

## CMD
&nbsp;&nbsp;和RUN命令相似，CMD可以用于执行特定的命令。和RUN不同的是，这些命令不是在镜像构建的过程中执行的，而是在用镜像构建容器后被调用。

```php
# Usage 1: CMD application "argument", "argument", ..
CMD "echo" "Hello docker!"
```

## ENTRYPOINT
&nbsp;&nbsp;ENTRYPOINT 帮助你配置一个容器使之可执行化，如果你结合CMD命令和ENTRYPOINT命令，你可以从CMD命令中移除“application”而仅仅保留参数，参数将传递给ENTRYPOINT命令。

```php
# Usage: ENTRYPOINT application "argument", "argument", ..
# Remember: arguments are optional. They can be provided by CMD
# or during the creation of a container.
ENTRYPOINT echo
# Usage example with CMD:
# Arguments set with CMD can be overridden during *run*
CMD "Hello docker!"
ENTRYPOINT echo
```

## ENV
NV命令用于设置环境变量。这些变量以”key=value”的形式存在，并可以在容器内被脚本或者程序调用。这个机制给在容器中运行应用带来了极大的便利。

```php
# Usage: ENV key value
ENV SERVER_WORKS 4
```

## EXPOSE
EXPOSE用来指定端口，使容器内的应用可以通过端口和外界交互。

```php
# Usage: EXPOSE [port]
EXPOSE 8080
```

## FROM
&nbsp;&nbsp;FROM命令可能是最重要的Dockerfile命令。改命令定义了使用哪个基础镜像启动构建流程。基础镜像可以为任意镜 像。如果基础镜像没有被发现，Docker将试图从Docker image index来查找该镜像。FROM命令必须是Dockerfile的首个命令。

```php
# Usage: FROM [image name]
FROM ubuntu 
```

## MAINTAINER
&nbsp;&nbsp;我建议这个命令放在Dockerfile的起始部分，虽然理论上它可以放置于Dockerfile的任意位置。这个命令用于声明作者，并应该放在FROM的后面

```php
# Usage: MAINTAINER [name]
MAINTAINER authors_name 
```

## USER
USER命令用于设置运行容器的UID。

```php
# Usage: USER [UID]
USER 751
```

## VOLUME
VOLUME命令用于让你的容器访问宿主机上的目录。

```
# Usage: VOLUME ["/dir_1", "/dir_2" ..]
VOLUME ["/my_files"]

```

## WORKDIR
WORKDIR命令用于设置CMD指明的命令的运行目录。

```
# Usage: WORKDIR /path
WORKDIR ~/
```








* 目录
{:toc #cntNav}















