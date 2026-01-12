Go Ethereum (Geth)

Go Ethereum is the official Golang implementation of the Ethereum execution layer, providing a robust, production-grade client for interacting with the Ethereum protocol.

Geth enables developers, operators, and organizations to run Ethereum nodes, deploy smart contracts, interact with the blockchain via APIs, and build infrastructure on top of Ethereum.

📚 Resources

API Reference

Go Report Card

CI / Build Status

Community: Discord · Twitter

Precompiled binaries for stable releases and the development (master) branch are available at:
https://geth.ethereum.org/downloads/

🛠 Building from Source

For detailed setup instructions and prerequisites, refer to the official Installation Guide.

Requirements

Go (version 1.23+)

C compiler

Supported operating systems: Linux, macOS, Windows

Once dependencies are installed, build Geth using:

make geth


To build the full suite of utilities:

make all

📦 Executables

The cmd/ directory contains the following executables:

Command	Description
geth	The primary Ethereum CLI client. Supports mainnet, testnets, and private networks. Can operate as a full node, archive node, or light client. Exposes JSON-RPC APIs over HTTP, WebSocket, and IPC.
clef	A standalone signing tool that can act as an external transaction signer for geth.
devp2p	Networking utilities for interacting with Ethereum’s peer-to-peer layer without running a full node.
abigen	Generates type-safe Go bindings from Ethereum contract ABIs or Solidity source files.
evm	A developer-focused Ethereum Virtual Machine for debugging and executing bytecode in isolation.
rlpdump	Converts binary RLP-encoded data into a readable hierarchical format.

For CLI options, run:

geth --help

▶ Running Geth

Due to the large number of configuration flags, only common use cases are covered here. For full details, see the CLI documentation.

💻 Hardware Requirements
Minimum

4-core CPU

8 GB RAM

1 TB free disk space (Mainnet sync)

8 Mbps internet connection

Recommended

8+ core CPU

16 GB+ RAM

High-performance SSD (1 TB+ free)

25+ Mbps internet connection

🌐 Running a Full Node (Mainnet)

For most users who want to interact with Ethereum (send transactions, deploy contracts, query state):

geth console


This will:

Start Geth in snap sync mode (default)

Launch the interactive JavaScript console

Enable access to management and Web3 APIs

Note: The bundled Web3 console uses an older API version and may differ from current Web3.js documentation.

🧪 Running a Full Node (Holesky Testnet)

For development and testing without real funds:

geth --holesky console


This configuration:

Connects to the Holesky test network

Uses separate data directories and network IDs

Prevents accidental cross-network transactions

⚠️ Always use separate accounts for testnet and mainnet.

⚙ Configuration Files

Instead of CLI flags, Geth supports TOML-based configuration files:

geth --config /path/to/config.toml


Generate a configuration template from existing flags:

geth --your-flags dumpconfig

🐳 Docker Quick Start

Run a Geth node using Docker:

docker run -d --name ethereum-node \
  -v /Users/alice/ethereum:/root \
  -p 8545:8545 -p 30303:30303 \
  ethereum/client-go


This setup:

Runs in snap sync mode

Allocates 1GB DB memory

Persists blockchain data locally

To expose RPC externally, include:

--http.addr 0.0.0.0

🔌 Programmatic Access (JSON-RPC)

Geth exposes JSON-RPC APIs via:

IPC (enabled by default)

HTTP

WebSocket

Common Flags

HTTP

--http
--http.addr
--http.port
--http.api
--http.corsdomain


WebSocket

--ws
--ws.addr
--ws.port
--ws.api
--ws.origins


IPC

--ipcdisable
--ipcpath


⚠️ Security Warning:
Exposing HTTP/WS APIs publicly can compromise your node. Only enable these interfaces with proper network controls.

🔒 Private Networks

After Ethereum’s Merge, private networks require both:

Execution layer (Geth)

Consensus layer (Beacon client)

Supported options:

Simulated Backend – CI and automated testing

Dev Mode – Single-node local testing

Kurtosis – Multi-node test networks

🤝 Contributing

We welcome contributions of all sizes.

Contribution Guidelines

Follow Go formatting (gofmt)

Document code using Go conventions

Base PRs on the master branch

Prefix commits with affected packages

Example:

eth, rpc: make trace configs optional


For major changes, discuss first on the Discord server.

🌍 Website Contributions

Website-related contributions should target the website branch.
Refer to the website README for additional instructions.

📄 License

Library code: GNU LGPL v3.0

Binary executables: GNU GPL v3.0

License files:

COPYING.LESSER
