# Crediflex

**Crediflex** is an **Undercollateralized Lending Protocol** that introduces a novel approach to borrowing assets in decentralized finance (DeFi). By leveraging on-chain activity-based credit scoring, it enables users to borrow more assets than they collateralize, provided certain requirements are met.

---

## Problem Statement

Traditional lending protocols in DeFi face a significant limitation:
- **Overcollateralization Requirement**: Users must deposit more collateral than the amount they intend to borrow.

This restrictive model limits capital efficiency and discourages broader adoption of lending platforms.

---

## Proposed Solution

Crediflex addresses this issue with an **undercollateralized approach**, allowing users to borrow assets with collateral worth less than the borrowed amount. The key innovation lies in the integration of **on-chain credit scoring** to determine dynamic loan-to-value (LTV) ratios. 

- **Dynamic LTV Calculation**: Crediflex calculates LTV based on a user’s credit score (C Score), reflecting their on-chain activities. 
- **C Score-Driven Lending**: A higher C Score enables users to borrow more assets relative to their collateral.

---

## Credit Scoring (C Score)

The **C Score** is a unique metric that evaluates a user’s on-chain activity using specific parameters. While there are plans to integrate many parameters in the future, the hackathon version of Crediflex uses the following **four parameters**:

1. **Wallet Age**: How long the wallet has been active.
2. **Token Holding Diversity**: Number of unique tokens worth more than $1 held by the wallet.
3. **Total Transactions**: Total count of transactions performed by the wallet.
4. **Multi-Chain Activities**: Number of distinct blockchains the wallet has interacted with.

### Why These Parameters?
These parameters are chosen because:
- **Wallet Age**: Reflects the longevity and commitment of the user in the blockchain ecosystem.
- **Token Holding Diversity**: Indicates the user’s financial behavior and diversification.
- **Total Transactions**: Demonstrates the user’s engagement and activity level on the blockchain.
- **Multi-Chain Activities**: Shows the user’s participation across different blockchain ecosystems, reflecting versatility.

---

## Workflow

### Credit Scoring Workflow
1. The user requests a **C Score** by interacting with the **AVS contract**.
2. The AVS contract creates a task for credit scoring.
3. An **Operator** monitors and picks up the task.
4. The Operator fetches remote data over HTTPS endpoints (secured with zkTLS), providing verifiable proof of execution.
5. The fetched data is processed to calculate the C Score based on the defined parameters.
6. The calculated C Score is signed, verified, and sent back to the AVS contract.

**Note**: The C Score remains valid for **120 days** (approximately 4 months). After this period, users must request a new C Score to ensure it reflects the latest on-chain activity.

---

### Lending Workflow
1. Users deposit collateral (e.g., **WETH**) into the protocol.
2. Users can borrow assets (e.g., **USDe**) based on the dynamic LTV determined by their C Score.

---

## Smart Contracts

- **Main Contract**: [0xC4EC8E64157Ff9B5140966e6764F8B55319Ad08B](https://sepolia.arbiscan.io/address/0xC4EC8E64157Ff9B5140966e6764F8B55319Ad08B)
- **AVS Contract**: [0xc4327ad867e6e9a938e03815ccdd4198cce1023c](https://sepolia.arbiscan.io/address/0xc4327ad867e6e9a938e03815ccdd4198cce1023c)
- **Mocks**:
  - **usdeUsdDataFeed**: [0x27D0Dd86F00b59aD528f1D9B699847A588fbA2C7](https://sepolia.arbiscan.io/address/0x27D0Dd86F00b59aD528f1D9B699847A588fbA2C7)
  - **wethUsdDataFeed**: [0x122e4C08f927AD85534Fc19FD5f3BC607b00C731](https://sepolia.arbiscan.io/address/0x122e4C08f927AD85534Fc19FD5f3BC607b00C731)
  - **usde**: [0x6AcaCCDacE944619678054Fe0eA03502ed557651](https://sepolia.arbiscan.io/address/0x6AcaCCDacE944619678054Fe0eA03502ed557651)
  - **weth**: [0x80207B9bacc73dadAc1C8A03C6a7128350DF5c9E](https://sepolia.arbiscan.io/address/0x80207B9bacc73dadAc1C8A03C6a7128350DF5c9E)

---

## Deployment

### Web Application
Access the Crediflex web interface: [https://crediflex.vercel.app/](https://crediflex.vercel.app/)

---

## Future Plans

1. **KYC Integration**:
   - Handle users with multiple wallet addresses to prevent sybil attacks.
2. **Enhanced Credit Scoring**:
   - Add more parameters, such as:
     - Interaction with DeFi protocols.
     - Loan repayment history.
     - Liquidation history.
3. **Improved Calculation**:
   - Optimize algorithms for better scoring accuracy.
4. **Expand Ecosystem**:
   - Support additional assets and chains for lending and borrowing.
5. **Automated Monitoring**:
   - Implement mechanisms to track and update C Scores in real time.

---

## License
MIT License

---

For more information, feel free to explore the **contracts**, visit the **web app**, or contact the team!
