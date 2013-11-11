
!SLIDE smaller bullets incremental
# The Spring Approach

* [STOMP](http://stomp.github.io/) over WebSocket
* Ability to plug message broker for message broadcasting
* New `spring-messaging` module
* Core types from Spring Integration<br>`Message`, `MessageChannel`, `MessageHandler`, etc
* Message processing annotations<br>`@MessageMapping`, `@SubscribeEvent`, etc

!SLIDE smaller bullets incremental
# STOMP

* Simple messaging protocol<br>originally for use form scripting languages (Ruby, Python)
* Widely [supported](http://stomp.github.io/implementations.html#STOMP_Servers) by message brokers
* Can be used over TCP and over WebSocket
* Frames modelled on HTTP

!SLIDE smaller center
# STOMP Frame Content
<br>
![STOMP Frame Content](stomp-frame-content.png)

!SLIDE smaller bullets incremental
# Client-to-Server Commands

* `SEND`
* `SUBSCRIBE`
* `UNSUBSCRIBE`

!SLIDE smaller bullets incremental
# Server-to-Client Commands

* `MESSAGE`
* `ERROR`
* `RECEIPT`
* `ACK`
* `NACK`

!SLIDE smaller bullets incremental
# The `"Destination"` Header

* A key concept in STOMP
* Opaque string, syntax left to server
* Typically path-like URIs (`"/queue/a"`, `"/topic/a"`)
* Message brokers define precise semantics

!SLIDE smaller center
# Client Producing a Message
<br>
![SEND frame](send-frame.png)

!SLIDE smaller center
# Client Subscribing
<br>
![SUBSCRIBE frame](subscribe-frame.png)

!SLIDE smaller center
# Client Receiving a Message
<br>
![MESSAGE frame](message-frame.png)

!SLIDE smaller bullets incremental
# Advantages of Using STOMP
## <em>(vs raw WebSocket)</em>
<br><br>
* Standard message format
* Browser clients, e.g. [stomp.js](https://github.com/jmesnil/stomp-websocket), [msgs.js](https://github.com/cujojs/msgs)
* Common messaging patterns
* Ability to incorporate (full-featured) message broker
* Application-level protocol



