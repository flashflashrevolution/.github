# Security and Secrets

rCubed is desgined to communicate with:

- php endpoints over http.
- smartFoxServer endpoint over a socket.

Neither of these are encrypted, so all information sent over the wire *must* be hashed or encrypted.
