# ⚡ Quick Guide: Deploy a Smart Contract to Arc Testnet 

No VPS needed you can run this command with your local using WSL

---

## 🧱 1. Set Up Your Development Environment

### Install Dependencies
#### Update
```bash
sudo apt update && sudo apt install -y 
```
#### Update System
```bash
sudo apt install curl git make build-essential pkg-config libssl-dev libclang-dev -y
```

### Install Foundry

```bash
curl -L https://foundry.paradigm.xyz | bash
```

#### Reload Shell
```bash
source ~/.bashrc
```

#### Run Foundry
```bash
foundryup
```

### Initialize a New Project
```bash
forge init hello-arc && cd hello-arc
```

## ⚙️ 2. Configure Foundry for Arc Testnet
### Create .env
```bash
nano .env
```

add this to .env
```bash
ARC_TESTNET_RPC_URL="https://rpc.testnet.arc.network"
```
Save .env with CTRL + X, then prees Y then Enter

load .env
```bash
source .env
```

## 💡 3. Create the Smart Contract

Then create src/HelloArchitect.sol
```bash
nano src/HelloArchitect.sol
```

then paste : 
```bash
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.30;

contract HelloArchitect {
    string private greeting = "Hello Architect!";
    event GreetingChanged(string newGreeting);

    function setGreeting(string memory newGreeting) public {
        greeting = newGreeting;
        emit GreetingChanged(newGreeting);
    }

    function getGreeting() public view returns (string memory) {
        return greeting;
    }
}
```

load
```bash
source .env
```

## 🧪 4. Test and Build the Contract
Run Tests
```bash
forge test
```
Compile
```bash
forge build
```

## 🚀 5. Deploy to Arc Testnet
### Generate a Wallet
cast wallet new
```bash
Add your private key to .env:
```

Add your private key to .env:
```bash
nano .env
```
and add to .env
```bash
PRIVATE_KEY="0x<yourprivatekey>"
```
change <yourprivatekey> with your evm private key

load .env
```bash
source .env
```

### Fund Your Wallet
Visit https://faucet.circle.com, select Arc Testnet, paste your wallet address, and request testnet USDC.

### Deploy the Contract
```bash
forge create src/HelloArchitect.sol:HelloArchitect \
  --rpc-url $ARC_TESTNET_RPC_URL \
  --private-key $PRIVATE_KEY \
  --broadcast
```

#### After successfull deployed Smart Contract
<img src="https://drive.google.com/uc?export=view&id=1Lh9ssQX7vegCbW5f37eFb1GRJhBaD-s1" width="600" />

Save your deployed address in .env
```bash
nano .env
```
and add to .env
```bash
HELLOARCHITECT_ADDRESS="<smart-contract>"
```
change <smart-contract> with your smart contract address

load .env
```bash
source .env
```

## 💬 6. Interact with Your Deployed Contract
### Call a Function
```bash
cast call $HELLOARCHITECT_ADDRESS "getGreeting()(string)" \
  --rpc-url $ARC_TESTNET_RPC_URL
```

### Check Your Address on Explorer ###

Check on https://testnet.arcscan.app/?_gl=1*1crz3rj*_gcl_au*MjEwNjY5NjM3MC4xNzYxNjYyNTY2*_ga*ODEwODgzNTc1LjE3NjE2NjI1NTg.*_ga_TFHGH9W48Q*czE3NjE4MDEwMDckbzQkZzEkdDE3NjE4MDE2NDEkajU4JGwwJGgyMDkxMjYxNjU2

<img src="https://drive.google.com/uc?export=view&id=17fffSM_7YIitQH5Pm9lyFh_EXT18gm4N" width="800" />

## ✅ Final Result
- Your HelloArchitect contract is live on Arc Testnet
- You can read and update the greeting variable
- You’re now ready to build more complex contracts on Arc 🚀

```bash
✅ **Instructions:**  
Copy everything between the triple backticks (```markdown ... ```) and paste it directly into your GitHub `README.md`.  
It will render **exactly** with all emojis, headings, and syntax highlighting like a professional guide.  

Would you like me to now add a **header section** (project title, logo, badges for “Built with Foundry” and “Deployed on Arc Testnet”) at the top?  
That would make it look like official documentation.
```

