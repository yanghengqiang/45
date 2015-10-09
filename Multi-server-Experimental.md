Multi-server
===========

This branch is experimental for multiple server support.

## What changed from master branch?
- Increase inactive timeout from `5000` milisecond to ... i don't remember, just make it as large as possible :trollface: 
- Add `gateway.js` and `npm run cluster` command to start server as a cluster
- Add `redis` for sharing data between servers

## How is the servers look like?

We're running the cluster with 4 instances of `Agar.IO Server` and 1 `Redis` server for transferring messages between instances.

The communication between instances now using Redis's `Publish` and `Subscribe`

======================================================
|                       REDIS                        |
======================================================
||                ||                ||              ||
||                ||                ||              ||
||                ||                ||              ||     
Server #1       Server #2        Server #3       Server #4

By doing this, we can run multiple servers from multiple location but still able to share the data (foods, players, chat messages,...) between them.

## How to use it?

**Step 1: Run the environment**
- Install and run `Redis` with `redis-server` command

**Step 2: Run the server cluster**
- Checkout the `multi-server` branch
- Run the server cluster with: `npm run cluster`

The cluster will start up with 4 server running on http://localhost:3000, http://localhost:3001, http://localhost:3002, and http://localhost:3003

**Step 3: Test multi server function**
- Go to server #1: http://localhost:3000, login with any name you want
- Go to server #2: http://localhost:3001, login with any name you want
- In any client, leave some chat message
- Go to another client to see the message displayed!
