FROM eclipse-temurin:17.0.12_7-jdk-jammy

LABEL authors="JinBooks <support@jinbooks.com>"
LABEL description="JinBooks财务记账系统 - 后端服务"
LABEL version="1.1.0"

RUN mkdir -p /jinbooks

WORKDIR /jinbooks

ARG JAR_FILE=../build/jinbooks-boot-*-ga.jar

COPY ${JAR_FILE} jinbooks-boot.jar

EXPOSE 2154

ENV TZ=Asia/Shanghai JAVA_OPTS="-XX:MaxRAMPercentage=75.0 -XX:InitialRAMPercentage=50.0 -XX:MinRAMPercentage=25.0 -Djava.security.egd=file:/dev/./urandom"

HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD curl -f http://localhost:2154/jinbooks-api/actuator/health || exit 1

CMD ["sh", "-c", "exec java $JAVA_OPTS -jar jinbooks-boot.jar"]