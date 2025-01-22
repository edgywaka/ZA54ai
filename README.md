
![Logo](https://i.imgur.com/tqkWIdc.jpeg)

# ZA54ai Sabiaterminal Framework
##### The ZA54ai Framework is an open-source system that empowers users to create Artificial Linguistic Internet Computer Entities (ALICEs) via their CLI, with ZA54ai serving as a co-pilot to assist in building them. The ZA54ai API facilitates interaction with the ALICEs created through the ZA54ai Framework.

### 🌟 Key Features
- **Entity Deployment**: Deploy custom Artificial Linguistic Internet Computer Entities (ALICEs) onto blockchain networks.
- **Entity Interaction**: Use natural language queries to interact with deployed ALICEs.
- **Token Analytics**: Fetch real-time blockchain data, including token market cap, top holders, and trading activity.
- **Trend Insights**: Discover trending tokens and analyze trading patterns.
- **Custom Queries**: Execute powerful custom queries for advanced data analysis.
- **Bitquery Integration**: Seamlessly integrates with Bitquery APIs to fetch blockchain data.

### 🛠 Framework Capabilities:
- **Token Interaction**: Query token metrics such as market cap and top holders.
- **Trading Analytics**: Identify trending tokens and analyze transaction data.
- **Customizable Commands**: Easily define custom scripts for ALICE interaction and deployment.
- **Cross-Platform**: Fully compatible with modern Node.js environments.

## 🚀 Quick Start
### Prerequisites
- Node.js (>= 16.x)
- npm (or yarn) installed
- A valid Bitquery API key
- Refer to `.env.example` for additional prerequisites

### Installation 
1. Clone the repository
``` bash 
git clone https://github.com/za54ai/sabiaterminal-framework-v.1.git
cd sabiaterminal-framework-v.1
```
2. Install dependencies:
``` bash
npm install
```
3. Set up environment variables: Create a `.env` file in the root directory and add the following variables:
 
```bash
PRIVATE_KEYPAIR=<YOUR_PRIVATE_KEYPAIR>
OPENAI_API_KEY=<YOUR_OPENAI_API_KEY> 
RPC_ENDPOINT=https://api.mainnet-beta.solana.com 
Add your Bitquery API in interactALICE.ts 
```
4. Build the Framework
```bash
npm run build
```

## 📜 Available Commands
1. Ask Queries to an ALICE:
```bash
npm run askza54ai {aliceName} {yourQuestion}
```
   - Example:
   ```bash
   npm run askza54ai Sabi "What is the market cap of Solana?"
   ```
2. Deploy an ALICE or Token:
- Go to `defineALICE.ts` and replace placeholders as needed. 
- Then run:
```bash 
npm run build 
```
```bash
npm run deployza54ai
```
- Deploys a new ALICE or token to the blockchain.

3. Interact with an ALICE:
```bash
npm run interactza54ai {alice_name} ask "Your question"
```
- Example:
```bash
npm run interactza54ai Sabi ask "Trending token 24h"
```
4. Fetch Trending Tokens:
```bash 
npm run interactza54ai Sabi ask "Trending token 24h"
```
5. Fetch Top Token Holders:
```bash
npm run interactza54ai Sabi ask "Top holders: {mintAddress}"
```
- Example:
```bash
npm run interactza54ai Sabi ask "Top holders: 6LKbpcg2fQ84Ay3kKXVyo3bHUGe3s36g9EVbKYSupump"
```
6. Fetch Market Cap Data:
```bash
npm run interactza54ai Sabi ask "Marketcap count:{count} term:\"{term}\""
``` 
- Example:
```bash
npm run interactza54ai Sabi ask "Marketcap count:50 term:\"pump\""
```
7. Fetch First Top Buyers:
```bash
npm run interactza54ai {aliceName} ask "First top {count} buyers for: {mintAddress}"
```
- Example: 
```bash 
npm run interactza54ai Sabi ask "First top 10 buyers for: 6LKbpcg2fQ84Ay3kKXVyo3bHUGe3s36g9EVbKYSupump"
```
8. Trade Tokens:
```bash 
npm run za54ai-trade {alice_name}
```
## Dependencies

The project utilizes the following dependencies:

| Dependency         | Version  | Description                                                                 |
|--------------------|----------|-------------------------------------------------------------------------|
| `@solana/web3.js`          | ^1.98.0  | Interact with blockchain networks.	                             |
| `dotenv`             | ^16.4.7   | Load environment variables from a `.env` file.           |
| `firebase`   | ^11.1.0  | Firebase SDK for secure and scalable data storage.                          |
| `node-fetch`           | ^3.3.2  | Lightweight HTTP client for making API requests.                            |
| `openai`           | ^4.77.3  | Integration with OpenAI APIs for natural language queries.              |
| `bs58`          | ^6.0.0	  | Base58 encoding/decoding for blockchain addresses.	                             |
| `form-data`             | ^4.0.1   | Handle multipart/form-data requests.          |
| `punycode`   | ^2.3.1	  | Utility for converting Unicode strings.


## Dev Dependencies

The project utilizes the following development dependencies:

| Dependency         | Version  | Purpose                                                                 |
|--------------------|----------|-------------------------------------------------------------------------|
| `typescript`          | ^5.7.3  | Strongly-typed JavaScript for scalable and reliable code.	                                      |
| `ts-node`   | ^10.9.2  | Execute TypeScript code without transpiling it first.                          |
| `tsconfig-paths`           | ^4.2.0  | Resolve module paths in TypeScript projects for better structure.                            

## 🛠 Scripts Overview
#### The framework comes with several npm scripts for ease of use:

- `npm run build`: Transpile TypeScript to JavaScript.
- `npm run askza54ai`: Ask general questions to your ALICEs.
- `npm run deployza54ai`: Deploy a new ALICE to the blockchain.
- `npm run interactza54ai`: Interact with deployed ALICEs using queries.
- `npm run za54ai-trade`: Trade tokens on blockchain networks.

## 🔧 How It Works
- **Firebase Integration**: Provides secure storage and retrieval of ALICE-related data.
- **Bitquery Integration**: Fetches real-time and historical blockchain data for queries.
- **Command Parsing**: Processes user commands to route them to the appropriate functionality.
- **Customizable Framework**: Modify or extend the framework to suit your specific needs.

# USING api.za54.ai API

## Prerequisites

To use the API, ensure you have the following:

1. **API Access**: The API is publicly available at [api.za54.ai](https://api.za54.ai).
2. **API Client**: Use a tool like `curl`, Postman, or any HTTP client library in your preferred programming language.

---

## API Endpoints

### 1. Fetch ALICE Details
Retrieve metadata about an ALICE from the official ZA54ai Framework database.

**GET** `/api/alice/:name`

#### Request Example:
```bash
curl https://api.za54.ai/api/alice/Sabi
```
**Response Example:**
```bash
{
  "name": "Sabi",
  "description": "An intelligent entity designed to assist with tasks.",
  "createdAt": "2025-01-01T12:00:00Z"
}
```
#### 2. Interact with an ALICE (GET Method)
Send a message to an ALICE and receive an AI-generated response using query parameters.

**GET** `/api/alice/:name/interact?message=YourMessage`

**Request Example:**
```bash
curl "https://api.za54.ai/api/alice/Sabi/interact?message=Hello!"
```
**Response Example:**
```bash
{
  "alice": "Sabi",
  "reply": "Hello! How can I assist you today?"
}
```
#### 3. Interact with an ALICE (POST Method)
Send a message to an ALICE and receive an AI-generated response using a JSON payload.

**POST** `/api/alice/:name/interact`

**Request Example:**
```bash
curl -X POST "https://api.za54.ai/api/alice/Sabi/interact" \
-H "Content-Type: application/json" \
-d '{"message": "Hello, Sabi"}'
```
**Response Example:**
```bash
{
  "alice": "Sabi",
  "reply": "Hey, how can i help you?"
}
```
## Example Usage in Node.js
Here’s how you can interact with the API programmatically:
```bash
const fetch = require("node-fetch");

async function interactWithALICE(aliceName, message) {
  const response = await fetch(`https://api.za54.ai/api/alice/${aliceName}/interact`, {
    method: "POST",
    headers: { "Content-Type": "application/json" },
    body: JSON.stringify({ message }),
  });

  if (!response.ok) {
    console.error("Failed to interact with the ALICE:", response.statusText);
    return;
  }

  const data = await response.json();
  console.log("ALICE Reply:", data.reply);
}

interactWithALICE("Sabi", "Hello there!");
```

## Notes for api.za54.ai
- **No Local Setup Required**: This API is fully hosted and ready to use—no Firebase setup or service account keys needed.
- **ALICE Metadata**: All ALICE information is sourced directly from the official ZA54ai Framework database.

## 🤝 Contribution
We welcome contributions! To get started:

- Fork the repository.
- Create a new branch (feature/my-feature).
- Make your changes and commit them.
- Open a pull request.

---
