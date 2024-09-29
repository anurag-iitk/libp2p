
# libp2p

This is a `libp2p` application that creates a node and allows it to ping other `libp2p` nodes using the `go-libp2p` library. You can either run the node to listen for incoming connections or use it to send ping messages to another node.

## Features

- Creates a `libp2p` node listening on a random TCP port.
- Provides a ping service using the `libp2p` Ping Protocol.
- Can connect to other `libp2p` nodes and send ping requests.
- Gracefully handles shutdown signals (`SIGINT` and `SIGTERM`).

## Installation

1. Clone the repository:

```bash
git clone https://github.com/anurag-iitk/libp2p.git
cd libp2p
```

2. Install the dependencies:

```bash
go mod tidy
```

3. Build the application:

```bash
go build -o libp2p-node
```

## Usage

### Run the Node

By default, the node listens on a random TCP port and waits for incoming connections. To run the node:

```bash
./libp2p-node
```

Upon startup, the node will print its address. Example output:

```bash
libp2p node address: /ip4/127.0.0.1/tcp/12345/p2p/QmSomePeerID
```

### Connect and Ping Another Node

To connect to another node and send 5 ping messages, pass the peer's multiaddress as an argument:

```bash
./libp2p-node /ip4/127.0.0.1/tcp/12345/p2p/QmSomePeerID
```

This will connect to the given node and ping it 5 times. Example output:

```bash
sending 5 ping messages to /ip4/127.0.0.1/tcp/12345/p2p/QmSomePeerID
pinged /ip4/127.0.0.1/tcp/12345/p2p/QmSomePeerID in 50ms
pinged /ip4/127.0.0.1/tcp/12345/p2p/QmSomePeerID in 48ms
pinged /ip4/127.0.0.1/tcp/12345/p2p/QmSomePeerID in 51ms
pinged /ip4/127.0.0.1/tcp/12345/p2p/QmSomePeerID in 49ms
pinged /ip4/127.0.0.1/tcp/12345/p2p/QmSomePeerID in 50ms
```

### Graceful Shutdown

The node will run until it receives a `SIGINT` or `SIGTERM` signal (e.g., pressing `Ctrl+C`). When the signal is received, the node will cleanly shut down.
