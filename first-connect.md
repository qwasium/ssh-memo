# Connecting to a server with public key auth for the first time

When connecting to a server for the first time, and that server has password authentication disable (which is good), the client and server must exchange their public keys.

## Adding client public key to server

The client will first need to register its public key to the server (otherwise the server will reject the connection).

Since the server has disabled password authentication, `ssh-copy-id` cannot be used.

You will need to register the client public key to the server's `~/.ssh/authorized_keys`.

- There is a web GUI to register client public key.
- Email the client public key to server admin.
- Server is locally hosted and you have physical access.
- Another ssh client that has already established an ssh connection.

### Cheatsheet

1. copy from ssh client: `~/.ssh/<key name>.pub`
2. paste to ssh server: `~/.ssh/authorized_keys`

## Adding server public key to client

Technically, he client doesn't need to know the public key of the server.

But the default config doesn't allow to connect to an unknown server to prevent man-in-the-middle attack.

All the hosts are in `~/.ssh/known_hosts`.

The config is set in `/etc/ssh/ssh_config`.

- `StrictHostKeyCheckihg yes`

Changing this in `ssh_config` or via `ssh -o` is not recommended.

### Cheatsheet

Scan the public key of the server and add it to `~/.ssh/known_hosts`.

```bash
# specify key type to use
# ssh-keyscan -t <key type> <ip address of server> >> ~/.ssh/known_hosts
ssh-keyscan -t ed25519 <ip-address>
```

Then, connect as usual.
Also, probably a good idea to write to `~/.ssh/config` (see [overview](overview.md)).

```bash
# -i identity file
# -p port number
ssh -i <private key> <server user>@<server address> -p <port>
```
