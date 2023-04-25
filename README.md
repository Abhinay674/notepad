2023-04-25 08:34:40.146  INFO 776238 --- [           main] w.s.c.ServletWebServerApplicationContext : Root WebApplicationContext: initialization completed in 1907 ms
2023-04-25 08:34:41.267  INFO 776238 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 5000 (http) with context path ''
2023-04-25 08:34:41.270  INFO 776238 --- [           main] o.s.a.r.c.CachingConnectionFactory       : Attempting to connect to: [localhost:5672]
2023-04-25 08:34:41.334  INFO 776238 --- [           main] o.s.a.r.c.CachingConnectionFactory       : Created new connection: rabbitConnectionFactory#3569fc08:0/SimpleConnection@7bb3a9fe [delegate=amqp://guest@127.0.0.1:5672/, localPort= 50332]
2023-04-25 08:34:41.403  INFO 776238 --- [           main] c.i.i.b.BlenderserviceApplication        : Started BlenderserviceApplication in 4.235 seconds (JVM running for 5.052)
MessagesRecieved V: [GenericMessage [payload=byte[0], headers={amqp_receivedDeliveryMode=NON_PERSISTENT, amqp_receivedRoutingKey=ixrvp-blender-process-queue, amqp_deliveryTag=1, amqp_consumerQueue=ixrvp-blender-process-queue, amqp_redelivered=false, id=387ac04a-82eb-4cbf-1549-a49fd5fb9236, amqp_consumerTag=amq.ctag-XwBGnaa1EfWx23RQXlgHaw, amqp_lastInBatch=false, timestamp=1682412001849}]]
Batch 1 Recieved : 1
com.fasterxml.jackson.databind.exc.MismatchedInputException: No content to map due to end-of-input
 at [Source: (byte[])""; line: 1, column: 0]
        at com.fasterxml.jackson.databind.exc.MismatchedInputException.from(MismatchedInputException.java:59)
        at com.fasterxml.jackson.databind.ObjectMapper._initForReading(ObjectMapper.java:4668)
        at com.fasterxml.jackson.databind.ObjectMapper._readMapAndClose(ObjectMapper.java:4513)
        at com.fasterxml.jackson.databind.ObjectMapper.readValue(ObjectMapper.java:3529)
        at com.infosys.ixrvp.blenderservice.service.MsgProcessor.processIncomingMessages(MsgProcessor.java:33)
        at com.infosys.ixrvp.blenderservice.config.RabbitMQConfig.consumerBatch1(RabbitMQConfig.java:44)
        at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at java.base/jdk.internal.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
        at java.base/jdk.internal.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.base/java.lang.reflect.Method.invoke(Method.java:566)
        at org.springframework.messaging.handler.invocation.InvocableHandlerMethod.doInvoke(InvocableHandlerMethod.java:171)
        at org.springframework.messaging.handler.invocation.InvocableHandlerMethod.invoke(InvocableHandlerMethod.java:120)
        at org.springframework.amqp.rabbit.listener.adapter.HandlerAdapter.invoke(HandlerAdapter.java:68)
        at org.springframework.amqp.rabbit.listener.adapter.MessagingMessageListenerAdapter.invokeHandler(MessagingMessageListenerAdapter.java:222)
        at org.springframework.amqp.rabbit.listener.adapter.MessagingMessageListenerAdapter.invokeHandlerAndProcessResult(MessagingMessageListenerAdapter.java:150)
        at org.springframework.amqp.rabbit.listener.adapter.BatchMessagingMessageListenerAdapter.onMessageBatch(BatchMessagingMessageListenerAdapter.java:80)
        at org.springframework.amqp.rabbit.listener.AbstractMessageListenerContainer.doInvokeListener(AbstractMessageListenerContainer.java:1646)
               
