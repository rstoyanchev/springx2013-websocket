
!SLIDE smaller bullets incremental
# Spring Framework 4.0

* First class WebSocket support<br>with built-in, transparent [SockJS](sockjs.org) fallback options
* [STOMP](http://stomp.github.io/index.html) over WebSocket support<br>with ability to plug external message broker
* A foundation for messaging architecture-<br>based on core types from __Spring Integration__

!SLIDE smaller
# Example

<br><br>
    @@@ java

    import org.springframework.web.socket.*;


    public class MyHandler extends TextWebSocketHandlerAdapter {


      @Override
      public void handleTextMessage(WebSocketSession session,
          TextMessage message) throws Exception {

        session.sendMessage(message);

      }

    }

!SLIDE smaller
# Basic Config

    @@@ java

    @Configuration

    public class WsConfig implements WebSocketConfigurer {









    }

!SLIDE smaller
# Basic Config

    @@@ java

    @Configuration
    @EnableWebSocket
    public class WsConfig implements WebSocketConfigurer {









    }


!SLIDE smaller
# Basic Config

    @@@ java

    @Configuration
    @EnableWebSocket
    public class WsConfig implements WebSocketConfigurer {


      @Override
      public void registerWebSocketHandlers(
            WebSocketHandlerRegistry registry) {

        registry.addHandler(new MyHandler(), "/echo");
      }

    }

!SLIDE smaller
# Browser client

    @@@ javascript

    var ws = new WebSocket("wss://localhost:8080/myapp/echo");

    ws.onopen = function () {
      console.log("opened");
    };

    ws.onmessage = function (event) {
      console.log('message: ' + event.data);
    };

    ws.onclose = function (event) {
      console.log('closed:' + event.code);
    };

!SLIDE smaller bullets incremental
# `HandshakeInterceptor`

* Access to HTTP request & response<br>before and after handshake
* Can return `false` from `beforeHandshake`
* Can also pass attributes to WebSocketSession<br>e.g. `HttpSessionHandshakeInterceptor`

!SLIDE smaller
# Add Interceptor

    @@@ java

    @Configuration
    @EnableWebSocket
    public class WsConfig implements WebSocketConfigurer {


      @Override
      public void registerWebSocketHandlers(
            WebSocketHandlerRegistry registry) {

        registry.addHandler(echoHandler(), "/echo");

      }

    }

!SLIDE smaller
# Add Interceptor

    @@@ java

    @Configuration
    @EnableWebSocket
    public class WsConfig implements WebSocketConfigurer {


      @Override
      public void registerWebSocketHandlers(
            WebSocketHandlerRegistry registry) {

        registry.addHandler(echoHandler(), "/echo")
            .addInterceptors(new MyHandshakeInterceptor());
      }

    }

!SLIDE smaller bullets incremental
# Per-Session Handler

* A new handler can be created for each new session
* Use `PerConnectionWebSocketHandler`<br>and pass `WebSocketHandler` type to constructor
* __Singleton__ vs __stateful__ handlers
* Instances have DI and lifecycle applied

!SLIDE smaller
# Configure Per-Session Handler

    @@@ java

    @Configuration
    @EnableWebSocket
    public class WsConfig implements WebSocketConfigurer {


      @Bean
      public WebSocketHandler snakeHandler() {
        return new PerConnectionWebSocketHandler(
            SnakeWebSocketHandler.class);
      }









    }

!SLIDE smaller
# Configure Per-Session Handler

    @@@ java

    @Configuration
    @EnableWebSocket
    public class WsConfig implements WebSocketConfigurer {


      @Bean
      public WebSocketHandler snakeHandler() {
        return new PerConnectionWebSocketHandler(
            SnakeWebSocketHandler.class);
      }


      @Override
      public void registerWebSocketHandlers(
            WebSocketHandlerRegistry registry) {

        registry.addHandler(snakeHandler(), "/snake");
      }

    }

!SLIDE smaller bullets incremental
# Deployment Notes

* Config doesn't use JSR-356 deployment mechanism
* HTTP handshakes served by `DispatcherServlet`
* Requires container-specific `RequestUpgradeStrategy`<br>currently supported are Tomcat, Jetty, Glassfish
* See [WEBSOCKET_SPEC-211](https://java.net/jira/browse/WEBSOCKET_SPEC-211) (and vote!)




