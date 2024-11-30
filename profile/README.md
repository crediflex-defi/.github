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

---

## What is Crediflex?

Crediflex is an undercollateralized lending protocol that leverages **AVS (Actively Validated Service)** with **EigenLayer middleware** to verify credit scoring and **zkTLS** to fetch proofed data for calculating C Score parameters. 

- The **C Score** dynamically determines Loan-to-Value (LTV) ratios, enabling users to borrow more than their collateral based on their on-chain activities.
- For the hackathon, users deposit **mock WETH** as collateral and borrow **mock USDe** as the asset, with borrowing limits calculated using four key parameters:
  1. **Wallet Age**: How long the wallet has been active.
  2. **Token Holding Diversity**: Number of unique tokens worth more than $1 held.
  3. **Total Transactions**: How many transactions the wallet has performed.
  4. **Multi-Chain Activities**: Number of distinct blockchains the wallet has interacted with.

This implementation showcases **secure data handling**, **efficient scoring**, and practical lending mechanics for DeFi.

---

## Deployment

Crediflex is deployed on the **Arbitrum-Sepolia testnet**, while the credit scoring parameters are derived from **Arbitrum Mainnet activity**. This approach ensures realistic data is used for parameter calculation while maintaining a test environment for rapid development and validation.

---

## Links

- **Demo Application**: [Loom Video](https://www.loom.com/share/f2f07bec1d7f4a16a265d5c2e15b4fd5?sid=6b59d2d7-8cec-4437-b5a9-5837ee9344db)
- **Presentation**: [Google Slides](https://docs.google.com/presentation/d/1jzdRC5VvygoHkkKyZcC22kcvkAqC7YxsAfnADTBuLmU/edit#slide=id.g1f1ce5643d3_0_0)
- **Web App**: [Crediflex App](https://crediflex.vercel.app/)

---

## Credit Scoring (C Score)

The **C Score** is a unique metric that evaluates a user’s on-chain activity using specific parameters. While there are plans to integrate many parameters in the future, the hackathon version of Crediflex uses the four parameters mentioned above.

---

### AVS and zkTLS in Action

1. **AVS (Actively Validated Service)**:
   - AVS is a system for managing credit scoring requests.
   - It uses **EigenLayer middleware** to verify credit scoring tasks securely.
   - Ensures trust and validation for off-chain processes by enabling on-chain verification of fetched data and calculated scores.

2. **zkTLS**:
   - zkTLS ensures that data fetched from HTTPS endpoints is proofed and verifiable, preventing tampering during the data-fetching process.
   - This technology adds an extra layer of trust to the **C Score** generation workflow by ensuring accurate and secure data for credit scoring.

---

## Workflow

### Credit Scoring Workflow
1. The user requests a **C Score** by interacting with the **AVS contract**.
2. The AVS contract creates a task for credit scoring.
3. An **Operator** monitors and picks up the task.
4. The Operator fetches remote data over HTTPS endpoints (secured with **zkTLS**) to ensure proof of correct data fetching and integrity.
5. The fetched data is processed to calculate the C Score based on the defined parameters.
6. The calculated C Score is signed, verified using EigenLayer middleware, and sent back to the AVS contract.

**Note**: The C Score remains valid for **120 days** (approximately 4 months). After this period, users must request a new C Score to ensure it reflects the latest on-chain activity.

---

### Lending Workflow
1. Users deposit collateral (e.g., **mock WETH**) into the protocol.
2. Users can borrow assets (e.g., **mock USDe**) based on the dynamic LTV determined by their C Score.

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

## Technology Stack

- **AVS (Actively Validated Service)**: Manages credit scoring requests and verifies responses using middleware for task validation.
- **zkTLS**: Ensures data fetched from HTTPS endpoints is verifiable and tamper-proof.
- **EigenLayer Middleware**: Provides secure and trustless task verification for C Score calculations.
- **Mock Contracts**: Simulated **USDe** and **WETH** contracts for testing borrowing and collateral features.
- **Arbitrum-Sepolia Testnet**: Deployment environment for contracts and protocol validation.

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
