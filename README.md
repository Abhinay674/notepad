2023-04-25 12:39:50.923  INFO 3844 --- [  restartedMain] c.i.i.b.BlenderserviceApplication        : Starting BlenderserviceApplication using Java 17.0.6 on HYDPCM260866L with PID 3844 (D:\Github\ixrvp-blender-conversion-service-master\target\classes started by abhinay.kumar04 in D:\Github\ixrvp-blender-conversion-service-master)
2023-04-25 12:39:50.936  INFO 3844 --- [  restartedMain] c.i.i.b.BlenderserviceApplication        : No active profile set, falling back to default profiles: default
2023-04-25 12:39:51.271  INFO 3844 --- [  restartedMain] .e.DevToolsPropertyDefaultsPostProcessor : Devtools property defaults active! Set 'spring.devtools.add-properties' to 'false' to disable
2023-04-25 12:39:51.272  INFO 3844 --- [  restartedMain] .e.DevToolsPropertyDefaultsPostProcessor : For additional web related logging consider setting the 'logging.level.web' property to 'DEBUG'
2023-04-25 12:39:54.764  INFO 3844 --- [  restartedMain] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat initialized with port(s): 5000 (http)
2023-04-25 12:39:54.794  INFO 3844 --- [  restartedMain] o.apache.catalina.core.StandardService   : Starting service [Tomcat]
2023-04-25 12:39:54.795  INFO 3844 --- [  restartedMain] org.apache.catalina.core.StandardEngine  : Starting Servlet engine: [Apache Tomcat/9.0.46]
2023-04-25 12:39:55.063  INFO 3844 --- [  restartedMain] o.a.c.c.C.[Tomcat].[localhost].[/]       : Initializing Spring embedded WebApplicationContext
2023-04-25 12:39:55.063  INFO 3844 --- [  restartedMain] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 3788 ms
2023-04-25 12:39:56.678  INFO 3844 --- [  restartedMain] o.s.b.d.a.OptionalLiveReloadServer       : LiveReload server is running on port 35729
2023-04-25 12:39:56.827  INFO 3844 --- [  restartedMain] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 5000 (http) with context path ''
2023-04-25 12:39:56.833  INFO 3844 --- [  restartedMain] o.s.a.r.c.CachingConnectionFactory       : Attempting to connect to: [localhost:5672]
2023-04-25 12:39:56.967  WARN 3844 --- [ 127.0.0.1:5672] c.r.c.impl.ForgivingExceptionHandler     : An unexpected connection driver error occured (Exception message: Connection reset)
2023-04-25 12:39:56.995  WARN 3844 --- [:0:0:0:0:1:5672] c.r.c.impl.ForgivingExceptionHandler     : An unexpected connection driver error occured (Exception message: Socket closed)
2023-04-25 12:39:57.001  INFO 3844 --- [  restartedMain] o.s.a.r.l.SimpleMessageListenerContainer : Broker not available; cannot force queue declarations during start: com.rabbitmq.client.AuthenticationFailureException: ACCESS_REFUSED - Login was refused using authentication mechanism PLAIN. For details see the broker logfile.
2023-04-25 12:39:57.031  INFO 3844 --- [ntContainer#0-1] o.s.a.r.c.CachingConnectionFactory       : Attempting to connect to: [localhost:5672]
2023-04-25 12:39:57.056  WARN 3844 --- [ 127.0.0.1:5672] c.r.c.impl.ForgivingExceptionHandler     : An unexpected connection driver error occured (Exception message: Socket closed)
2023-04-25 12:39:57.075  WARN 3844 --- [:0:0:0:0:1:5672] c.r.c.impl.ForgivingExceptionHandler     : An unexpected connection driver error occured (Exception message: Socket closed)
2023-04-25 12:39:57.094 ERROR 3844 --- [ntContainer#0-1] o.s.a.r.l.SimpleMessageListenerContainer : Consumer received fatal exception on startup

org.springframework.amqp.rabbit.listener.exception.FatalListenerStartupException: Authentication failure
	at org.springframework.amqp.rabbit.listener.BlockingQueueConsumer.start(BlockingQueueConsumer.java:602) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.SimpleMessageListenerContainer$AsyncMessageProcessingConsumer.initialize(SimpleMessageListenerContainer.java:1348) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.SimpleMessageListenerContainer$AsyncMessageProcessingConsumer.run(SimpleMessageListenerContainer.java:1193) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at java.base/java.lang.Thread.run(Thread.java:833) ~[na:na]
Caused by: org.springframework.amqp.AmqpAuthenticationException: com.rabbitmq.client.AuthenticationFailureException: ACCESS_REFUSED - Login was refused using authentication mechanism PLAIN. For details see the broker logfile.
	at org.springframework.amqp.rabbit.support.RabbitExceptionTranslator.convertRabbitAccessException(RabbitExceptionTranslator.java:64) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.AbstractConnectionFactory.createBareConnection(AbstractConnectionFactory.java:602) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.CachingConnectionFactory.createConnection(CachingConnectionFactory.java:724) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils.createConnection(ConnectionFactoryUtils.java:216) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils$RabbitResourceFactory.createConnection(ConnectionFactoryUtils.java:295) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils.doGetTransactionalResourceHolder(ConnectionFactoryUtils.java:130) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils.getTransactionalResourceHolder(ConnectionFactoryUtils.java:92) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils.getTransactionalResourceHolder(ConnectionFactoryUtils.java:75) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.BlockingQueueConsumer.start(BlockingQueueConsumer.java:596) ~[spring-rabbit-2.3.7.jar:2.3.7]
	... 3 common frames omitted
Caused by: com.rabbitmq.client.AuthenticationFailureException: ACCESS_REFUSED - Login was refused using authentication mechanism PLAIN. For details see the broker logfile.
	at com.rabbitmq.client.impl.AMQConnection.start(AMQConnection.java:385) ~[amqp-client-5.10.0.jar:5.10.0]
	at com.rabbitmq.client.ConnectionFactory.newConnection(ConnectionFactory.java:1139) ~[amqp-client-5.10.0.jar:5.10.0]
	at com.rabbitmq.client.ConnectionFactory.newConnection(ConnectionFactory.java:1087) ~[amqp-client-5.10.0.jar:5.10.0]
	at org.springframework.amqp.rabbit.connection.AbstractConnectionFactory.connectAddresses(AbstractConnectionFactory.java:640) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.AbstractConnectionFactory.connect(AbstractConnectionFactory.java:615) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.AbstractConnectionFactory.createBareConnection(AbstractConnectionFactory.java:565) ~[spring-rabbit-2.3.7.jar:2.3.7]
	... 10 common frames omitted

2023-04-25 12:39:57.097  WARN 3844 --- [  restartedMain] ConfigServletWebServerApplicationContext : Exception encountered during context initialization - cancelling refresh attempt: org.springframework.context.ApplicationContextException: Failed to start bean 'org.springframework.amqp.rabbit.config.internalRabbitListenerEndpointRegistry'; nested exception is org.springframework.amqp.AmqpIllegalStateException: Fatal exception on listener startup
2023-04-25 12:39:57.104  INFO 3844 --- [  restartedMain] o.s.a.r.l.SimpleMessageListenerContainer : Waiting for workers to finish.
2023-04-25 12:39:57.104  INFO 3844 --- [  restartedMain] o.s.a.r.l.SimpleMessageListenerContainer : Successfully waited for workers to finish.
2023-04-25 12:39:57.106 ERROR 3844 --- [ntContainer#0-1] o.s.a.r.l.SimpleMessageListenerContainer : Stopping container from aborted consumer
2023-04-25 12:39:57.165  INFO 3844 --- [  restartedMain] o.apache.catalina.core.StandardService   : Stopping service [Tomcat]
2023-04-25 12:39:57.202  INFO 3844 --- [  restartedMain] ConditionEvaluationReportLoggingListener : 

Error starting ApplicationContext. To display the conditions report re-run your application with 'debug' enabled.
2023-04-25 12:39:57.274 ERROR 3844 --- [  restartedMain] o.s.boot.SpringApplication               : Application run failed

org.springframework.context.ApplicationContextException: Failed to start bean 'org.springframework.amqp.rabbit.config.internalRabbitListenerEndpointRegistry'; nested exception is org.springframework.amqp.AmqpIllegalStateException: Fatal exception on listener startup
	at org.springframework.context.support.DefaultLifecycleProcessor.doStart(DefaultLifecycleProcessor.java:181) ~[spring-context-5.3.7.jar:5.3.7]
	at org.springframework.context.support.DefaultLifecycleProcessor.access$200(DefaultLifecycleProcessor.java:54) ~[spring-context-5.3.7.jar:5.3.7]
	at org.springframework.context.support.DefaultLifecycleProcessor$LifecycleGroup.start(DefaultLifecycleProcessor.java:356) ~[spring-context-5.3.7.jar:5.3.7]
	at java.base/java.lang.Iterable.forEach(Iterable.java:75) ~[na:na]
	at org.springframework.context.support.DefaultLifecycleProcessor.startBeans(DefaultLifecycleProcessor.java:155) ~[spring-context-5.3.7.jar:5.3.7]
	at org.springframework.context.support.DefaultLifecycleProcessor.onRefresh(DefaultLifecycleProcessor.java:123) ~[spring-context-5.3.7.jar:5.3.7]
	at org.springframework.context.support.AbstractApplicationContext.finishRefresh(AbstractApplicationContext.java:935) ~[spring-context-5.3.7.jar:5.3.7]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:586) ~[spring-context-5.3.7.jar:5.3.7]
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:144) ~[spring-boot-2.4.6.jar:2.4.6]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:771) ~[spring-boot-2.4.6.jar:2.4.6]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:763) ~[spring-boot-2.4.6.jar:2.4.6]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:438) ~[spring-boot-2.4.6.jar:2.4.6]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:339) ~[spring-boot-2.4.6.jar:2.4.6]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1329) ~[spring-boot-2.4.6.jar:2.4.6]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1318) ~[spring-boot-2.4.6.jar:2.4.6]
	at com.infosys.ixrvp.blenderservice.BlenderserviceApplication.main(BlenderserviceApplication.java:10) ~[classes/:na]
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ~[na:na]
	at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:77) ~[na:na]
	at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43) ~[na:na]
	at java.base/java.lang.reflect.Method.invoke(Method.java:568) ~[na:na]
	at org.springframework.boot.devtools.restart.RestartLauncher.run(RestartLauncher.java:49) ~[spring-boot-devtools-2.4.6.jar:2.4.6]
