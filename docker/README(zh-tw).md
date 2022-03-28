# Docker實作

## 安裝

### Windows

* [使用 chocolatey](https://www.how2shout.com/how-to/how-to-install-docker-toolbox-using-chocolatey-choco-on-windows-10.html)

    ``` code=base
    <!-- 若未安裝 Windows的 Containers and Microsoft-Hyper-V -->
    $ choco install Containers Microsoft-Hyper-V --source windowsfeatures
    <!-- 安裝 docker -->
    $ choco install docker-toolbox docker-kitematic virtualbox
    ```

* [使用 winget](https://allthings.how/how-to-install-docker-on-windows-10/)
* [官網手動安裝](https://www.docker.com/get-started/)

### Ubuntu

* [Install using the repository](https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository)
  
    ``` code=bash
    <!-- docker recommended -->
    $ apt-get update
    $ apt-get install ca-certificates curl gnupg lsb-release
    $ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    $ echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu (lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
    $ apt-get update
    $ apt-get install docker-ce docker-ce-cli containerd.io
    ```

* [install-from-a-package](https://docs.docker.com/engine/install/ubuntu/#install-from-a-package)
* [Install using the convenience script](https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script)

### Mac

* [使用 homebrew](https://www.cprime.com/resources/blog/docker-for-mac-with-homebrew-a-step-by-step-tutorial/)
  
    ``` code=bash
    <!-- 安裝docker -->
    $ brew cask install docker
    ```

* [官網手動安裝](https://www.docker.com/get-started/)(:warning:根據電腦晶片種類選擇下載並安裝)

## 開始使用

* docker search
    1. 使用docker hub搜尋相關image
    2. 使用cmd搜尋相關image

    ``` code=bash
    <!-- 搜尋相關image -->
    $ docker search <image name>
    ```

* docker pull
    可以從[Docker Hub](https://hub.docker.com/search?type=image&image_filter=official)上找到需要的image

    ``` code=bash
    <!-- 抓取 image -->
    $ docker pull <images name>
    ```

* docker run

    ``` code=bash
    <!-- 製作一個容器 -->
    $ docker run <images name>
    <!-- 給定容器名稱 -->
    $ docker run --name <the name> <image name>
    <!-- 建立輸入與連線 -->
    $ docker run -it <image name>
    <!-- 使其背景執行 -->
    $ docker run -d <image name>
    ```

    :bookmark: [更詳細的 -itd options](https://jerrymei.cn/docker-run-interactive-tty-detach/)
    :warning: 使用ctrl+p + ctrl+q離開容器，避免其關閉

* docker ps

    ``` code=bash
    <!-- 查看現存的容器 -->
    $ docker ps
    <!-- 查看所有的容器 -->
    $ docker ps -a(--all)
    ```

* docker start
  
    ``` code=bash
    <!-- 啟動容器 -->
    $ docker start <container name>
    <!-- 啟動並進入容器 -->
    $ docker start -a(--attach) <container name>
    ```

* docker attach

    ``` code=bash
    <!-- 進入容器 -->
    $ docker attach <container name>
    ```

* docker restart

    ``` code=bash
    <!-- 重啟容器 -->
    $ docker restart <container name>
    ```

* docker stop

    ``` code=bash
    <!-- 停止容器 -->
    $ docker stop <container name>
    ```

* docker rm

    ```code=bash
    <!-- 移除停止的容器 -->
    $ docker rm <container name>
    ```

* docker rmi

    ```code=bash
    <!-- 移除鏡像 -->
    $ docker rmi <image name>
    ```

## Dockerfile

### 關鍵字

1. FROM
2. MAINTAINER
3. RUN
4. COPY
5. ADD
6. CMD
7. ENTRYPOINT, ENV, ARG, VOLUME, EXPOSE, WORKDIR, USER, HEALTHCHECK, ONBUILD, LABEL
[learn more]((https://www.runoob.com/docker/docker-dockerfile.html))
[more & more](https://www.gss.com.tw/blog/%E6%AF%8F%E6%97%A5%E5%B0%8F%E7%9F%A5%E8%AD%98-5-dockerfile)

### 範例

[Example1](https://ithelp.ithome.com.tw/articles/10191016?sc=hot)

``` code=bash
<!--  使用到的 Docker Image 名稱 -->
FROM centos:7
<!-- 用來說明，撰寫和維護這個 Dockerfile 的人是誰，也可以給 E-mail的資訊 -->
MAINTAINER jack

<!-- 執行指令 -->
RUN yum install -y wget
RUN cd /

<!-- 把 Local 的檔案複製到 Image 裡，如果是 tar.gz 檔複製進去 Image 時會順便自動解壓縮 -->
ADD jdk-8u152-linux-x64.tar.gz /

RUN wget http://apache.stu.edu.tw/tomcat/tomcat-7/v7.0.82/bin/apache-tomcat-7.0.82.tar.gz
RUN tar zxvf apache-tomcat-7.0.82.tar.gz

ENV JAVA_HOME=/jdk1.8.0_152
ENV PATH=$PATH:/jdk1.8.0_152/bin
CMD ["/apache-tomcat-7.0.82/bin/catalina.sh", "run"]
```

* docker build
  
    ``` code=bash
    <!-- 建立客製化的image -->
    $ docker build <image name> <path to dockerfile>
    <!-- 建立帶有tag的客製化的image -->
    $ docker build -t <image name>:<tag> <path to dockerfile>
    
    <!-- example -->
    $ docker build -t nginx:v3 .
    ```