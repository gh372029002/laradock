# 使用官方的OpenJDK基础镜像
FROM openjdk:8-jre-alpine

# 设置MyCat版本
ENV MYCAT_VERSION 1.6.7.4

# 下载并解压MyCat
RUN apk add --no-cache bash curl && \
    curl -L https://github.com/MyCATApache/Mycat-Server/releases/download/mycat-${MYCAT_VERSION}/mycat-server-${MYCAT_VERSION}-release-20220926-linux.tar.gz -o /tmp/mycat.tar.gz && \
    mkdir /opt/mycat && \
    tar -xzf /tmp/mycat.tar.gz -C /opt/mycat --strip-components=1 && \
    rm /tmp/mycat.tar.gz

# 设置工作目录
WORKDIR /opt/mycat

# 复制配置文件到容器中
COPY conf/schema.xml conf/schema.xml
COPY conf/rule.xml conf/rule.xml
COPY conf/server.xml conf/server.xml

# 暴露MyCat默认端口
EXPOSE 8066 9066

# 启动MyCat服务
CMD ["./bin/mycat", "console"]

