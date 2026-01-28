# Blockchain Study

This project is a simple implementation of a blockchain based on Python, designed for educational purposes to understand the core concepts of cryptocurrency and blockchain technology.

## Features

- **Blockchain Core**: A basic blockchain implementation with support for blocks, transactions, and hashing.
- **Proof of Work (PoW)**: Uses SHA-256 hashing with a difficulty requirement (4 leading zeros) to secure the network.
- **Decentralization**: Support for multiple nodes and a consensus algorithm (Conflict Resolution) that follows the "Longest Chain" rule.
- **HTTP API**: A Flask-based RESTful API to interact with the blockchain.

## Getting Started

### Prerequisites

- Python 3.13 or higher
- [uv](https://github.com/astral-sh/uv) (recommended) or `pip`

### Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd blockchain
   ```

2. Install dependencies:
   Using `uv`:
   ```bash
   uv sync
   ```
   Or using `pip`:
   ```bash
   pip install flask requests
   ```

## Usage

### Running the Node

To start a blockchain node, run:

```bash
python main.py
```

The server will start on `http://localhost:5000`.

### API Endpoints

- `GET /mine`: Tells the server to mine a new block.
- `POST /transactions/new`: Creates a new transaction to a block.
  - Body: `{"sender": "...", "recipient": "...", "amount": 5}`
- `GET /chain`: Returns the full Blockchain.
- `POST /nodes/register`: Accepts a list of new nodes in the form of URLs.
  - Body: `{"nodes": ["http://localhost:5001"]}`
- `GET /nodes/resolve`: Implements the consensus algorithm, resolving any conflicts to ensure a node has the correct chain.

### Examples

**Mine a block:**
```bash
curl http://localhost:5000/mine
```

**Create a transaction:**
```bash
curl -X POST -H "Content-Type: application/json" -d '{
 "sender": "d4ee26eee15148ee92c6cd394edd974e",
 "recipient": "someone-other-address",
 "amount": 5
}' http://localhost:5000/transactions/new
```

**View the chain:**
```bash
curl http://localhost:5000/chain
```

## Technologies Used

- **Python**: Core programming language.
- **Flask**: Web framework for the API.
- **Requests**: For communication between nodes.
- **Hashlib**: For SHA-256 hashing.
