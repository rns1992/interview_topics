## Interview Questions for Rabbir MQ

#### Q. What is RabbitMq?
- It is a message broker or event manager where queues are defined and application connects to it in order to transfer messages.

#### Q. Which protocol is used in Rabbit MQ?
- AMQP (Advanced Message Queuing Protocol)

#### Q. What is message broker?
- It is a middleman where various services connects and transfer messages. It reduces loads and delivery time of web application servers by delegating task that would normally take lot of time and resoource.

#### Q. What are exchanges?
- In rabbitMq, maggessages are not published directly to a queue. Instead, the producers sends messages to an exchange.  An exchange is responsible for routing the messages to different queues with the help of bindings and routing keys. A binding is a link between a queue and an exchange.

#### Q. What is the flow of message in RabbitMq?
1. The producer publishes a message to an exchange. When creating an exchange, the type must be specified. 
2. The exchange receives the message and is now responsible for routing the message. The exchange takes different message attributes into account, such as the routing key, depending on the exchange type.
3. Bindings must be created from the exchange to queues. 
4. The messages stay in the queue until they are handled by a consumer
5. The consumer handles the message.

#### Q. Types of exchanges?
##### Direct: 
- The message is routed to the queues whose binding key exactly matches the routing key of the message. For example, if the queue is bound to the exchange with the binding key pdfprocess, a message published to the exchange with a routing key pdfprocess is routed to that queue.
##### Fanout: 
- A fanout exchange routes messages to all of the queues bound to it.
##### Topic: 
- The topic exchange does a wildcard match between the routing key and the routing pattern specified in the binding
##### Headers:
- Headers exchanges use the message header attributes for routing.

#### Q. What is routing key in Rabbit Mq?
- A key that the exchange looks at to decide how to route the message to queues. Think of the routing key like an address for the message.

#### Q. What is Binding in Rabbit Mq?
- A binding is a link between a queue and an exchange.

#### Q. What is Channel in RabbitMq?
- A virtual connection inside a connection. When publishing or consuming messages from a queue - it's all done over a channel.
