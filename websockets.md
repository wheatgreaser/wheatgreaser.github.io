# treacherous (not really) forest of websockets
 i wanna learn sockets because i really dont know much about computer networking shit. its fucking humiliating. also i thought sockets sounded fun. msotly the second part. 

## july 1, 2024:
basically http is unidirectional, you send a request to the webserver and it builds a response and sends it to you, its a two step process, connection has to be first established in the "forward" direction then in the "backward" direction. websockets are bidirectional, you can send information back and forth extremely fast, for instance in AJAX we use something calling polling where we constantly perster the webserver, asking if there are any updates. it can be made faster by using something called long polling where we send a request and the webserver holds it till there are new updates. websockets are bidirectional and it creates a connection and keeps it open. so obviously webscokets are fast, itll be useful for realtime updates (stock market app) or for messaging applications.