Caused by: org.springframework.amqp.AmqpIllegalStateException: Fatal exception on listener startup
	at org.springframework.amqp.rabbit.listener.SimpleMessageListenerContainer.waitForConsumersToStart(SimpleMessageListenerContainer.java:601) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.SimpleMessageListenerContainer.doStart(SimpleMessageListenerContainer.java:562) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.AbstractMessageListenerContainer.start(AbstractMessageListenerContainer.java:1372) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.RabbitListenerEndpointRegistry.startIfNecessary(RabbitListenerEndpointRegistry.java:299) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.RabbitListenerEndpointRegistry.start(RabbitListenerEndpointRegistry.java:249) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.context.support.DefaultLifecycleProcessor.doStart(DefaultLifecycleProcessor.java:178) ~[spring-context-5.3.7.jar:5.3.7]
	... 20 common frames omitted
Caused by: org.springframework.amqp.rabbit.listener.exception.FatalListenerStartupException: Authentication failure
	at org.springframework.amqp.rabbit.listener.BlockingQueueConsumer.start(BlockingQueueConsumer.java:602) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.SimpleMessageListenerContainer$AsyncMessageProcessingConsumer.initialize(SimpleMessageListenerContainer.java:1348) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.SimpleMessageListenerContainer$AsyncMessageProcessingConsumer.run(SimpleMessageListenerContainer.java:1193) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at java.base/java.lang.Thread.run(Thread.java:833) ~[na:na]
