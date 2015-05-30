This document will help you understand the project architecture, what's in the source and how the game is running on both client and server side.

# Requirements
- NodeJS
- NPM
- Bower
- Socket.IO
- Express

# Architecture
![Server architecture](http://i.imgur.com/Zw561RV.png)

The game runs on a **NodeJS** environment using **Socket.IO** to create a WebSocket server listening on port **3000** (by default).

There's also a **ExpressJS** setup serving a simple HTTP service that displays `index.html`, which has the Canvas element used to render the game and some client side Javascript to coummunicate with the WebSocket server.

# Project Structure
This project has 3 main parts:
- Config files (bower.json, package.json, etc.)
- Client side
- Server side

The config files list the libraries, packages, etc. that are needed for the game to run. You can install all the dependencies with the following command:

```
npm install
```

It will install all the libraries listed in `package.json` and `bower.json`

### Game Client

The client folder contains the code used in the game client. It's just a simple HTML file that creates a `canvas` to render the game and some HTML elements for the chatbox.

The game client logic inside `js/app.js`. It contains the functions to render the game, check ping/latency, toogle dark mode, send chat messages, process game input, and some `socket` event listener to communicate with the server.

No game logic are processed from client side. The only thing related to gameplay on the client side is processing game input (send mouse position to server).

The rendering loop of the game uses `requestAnimationFrame` instead of `setInterval`, and this gives the canvas a better drawing performance.

To compare, you can change the code block:

```
(function animloop(){
  requestAnimFrame(animloop);
  gameLoop();
})();
```

to

```
setInterval(gameLoop, 100);
```

and see the crappy lag :trollface: 

### Game Server

The server code at `server/server.js` contains all the config/information and functions related to the game logic such as: food's mass, movement speed, minimum mass difference to be able to eat, random color, hit test, process player movement, etc.

All the game logic is processed on the server side. The communication between server and client will be explained in the following section.

The player list is handled in the server side, inside the `users` array. The food list is inside the `foods` array. There's also a `sockets` array to store all the socket connections from connected players.

Initially, a simple loop is ran with a `setInterval` on server side to spawn food randomly every second, but running a loop on the server side is a bad idea, as it slows the server down dramatically and causes lag on the client side even if there are only 2 players connected. 

That's why we changed to a new (current) way: When a player connects to the game, the server will spawn **30** new random foods, (note this number can be changed at the `newFoodPerPlayer` variable). And when a player eats a food, **1** new food will be spawned, this number can be changed at the `respawnFoodPerPlayer` variable. If the total number of foods in the game arena is higher than **50** (see `maxFoodCount`), the server will stop serving new foods.

# Client-Server Communication

The communication between the Client and the Server sides can be separated into 2 stages: **Authentication** and **In-Game Communication**

### Authentication

![](http://i.imgur.com/q0WWIxt.png)
 
When a new player connects, a popup will be shown asking their name. Then, a new socket connection will be opened. The server receives this new connection and accept it with `welcome` message, attached with the `UserID` of this client.

When the client receives that `welcome` message, it will reply with a `gotit` message, attached with the `Player's name`. 

When the server receives that `gotit`, it will broadcast it back to every connected player (except the current player) that someone has joined the game with `playerJoin` message. Every players who has connected to the game will receives this message and update their player list (draw new enemy on screen, etc.)

Then, the game starts!

### In-Game Communication
There are 3 types of communication once the game is started: **Game Logic**, **Chat** and **Ping** (check latency)
#### Game Logic
[TBD] 

#### Chat
Chat is implemented using the following diagram:

![](http://i.imgur.com/dbBc8Nc.png)

When a player sends a new message and press enter, a new message will be sent to the server as a **playerChat** message. The server then receives that message and broadcasts it to the other players with **serverSendPlayerChat**. 

When a player receives the **serverSendPlayerChat** message, it will parse the chat message and put it into their chatbox.

#### Ping (Latency)
Every game has `-ping` command to check the latency of a connection to server. It's very easy to implement this latency checking command:

![](http://i.imgur.com/epBau83.png)

At the beginning of the check, we save the start time. Then send a message to server, let's call it **ping**. When the server receives that **ping** message, it will reply back with a **pong** message. And when the **pong** arrives the client side, we can calculate the difference between the start time and end time. As simple as that!