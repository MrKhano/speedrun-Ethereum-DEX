# 🚀 SpeedRun Ethereum – Challenge 5: Build a DEX

A complete implementation of a **Decentralized Exchange (DEX)** using a constant-product Automated Market Maker (AMM).  
Contracts deployed on **Sepolia**, with a live frontend on **Vercel**.

## 🌐 Live Deployment

| Component | Address / URL |
|----------|----------------|
| **Balloons Token (BAL)** | `0xf5c42f6C86B48Ffea90D9Ab416Cc6d06f982682c` |
| **DEX Contract** | `0xF3DF3B2Eda66937DC184730f0173Df57c8a98080` |
| **Etherscan** | https://sepolia.etherscan.io/address/0xF3DF3B2Eda66937DC184730f0173Df57c8a98080 |
| **Frontend (Vercel)** | https://ethereum-psdjidlxp-renauds-projects-24d51691.vercel.app/ |

**Contract Creator = Me** ✔️  
(Required for Speedrun validation)

## 📦 Project Structure

```bash
packages/
├── hardhat/
│   ├── contracts/
│   │   ├── Balloons.sol
│   │   └── DEX.sol
│   ├── scripts/
│   │   ├── importAccount.ts
│   │   ├── listAccount.ts
│   │   ├── generateAccount.ts
│   │   ├── generateTsAbis.ts
│   │   ├── revealPK.ts
│   │   └── runHardhatDeployWithPK.ts   ← Deployment script
│   ├── hardhat.config.ts
│   └── typechain-types/
│
└── nextjs/
    ├── app/
    ├── components/
    ├── public/
    ├── scaffold.config.ts
    └── contracts/
        └── deployedContracts.ts        ← Auto-updated after deploy
```

## 🧠 Smart Contracts

### **Balloons.sol**
- ERC20 token used in the AMM pair  
- 1000 BAL minted to deployer  
- Based on OpenZeppelin ERC20  

### **DEX.sol**
Implements:

- `init()` – initialize liquidity  
- `price()` – constant-product pricing  
- `ethToToken()` – swap ETH → BAL  
- `tokenToEth()` – swap BAL → ETH  
- `deposit()` / `withdraw()` – liquidity mgmt  
- LP token tracking  
- 0.3% trading fee  


## 🚀 Deployment (Sepolia)

### 1️⃣ Import your wallet

```bash
cd packages/hardhat
npx ts-node scripts/importAccount.ts
```

Verify:

```bash
npx ts-node scripts/listAccount.ts
```

### 2️⃣ Configure `.env`

```
SEPOLIA_RPC_URL="https://sepolia.infura.io/v3/YOUR_KEY"
PRIVATE_KEY="0xYOUR_PRIVATE_KEY"
```

### 3️⃣ Deploy contracts

```bash
npx ts-node scripts/runHardhatDeployWithPK.ts --network sepolia
```

This updates:

```
packages/nextjs/contracts/deployedContracts.ts
```

### 4️⃣ Deploy frontend

```bash
cd packages/nextjs
vercel --prod
```

## 💡 How the AMM Works (x·y = k)

- **x** = ETH reserve  
- **y** = BAL reserve  
- **k** = constant  
- Swaps adjust reserves automatically  
- Larger trades → more slippage  
- Fee: **0.3%**  

Uses the classic **Uniswap V1** invariant.

## 🧪 Testing

```bash
cd packages/hardhat
npx hardhat test
```

## 🧭 Using the DEX

1. Open the Vercel app  
2. Connect MetaMask (Sepolia)  
3. Swap ETH ↔ BAL  
4. Provide liquidity  
5. Withdraw liquidity  
6. View LP positions  

## 📝 SpeedRun Submission

- ✔️ Contracts deployed on Sepolia  
- ✔️ Contract creator = Me  
- ✔️ Frontend deployed  
- ✔️ Swaps working  
- ✔️ LP mint/withdraw working  
- ✔️ All checkpoints validated  

**Submit this Testnet Contract URL:**  
https://sepolia.etherscan.io/address/0xF3DF3B2Eda66937DC184730f0173Df57c8a98080

## 📄 License

MIT License  

---
