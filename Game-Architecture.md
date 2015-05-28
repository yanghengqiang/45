This document will help you understand the project architecture, what's in the source and how the game is running on both client and server side.

# Requirements
- NodeJS
- NPM
- Bower
- Socket.IO
- Express

# Project structure
This project has 3 parts:
- Configure files (bower.json, package.json,...)
- Client
- Server

The configures file contains the libraries, packages that needed for the game to run. You can install all the dependencies with the command:

```
npm install
```

It will install all the libraries defined in `package.json`, and `bower.json`

### Game client

The client folder contains the code for game client. It's just a simple HTML file that create a `canvas` for rendering the game and some HTML elements for the chatbox.

The game client logic are in `js/app.js` file. It contains the functions to render the game, check ping/latency, toogle dark mode, send chat messages, process game input, and some `socket` event listener to communicate with server.

No game logic are processed from client side. The only thing related to gameplay on client side is process game input (send mouse position to server)

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

### Game server

The server code in `server/server.js` file contains all the config/information and functions related to game logic such as: food's mass, movement speed, minimum mass distance to be able to eat, random color, hit test, process player movement... 

All the game logic are processed on server side. The communication between server and client will be explained in the next section.

On server side, we handle the player list in `users` array and the food list in `foods` array. We also have a `sockets` array to store all the socket connection from connected players.

Initially, we run a simple loop with `setInterval` on server side to spawn food randomly every second, but running a looop on server side is a bad idea, it slow the server down dramatically and causing lag on client side even there are only 2 players connected! 

That's why we changed to a new (current) way: When a player connected to the game, server will spawn **30** random foods, this number can be changed by `newFoodPerPlayer` variable. And when a player eat a food, there will be **1** new food spawned, this number configured in `respawnFoodPerPlayer` variable. But if the total number of foods in game arena larger than **50** (see `maxFoodCount`), the server will stop serving foods.

# Client-Server communication

<TBD>