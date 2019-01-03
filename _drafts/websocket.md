- 웹 페이지 로딩 이후, 사용자가 다음 페이지로 클릭하기 전까지는 아무런 일도 일어나지 않았다.
- 2005년 쯤, AJAX가 시작되면서 웹은 좀더 동적으로 변했다.
- 그러나 아직도 HTTP 통신은 사용자의 request에 의해 조종되고 있다.
- 클라이언트는 서버와 통신 후 계속 connection을 유지하여, 빠른 response를 기대할 수 있다.
- 그러나 단점은 HTTP의 부하가 있다는 것.

## WebSocket
브라우저와 서버 사이의 socket connection을 통해(persistant connection) 서버와 클라이언트 모두 자신이 원할 때 데이터를 전송할 수 있다.

## WebSocket(client) 사용하기
```
new Socket("ws://url");
```
- ws : WebSocket connection을 위한 새로운 URL schema
    + wss : https와 같은 secure connection
- Attribute (EventListener Type)
    + onopen : when the WebSocket connection's readyState changes to OPEN; this indicates that the connection is ready to send and receive data.
    + onerror : when an error occurs.
    + onmessage : when a message is received from the server. The listener receives a MessageEvent named "message".
    + onclose : when the WebSocket connection's readyState changes to CLOSED. The listener receives a CloseEvent named "close".
- Method
    + close() : Closes the WebSocket connection or connection attempt, if any.
    + send() : Transmits data to the server over the WebSocket connection.

## WebSocket(server) 사용하기
- npm의 websocket library를 사용
```
var http = require("http");

var server = http.createServer(function(request, response) {
    console.log((new Date()) + " Received request for " + request.url);
    response.writeHead(404);
    response.end();
});

server.listen(8080, function() {
    console.log((new Date()) + " Server is listening on port 8080");
});
```
- 새 서버를 만들기 위해 server를 생성하고, port를 설정한다


```
var WebSocketServer = require("websocket").server;

wsServer = new WebSocketServer({
    httpServer: server
});

wsServer.on("request", function(request) {

});
```
- WebSocket 서버를 생성한다. 
- listening하다가 request event가 발생했을 때 callback function을 설정한다.
    

- callback function 내부에서 할 일
    + Accept the connection  
        ```
        var connection = request.accept(null, request.origin);
        ```
        * 첫번째 parameter는 protocol  
    + Store connected clients
        * 배열에 저장하거나 하는듯 
    + Listen for incoming messages and broadcast messages to clients  
        ```
        connection.on('message', function(message) {
            connection.sendUTF(message);
        });
        ```
    + Listen for a client disconnecting and remove from list of clients  
        ```
        connection.on('close', function(reasonCode, description) {
            console.log((new Date()) + ' Peer ' + connection.remoteAddress + ' disconnected.');
        });
        ```


## Reference
- [html5rocks](http://www.html5rocks.com/en/tutorials/websockets/basics/)
- [MDN](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)
- [Starting with Node and Web Sockets](http://codular.com/node-web-sockets)