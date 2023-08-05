# EOS Cryptography Proposal 2 b

- **Project Name:** EOS Cryptography Proposal 2 b
- **Team Name:** ZeroPass
- **EOS Payment Address:** portxxxxxxxx
- **[Level](https://github.com/eosnetworkfoundation/grant-framework#grant-levels):** 3
- **Pomelo Grant(s)**  
https://pomelo.io/grants/ygc2lp2oe  
https://pomelo.io/grants/bot4eden
- **Project is Open-Source:** Yes
- **Project was part of Token sale:** No
- **Repository where Project resides:** https://github.com/ZeroPass/ack


## Contact

- **Contact Name:** Luka Percic
- **Contact Email:** zeropass@pm.me
- **Website:** [port.link](https://port.link/)

## Project Overview


### Overview
We are proposing to add different signature verification algorithms for EOS. There are different ways to achieve this, but doing research and implementation of many libraries on [eos-cryptography-proposal](https://github.com/lukapercic/grant-framework/blob/main/applications/eos-cryptography-proposal.md) lands us on optimizing previous SDK library for smart contracts by using another coordinate system, such as the Jacobian system or the mixed Jacobian/Chudnovsky coordinate system. This will allow ACK library to squeze more preformance for existing curves, and those delived in this grant. P-256 is hitting 7ms in OC (optimized compilation), and for brainpool curves we fully expect over 10ms (especially the 512 bit ones).. 


### Project Details

We implemented a [Antelope Cryptography Kits](https://github.com/ZeroPass/ack) the fastest RSA implementation for EOSIO. It can ran RSA4096 verificaitons on the mainnet today. We also have a working [PoC Port smart contract](https://github.com/ZeroPass/eosio-port). The smart contract can already do passive and active passport attestation for passports based on RSA PKCS 1.5 PKI. 

The main goal of the previous grant was to research which other libraries we can dissects and use their parts to rebuild different ECC algos in universal way. We now have the specialization needed to deliver further EC optimization for modular arithmetic operations which will help us run existing curves more efficiently (P-256 is currently hitting 7ms), and curves implemented in this grant Nist (P-384, P-512) and especially heavier brainpool (brainpoolP256r1, brainpoolP320r1, brainpoolP384r1, brainpoolP512r1) in under 10ms with OC (Optimized Compilation) flag enabled.

### Ecosystem Fit

Port can be used as a better version of (anonymous) identity on the blockchain. It's open-source and open-access nature allows any dapp to plug into it, and profit from the infrastructure it provides. It fixes the issue with DIDs, where self-sovereign identity in the practice always gets implemented as one KYC provider signing the attestations. Here the passport proves authenticity itself, cutting the middle man and cutting friction associated with it. I.e.: removing the costs and needed trust (don't be evil, versus can't be evil). Adding different signature verification algorithms can serve as crypto primitive for Antelope, and upon which our contract can be built on. To expand the use-cases we are mainly focusing on: making the Port a native way for EOS to solve Sybil protection, Identity, and multiple levels of verifications.

Right now, there are projects such as Pomelo and EOS Support integrating Port to help prevent Sybil attacks for their platforms (we would like to move it fully on-chain later). These signature verification algorithms will also benefit Randall Roland’s (CEO EOS Support) proposal that seeks to improve the user onboarding process of the RespectOS software. If successful, it might be the basis (or part of) the identity of the future EOS based DAOs.  We have been contacted by different NFT projects looking to do wide NFT drops, without the claimed abuse they detect right now. There are nice humanitarian applications, for instance, somebody can start an easy project to provide UBI-style donations to people with passports and IDs from affected countries. We are also defining new concept of Escape Tokens, that allows governance and distribution tokens to escape the main liquidity pair, and when thriving, its value overflow to Port identities in (UBI style). 

In short; it a real ID/Sybil building block that will enable many projects to plug and play. 

## Team

### Team members

- Luka Percic
- Crt Vavros
- Nejc Skerjanc

### Legal Structure
- **Registered Legal Entity:** Žerjal IT, d.o.o.
- **Registered Address:** Brje pri Komnu 40, 6223 Komen, Slovenia

### Team Experience

ZeroPass is a team of 3 from Slovenia (EU) with product/developers/cryptography skills.
Our most notable accomplishments in EOS community are:

- High severity [bug discovery in EOSIO node](https://b1.com/press/eosio-ram-resource-exploit-patch/) and disclosed through B1 hacker one bounty.
- EOS smart contract for BPs rotation.
- EOS smart contract for RAM resource market (RAM token).
- Providing bug fixes and patches for EOSIO CDT and EOSIO node software.
- 3rd place with [ROW project](https://github.com/ZeroPass/row.contract) at B1 hackathon / Google Cloud Platform, for proving WebAuthn to be fully done on-chain.
- [ack](https://github.com/ZeroPass/ack) - ECC primitives and ECDSA verification algorithms, RSA & Keccak hash algorithms cryptography library for Antelope smart contract.

### Team Code Repos

- https://github.com/ZeroPass
- https://github.com/ZeroPass/ack

 ### Team Members GitHub Accounts

- https://github.com/smlu
- https://github.com/nejc-skerjanc
- https://github.com/lukapercic

### Team LinkedIn Profiles

- https://www.linkedin.com/in/nejcskerjanc/
- https://www.linkedin.com/in/crt-vavros/
- https://www.linkedin.com/in/lukapercic/

## Development Status

**RSA PoC**
We painstakingly built, optimized, tested and deployed on the testnet to make it the fastest wasm RSA implementation in eosio. For example, it can verify RSA 4096 bit keys consistently under 10ms (3ms on average, much faster for the more standard  RSA 2048 bit).
- https://github.com/ZeroPass/ack


Our team built and deployed Port itself (server solution) that acts as our beta version for what we are trying to move on chain. In addition, we already experimented and built Port PoC smart contract for passport attestation on-chain (RSA PKCS 1.5 PKI only). 

We can also attach research from our documentation (which is not completly up to date). It is presented in the [In-depth section](https://github.com/ZeroPass/Port-documentation-and-tools#in-depth).

## Development Roadmap

- **Total Estimated Duration:** 3 months
- **Full-Time Equivalent (FTE):**  12 FTE months
- **Total Costs:** $55.000

### Milestone 1 - Optimization
- **Estimated duration:** 3 month
- **FTE:** 12 FTE months
- **Costs:** $55,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | MIT |
| 0b. | Documentation | Documentation and step by step guide will be updated in [README.md](https://github.com/ZeroPass/ack/blob/master/README.md).  | 
| 0c. | Testing Guide | [In the guide](https://github.com/ZeroPass/eosio.ck/blob/master/README.md#algorithm-testing=), we will describe how to run those tests. |
| 0d. | Running it | We will re-deploy on the [Jungle 3 and CryptoKylin testnets](https://github.com/ZeroPass/ack/blob/master/README.md#testnet).|
| 1. | Antelope SDK library | Optimized EC arithmetic by using another coordinate system, such as the Jacobian coordinate system or the mixed Jacobian/Chudnovsky system.
| 2. | Antelope SDK library | Sha-384 |

Preliminary tests of using Jacobian coordinate system suggests a ~2-fold increase in speed using such a system.

### Milestone 2 - Adding Curves
- **Estimated duration:** 2 month
- **FTE:** 6 FTE months
- **Costs:** $36,000 USD

| Number | Deliverable | Specification |
| -----: | ----------- | ------------- |
| 0a. | License | MIT |
| 0b. | Documentation | Documentation and step by step guide will be updated in [README.md](https://github.com/ZeroPass/ack/blob/master/README.md).  | 
| 0c. | Testing Guide | [In the guide](https://github.com/ZeroPass/eosio.ck/blob/master/README.md#algorithm-testing=), we will describe how to run those tests. |
| 0d. | Running it | We will re-deploy on the [Jungle 3 and CryptoKylin testnets](https://github.com/ZeroPass/ack/blob/master/README.md#testnet). |
| 1. | Antelope SDK library | Implementation of P-384, P-512 NIST curves |
| 2. | Antelope SDK library | Implementation of brainpoolP256r1, brainpoolP320r1, brainpoolP384r1, brainpoolP512r1 Brainpool curves |
| 3. | Antelope SDK library | Implementing ECDSA key recovery from signature |



## Future Plans
**Expected Part 3 of the proposal**  
- Implementation of EdDSA,

**Pending additional research;**  
Possibility of implementation for ECC curve alt_bn128 curve which is widely available on other major blockchain platforms like EVM and Polkadot.

We are planning to rebuild [Port](https://port.link/) on-chain, and this proposal provides the crypto primitives needed to begin the process.
Our RSA PKCS 1.5 implementation is also already used in our another project: [ROW](https://row.link/), which hopefully will one day become a full-fledged WebAuthn signer.
In the more distant future we are also planning to build dapp on top these projects, using both on-chain Port and ROW projects as building blocks.

## Additional Information

**How did you hear about the Grants Program?** 
Telegram

We also invite all to donate on Pomelo for our current [implementation of Port](https://pomelo.io/grants/ygc2lp2oe), and try increasing your Pomelo [Trust Bonus](https://pomelo.io/profile?tab=trust).
