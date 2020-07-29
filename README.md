# springCloudConfig

一、使用activeMQ做消息总线（springboot版本1.5.8 springcloud版本Dalston.SR4）
  1）pom文件中加入依赖
        <dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-actuator</artifactId>
		</dependency>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-activemq</artifactId>
		</dependency>
 2）在配置文件中添加如下配置：
 	spring:
	  activemq:
	    broker-url: tcp://your_activemq_ip:61616
	    user: admin
	    password: admin
 3)依次启动eureka-server  config-server  config-client
   第1次访问localhost:8881/hi,会得到一个foo的值
   修改git上的值后，再次访问，还会是上一步的值
   在http工具中使用post请求，访问localhost:8881/refresh后，再次访问localhost:8881/hi，会得到修改后的值
