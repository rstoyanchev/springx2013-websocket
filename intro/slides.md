!SLIDE subsection

# WebSocket in<br>Spring Framework 4.0 (part 1)
## [Rossen Stoyanchev](https://twitter.com/rstoya05)

!SLIDE small

# Part 1:
## Comprehensive Intro to WebSocket
## in Spring Framework 4.0
<br>
# Part 2:
## Building WebSocket Applications

!SLIDE small
# This Presentation
<br><br>
## [https://github.com/rstoyanchev/](https://github.com/rstoyanchev/springexchange2013-websocket)
## [springx2013-websocket](https://github.com/rstoyanchev/springx2013-websocket)

!SLIDE smaller bullets incremental
# The WebSocket Protocol

* [RFC 6455](http://www.ietf.org/rfc/rfc2616.txt) finalized in Dec-2011
* Two-way communication between browser and server
* Doesn't require multiple HTTP connections
* On the heels of long history

!SLIDE smaller bullets incremental
# How Did We Get Here?

* 1996 - Java Applets/Netscape 2.0
* 1999/2000 - XMLHttpRequest
* 2003 - Macromedia/Adobe Flash
* 2006 - Comet (term by Alex Russel)<br><br><em>XHR long-polling, XHR streaming,<br>htmlfile ActiveXObject, Server-Sent Events, ...</em>

!SLIDE smaller bullets incremental
# How Did We Get Here?

* HTTP async support in Servlet 3.0 
* `Callable` and `DeferredResult`<br>controller return values in Spring MVC 3.2
* Enables HTTP long-polling/streaming

!SLIDE smaller bullets incremental
# How WebSocket Works

* HTTP used for initial handshake only
* Server responds with 101 "Switching Protocols"
* TCP connection used thereafter
* Exchange text (UTF-8) or binary messages

!SLIDE smaller bullets incremental
# Practical Considerations

* Not [supported](http://caniuse.com/websockets) in IE < 10
* [Proxies may fail](http://www.infoq.com/articles/Web-Sockets-Proxy-Servers) the upgrade or close the connection
* It's very low level (thin layer over TCP)
* Messaging architecture

!SLIDE smaller bullets incremental
# Java WebSocket API 

* [JSR-356](http://jcp.org/en/jsr/detail?id=356) finalized in May-2013
* Lots of debate, fast-paced schedule
* A convergance of implementations and APIs<br><em>complete re-writes across containers</em>
* Now better than ever to start using

!SLIDE smaller bullets incremental
# Relation To the Servlet API

* WebSocket discussions started in Servlet 3.1 (JSR-340)<br>then moved into its own JSR
* Designed to have no dependency on the Servlet API
* In practice it comes down to Servlet containers
* Servlet 3.1 exposes hook for upgrade mechanism<br>`HttpServletRequest.upgrade`

!SLIDE smaller bullets incremental
# Server Availability

* Tomcat 8 (currently RC5) + backport to Tomcat 7.0.47<br><em>(existing Tomcat 7 WebSocket support removed)</em>
* Jetty 9 all-new, WebSocket API / impl<br>Jetty 9.1 (currently RC0) adds JSR-356 layer
* Glassfish 4 with Tyrus WebSocket engine
* More on the way with Java EE 7