Caused by: org.springframework.amqp.AmqpAuthenticationException: com.rabbitmq.client.AuthenticationFailureException: ACCESS_REFUSED - Login was refused using authentication mechanism PLAIN. For details see the broker logfile.
	at org.springframework.amqp.rabbit.support.RabbitExceptionTranslator.convertRabbitAccessException(RabbitExceptionTranslator.java:64) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.AbstractConnectionFactory.createBareConnection(AbstractConnectionFactory.java:602) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.CachingConnectionFactory.createConnection(CachingConnectionFactory.java:724) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils.createConnection(ConnectionFactoryUtils.java:216) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils$RabbitResourceFactory.createConnection(ConnectionFactoryUtils.java:295) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils.doGetTransactionalResourceHolder(ConnectionFactoryUtils.java:130) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils.getTransactionalResourceHolder(ConnectionFactoryUtils.java:92) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.ConnectionFactoryUtils.getTransactionalResourceHolder(ConnectionFactoryUtils.java:75) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.listener.BlockingQueueConsumer.start(BlockingQueueConsumer.java:596) ~[spring-rabbit-2.3.7.jar:2.3.7]
	... 3 common frames omitted
Caused by: com.rabbitmq.client.AuthenticationFailureException: ACCESS_REFUSED - Login was refused using authentication mechanism PLAIN. For details see the broker logfile.
	at com.rabbitmq.client.impl.AMQConnection.start(AMQConnection.java:385) ~[amqp-client-5.10.0.jar:5.10.0]
	at com.rabbitmq.client.ConnectionFactory.newConnection(ConnectionFactory.java:1139) ~[amqp-client-5.10.0.jar:5.10.0]
	at com.rabbitmq.client.ConnectionFactory.newConnection(ConnectionFactory.java:1087) ~[amqp-client-5.10.0.jar:5.10.0]
	at org.springframework.amqp.rabbit.connection.AbstractConnectionFactory.connectAddresses(AbstractConnectionFactory.java:640) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.AbstractConnectionFactory.connect(AbstractConnectionFactory.java:615) ~[spring-rabbit-2.3.7.jar:2.3.7]
	at org.springframework.amqp.rabbit.connection.AbstractConnectionFactory.createBareConnection(AbstractConnectionFactory.java:565) ~[spring-rabbit-2.3.7.jar:2.3.7]
	... 10 common frames omitted

