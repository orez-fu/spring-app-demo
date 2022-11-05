### Các bước build ứng dụng với Dockerfile

Chia làm 2 stage:

1. Stage 1

- Sử dụng base image ***maven:ibmjava-alpine***

- Copy source code vào image

- Từ source code build ra file ***websocket-demo-0.0.1-SNAPSHOT.jar*** bằng lệnh: `mvn clean package`.

- File ***websocket-demo-0.0.1-SNAPSHOT.jar*** sẽ nằm trong thư mục **target** của source code

2. Stage 2

- Sử dụng base image ***openjdk:8-alpine***

- Copy file ***websocket-demo-0.0.1-SNAPSHOT.jar*** từ stage 1 sang stage 2

- Dùng lệnh sau để start container: `java -Djava.security.egd=file:/dev/./urandom -jar websocket-demo-0.0.1-SNAPSHOT.jar`