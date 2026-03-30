DNIT ETHIOPIA - Decentralized National Identity and Tax Collection System
Project Overview
DNIT Ethiopia is a blockchain-based infrastructure for the Federal Democratic Republic of Ethiopia that manages digital identities and automates tax collection using smart contracts deployed on the Sepolia Testnet. The system integrates Ethiopia's Fayda National Digital ID system to provide a complete solution for identity verification and tax compliance.

System Architecture
The platform consists of two main smart contracts working together:

NationalIdentity Contract
Manages citizen registration and verification using Ethiopia's 12-digit Fayda ID. Stores only hashed values for privacy while maintaining verification status through a two-step approval process.

StaticTaxHandler Contract
Handles all tax collection operations including progressive tax calculations based on income brackets of 5 percent, 15 percent, and 30 percent. Implements role-based access control and treasury management.

Deployed Contracts
NationalIdentity
0xbB7d162D2445e3e61d232a4f46b8a1Da6a2698E

StaticTaxHandler
0x32dc886F48d02a45D84800DF0b25ACed1636166

Both contracts are deployed and verified on the Sepolia Testnet.

Features by Role
Citizen Portal
Citizens can register using their 12-digit Fayda ID and full name. The system stores a secure hash of the ID on-chain while maintaining privacy. Once verified, citizens can calculate progressive taxes based on their annual income and make payments directly to the national treasury. Real-time balance checking ensures users have sufficient funds before attempting payment.

Government Admin Dashboard
Administrators can view all registered citizens and verify identities. The verification process requires that citizens first pass Fayda verification before admin approval. The dashboard displays total national tax revenue collected and provides real-time analytics on system usage.

Tax Collector Portal
Tax collectors can search any wallet address to view citizen profiles, tax history, and compliance status. The system generates digital compliance certificates that are cryptographically verifiable on-chain for business licensing and government tenders.

Transparency Explorer
Any user can view national revenue allocation charts showing distribution across education, health, infrastructure, and administration. A live activity feed displays recent tax payments and registrations in real-time.

Employer Portal
Employers can register their businesses, onboard employees with their wallet addresses, and submit bulk tax payments for their entire payroll in a single transaction. The system automatically calculates progressive taxes for each employee based on their salary.

Technology Stack
Smart Contracts
Solidity 0.8.24 with OpenZeppelin libraries for access control and security features including reentrancy protection and pause functionality.

Frontend
React with Vite for fast development, Tailwind CSS for responsive design, and Ethers.js v6 for blockchain interaction. Recharts provides data visualization for analytics dashboards.

Blockchain Network
Sepolia Testnet using public RPC endpoints for deployment and testing.

Verification Process
The system implements a two-step verification pipeline that aligns with Ethiopia's actual government infrastructure.

Fayda Verification
A designated verifier with the FAYDA_VERIFIER_ROLE confirms that the citizen's 12-digit Fayda ID matches their identity. This step simulates integration with Ethiopia's official eSignet API.

Government Admin Verification
After Fayda verification is complete, a government administrator with the VERIFIER_ROLE approves the citizen for tax participation. This separation of duties ensures proper oversight and security.

Only citizens who complete both verification steps can file and pay taxes through the system.

Getting Started
Prerequisites
MetaMask browser extension installed and configured for Sepolia Testnet. Sepolia ETH for gas fees which can be obtained from faucets.

Installation
Clone the repository and install dependencies using npm install. Configure environment variables by copying the example file and adding your private key for deployment.

Running Locally
Start the development server with npm run dev and connect MetaMask to Sepolia Testnet. The application will automatically detect your network and configure the contracts.

Testing Workflow
To test the complete system, follow these steps with a fresh wallet.

First, register as a citizen by connecting your wallet and entering your full name along with a 12-digit Fayda ID. The system will show registration pending.

Next, using the deployer wallet that has admin privileges, grant yourself the FAYDA_VERIFIER_ROLE and verify the citizen's Fayda ID using the same 12-digit number provided during registration.

Then, as the government administrator, approve the citizen for tax payment. The citizen can now pay taxes.

Finally, the citizen can calculate tax based on income and make payment. The transaction appears in the transparency explorer and updates treasury balances in real-time.

Security Considerations
All sensitive data including Fayda IDs are stored as keccak256 hashes on-chain. Raw identifiers never appear in the blockchain. Role-based access control ensures that only authorized accounts can perform sensitive operations like verification and tax collection. Reentrancy guards protect against recursive attacks during fund transfers.

Future Development
Integration with Ethiopia's official eSignet API for real-time Fayda verification is planned once government APIs become publicly available. Mainnet deployment will follow after comprehensive security audits and pilot testing with government stakeholders. Additional features include mobile application development and multi-language support for Amharic and English.

Support
For technical issues or deployment questions, refer to the smart contract documentation in the contracts directory or review the frontend components in the src folder. Contract addresses can be verified on Sepolia Etherscan for additional transparency.

License
This project is developed for demonstration and pilot purposes as part of Ethiopia's Digital Transformation initiative.
