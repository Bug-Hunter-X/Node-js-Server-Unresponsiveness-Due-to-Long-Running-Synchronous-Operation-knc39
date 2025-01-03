# Node.js Server Unresponsiveness Bug

This repository demonstrates a common Node.js issue: server unresponsiveness caused by a long-running synchronous operation within the request handler.  The `server.js` file contains the buggy code, while `serverSolution.js` provides the corrected version.

The bug arises because the `while` loop in the request handler keeps the event loop blocked for 5 seconds. During this time, the server cannot accept or process any new requests, leading to unresponsiveness.  This highlights the importance of asynchronous programming in Node.js to prevent blocking the event loop.

**How to reproduce:**
1. Clone this repository.
2. Run `node server.js`.
3. Try to access `http://localhost:3000` in your browser. You'll see a delay of 5 seconds before receiving the response.  Try making multiple requests during that time; they will all hang.
4. Run `node serverSolution.js`. You'll see immediate response and handling of multiple requests without any hang.