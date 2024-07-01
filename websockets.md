# treacherous (not really) forest of websockets
 i wanna learn sockets because i really dont know much about computer networking shit. its fucking humiliating. also i thought sockets sounded fun. msotly the second part. check ouot the code [here](https://github.com/wheatgreaser/socketing).

## july 1, 2024:
basically http is unidirectional, you send a request to the webserver and it builds a response and sends it to you, its a two step process, connection has to be first established in the "forward" direction then in the "backward" direction. websockets are bidirectional, you can send information back and forth extremely fast, for instance in AJAX we use something calling polling where we constantly perster the webserver, asking if there are any updates. it can be made faster by using something called long polling where we send a request and the webserver holds it till there are new updates. websockets are bidirectional and it creates a connection and keeps it open. so obviously webscokets are fast, itll be useful for realtime updates (stock market app) or for messaging applications.

i'm making making use of threading so that the server can handle multiple client requests at once (not my idea im just following a tutorial). basically we have 2 methods, the start method that establishes the connection and the handle_client method that talks to each client, so we use multithreading to execute an intance of the handle_client for every client. when we recieve a message from the client the first message is going to tell us how many bytes it is, then we ge tthe actual message.

so the serverside is done. YES IT CONNECTED HAHA YES LETS UFCKING GOGOGOGOGOO. I SENT A MESSAGE. basically to send a message you need to send the length of the message but to send the length you need to set the bytes of the original message containing the length of the following message. so i padded the first message such that it added up to 64 bytes and sent it (it contains the length of the next message). then i sent the next message, badabing badaboom socket communication in python. 


