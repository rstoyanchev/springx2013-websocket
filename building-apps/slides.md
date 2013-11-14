!SLIDE subsection

# WebSocket Apps<br>Spring Framework 4 (part 2)
## [Rossen Stoyanchev](https://twitter.com/rstoya05)

!SLIDE smaller bullets incremental
# Non-Trivial Applications

* WebSocket is quite low level
* Thin layer above TCP
* A stream of messages rather than bytes
* Arguably not an application-level protocol like HTTP

!SLIDE small
## Using a WebSocket API is a bit like
## writing a __custom Servlet__ application

!SLIDE small
## Except WebSocket is even lower level

!SLIDE small
## You'll likely have 1 WebSocket handler
## for the whole application

!SLIDE small
## Annotations can't help much either...

!SLIDE small
## ...not without making assumptions about 
## what's in a message!

!SLIDE

 <blockquote>"The basic issue is there isn't enough information in an incoming websocket message for the container to know where to route it if there are multiple methods where it may land."</blockquote>
<br><br>
Danny Coward, __JSR-356 lead__<br>In [response to question](https://java.net/projects/websocket-spec/lists/users/archive/2013-03/message/69) on user mailing list

!SLIDE

<blockquote>"The subprotocol attribute of the handshake might serve as a useful place to attach this kind of message description/meta data, or some JSR356 specific headers in the handshake. Of course, the other issue is that the other end is often javascript, which would need to participate in some way in such a scheme."</blockquote>

<blockquote>"These are all things we'll likely look at in the next version."</blockquote>

From next [reply](https://java.net/projects/websocket-spec/lists/users/archive/2013-03/message/72) on same thread

!SLIDE smaller bullets incremental
# The Sub-protocol Attribute

* WebSocket defines the use of [sub-protocols](http://tools.ietf.org/html/rfc6455#section-1.9)<br>i.e. higher-level protocols
* ...but does not require it
* Either way apps are going to choose a message format<br>be it custom, standard, or framework-specific
* The choice has implications for client and server

!SLIDE smaller bullets incremental
# Furthermore..

* WebSocket implies a messaging architecture
* Completely different from HTTP/REST--<br>asynchronous, event-driven, reactive
* Closer to traditional messaging (JMS, AMQP, etc)
* Still a web application though

!SLIDE smaller bullets incremental
# Message Brokers an Option?

* It's possible to [connect to RabbitMQ](http://www.rabbitmq.com/blog/2012/05/14/introducing-rabbitmq-web-stomp/), [ActiveMQ](http://activemq.apache.org/stomp),<br>and others from a browser
* Messaging is a hard problem<br>and brokers have worked on it for a long time
* Traditionally used within enterprise
* Not over the web

!SLIDE smaller bullets incremental
# We Need a Bit of Both Worlds

* Event-driven, messaging achitecture
* Ideally have option to incorporate message broker
* Yet remain close to the needs of web applications

!SLIDE smaller center
# Many Approaches Exist
<br><br>
![Logos of projects](logos.png)


