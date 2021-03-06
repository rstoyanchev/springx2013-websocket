
!SLIDE smaller bullets incremental
# The Spring Approach

* [STOMP](http://stomp.github.io/) over WebSocket
* Ability to plug message broker for message broadcasting
* New `spring-messaging` module
* Core types from Spring Integration<br>`Message`, `MessageChannel`, `MessageHandler`, etc
* Message processing annotations<br>`@MessageMapping`, `@SubscribeEvent`, etc

!SLIDE smaller bullets incremental
# STOMP

* Simple messaging protocol<br>originally for use from scripting languages (Ruby, Python)
* Widely [supported](http://stomp.github.io/implementations.html)
* Can be used over WebSocket (origingally over TCP)
* Frames modelled on HTTP

!SLIDE smaller center
# STOMP Frame
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
# `"Destination"` Header

* Opaque string, syntax left to server
* Typically path-like URIs (`"/queue/a"`, `"/topic/a"`)
* Message brokers define semantics

!SLIDE center small
## Keep in mind:
<br>
## A server cannot send unsolicited messages
## client must subscribe first

!SLIDE smaller center
# Example
## Client Sends Message
<br>
![SEND frame](send-frame.png)

!SLIDE smaller center
# Example
## Client Subscribes To Receive Messages
<br>
![SUBSCRIBE frame](subscribe-frame.png)

!SLIDE smaller center
# Example
## Client Receives Message
<br>
![MESSAGE frame](message-frame.png)

!SLIDE smaller bullets incremental
# STOMP vs plain WebSocket
<br><br>
* Standard message format
* Browser client libraries: [stomp.js](https://github.com/jmesnil/stomp-websocket), [msgs.js](https://github.com/cujojs/msgs)
* Support for messaging patterns
* Ability to incorporate (full-featured) message broker
* Application-level protocol<br>so we can useful annotations, etc.




