## xWBTC on BRC-20: The Decentralized & BTC-Pegged Wrapped BTC based on OP_CAT Covenant

**Powered by** [**100Layer**](https://100layer.io/)

**Time: Jun. 16th 2025**

**X:** [**https://x.com/100_Layer**](https://x.com/100_Layer)

xWBTC is a BRC-20 token issued on Bitcoin Layer 1. xWBTC is a completely decentralized, trustless Wrapped BTC based on OP_CAT Covenant. This protocol is used to describe how to make BTC more programmable so that BTC can be used in the BRC-20 protocol on Bitcoin Layer 1, in DeFi applications (AMM, Stablecoin, Lending, etc.) based on technologies such as EVM, OP_CAT Covenant, WASM, State Machine, etc. Similar to WETH's empowerment for ETH programmability on Ethereum Layer 1, xWBTC can introduce BTC into Smart Contracts on Bitcoin Layer 1. This protocol proposes an implementation method of BTC Wrapping and Unwrapping based on OP_CAT Covenant, that manages the BTC locked by users and the xWBTC locked by the issuer, without the need for any trusted third party to custody user assets, truly realizing the completely decentralized, trustless, non-custodial, censorship-resistant, and 1:1 BTC-pegged Wrapped BTC.

xWBTC is implemented in a completely decentralized way. Based on this protocol, the completely decentralized, 1:1 BTC-pegged Wrapped BTC can be implemented on the BRC-20 protocol on Bitcoin Layer 1. xWBTC does not need to make any changes or upgrades to the original meta-protocol: BRC-20, and the xWBTC token is a token that complies with the original meta-protocol standard: BRC-20. Any application that supports the original meta-protocol natively supports the xWBTC Token. At the same time, both Wrapping and Unwrapping of xWBTC have the great advantages: Bitcoin miner validated and uses smart contracts, specifically covenants, to manage BTC wrapping and unwrapping.

## 1. Principles

### 1.1 1:1 BTC-Pegged xWBTC

In this protocol, when the user wraps BTC, the BTC will be locked into the OP_CAT Covenant, and the Covenant will transfer the same amount of xWBTC to the user. Any user can unwrap xWBTC to the same amount of BTC at any time, and no one can interfere with the user's wrapping and unwrapping, like WETH (Wrapped ETH) does.

### 1.2 Completely Decentralized

The xWBTC is on Bitcoin Layer 1 and is implemented by the decentralized OP_CAT Covenant, that is also known as Bitcoin Smart Contract. xWBTC does not rely on off-chain indexers and is verified by the Bitcoin miner. No one, including the xWBTC issuer, can change the operating mechanism and algorithm of the on-chain OP_CAT Covenant.

### 1.3 Trustless

The wrapping and unwrapping of BTC and xWBTC are both implemented through the OP_CAT Covenant. The BTC locked by users and the xWBTC locked by issuer are also managed by the Covenant. No trusted third party is required to manage BTC and xWBTC, truly realizing the trustless management of BTC on Bitcoin Layer 1.

### 1.4 Non-Custody of User Assets

Users can lock BTC to unlock xWBTC managed by the Covenant. The locked BTC is managed by the OP_CAT Covenant instead of being managed by a third party. The locked BTC can only be unlocked when the user transfers the corresponding xWBTC token to the Covenant. No one can abuse the locked BTC and xWBTC managed by the OP_CAT Covenant.

### 1.5 Censorship-Resistant

All the operations of the xWBTC are completed on the OP_CAT Covenant and are atomic. No additional process (like signature) is required from the xWBTC issuer. After the user agrees to the transaction by signing, the subsequent operations are automatically completed by the Covenant and then verified by the Bitcoin miner. No one can change the behavior and results, and no one can censor the user.

### 1.6 Atomic Operations

The user's BTC wrapping and unwrapping operations are atomic, which means that the wrapping or unwrapping is completed in one transaction. There will be no situation where the Covenant receives the user's locked BTC but does not unlock the xWBTC to the user. Similarly, there will be no situation where the Covenant receives the user's locked xWBTC but does not unlock the BTC to the user.

## 2. Innovations

The xWBTC has 5 important innovations: Locker: Locking Contract, Wrap, Unwrap, Optimized Covenants by MAST and Oracle, which will be introduced in details below.

### 2.1 Locker: Locking Contract

The Locking Contract (locker) is an OP_CAT Covenant, and is the management smart contract of the locked BTC and xWBTC. When users wrap BTC, they lock BTC to the locker to unlock the same amount of xWBTC. Similarly, for the unwrapping, when users lock xWBTC to the locker, the locker will unlock the same amount of BTC to the user. Both processes are verified by Bitcoin miner, are completely decentralized and trustless, and cannot be controlled by anyone. Locker is the core implementation of the xWBTC.

### 2.2 Wrap: Lock BTC to Unlock xWBTC

In this protocol, the xWBTC is managed by the OP_CAT Covenant: Locking Contract (locker). Users can lock BTC to the Locking Contract (locker) to unlock the same amount of xWBTC token. This process is atomic and occurs in one transaction, that means the locking BTC and unlocking xWBTC can either succeed at the same time or fail at the same time. The Locking Contract (locker) is a Smart Contract based on OP_CAT Covenant, which is responsible for managing the BTC assets locked by users and the xWBTC assets locked by the issuer. The xWBTC tokens users received can participate in any DeFi application (AMM, Stablecoin, Lending, etc.) on Bitcoin Layer 1, that supports the BRC-20 protocol.

### 2.3 Unwrap: Lock xWBTC to Unlock BTC

In this protocol, the xWBTC holders can lock xWBTC to unlock the same amount of BTC. The entire process is controlled by the Smart Contract: Locking Contract (locker) based on OP_CAT Covenant, and no one can censor the user. Like the wrap process, this process is also atomic and occurs in one transaction, that means locking xWBTC and unlocking BTC can either succeed at the same time or fail at the same time.

### 2.4 Optimized Covenants by MAST

MAST (Merklized Abstract Syntax Trees) is a method of using a merkle tree to store the various user-selected conditions that must be fulfilled in order for the encumbered bitcoins to be spent. Using a merkle tree allows the spender to select which one of the conditions they’ll fulfill without having to reveal the details of other conditions to the block chain. Users of MAST who are able to keep unused conditions off of the block chain will enjoy lower fees, be able to create larger contracts than currently possible, will have improved privacy, and will improve the fungibility of their bitcoins.

By MAST, the locker contract is actually composed of 4 contracts: Wrap, Unwrap, Recover, and Merge/Split. Each operation actually only executes the logic of one contract, which can greatly save the transaction fees.

![image](https://github.com/user-attachments/assets/16c53efd-3fe5-4a99-abb5-e7394814e547)


### 2.5 Oracle

A blockchain oracle is a third-party service or agent that provides external data to a blockchain network. It is a bridge between the blockchain and the external world, enabling smart contracts to access, verify, and incorporate data from outside the blockchain. This allows smart contracts to execute based on real-world events and conditions, enhancing their utility and functionality.

Since the states (e.g. balance) of Bitcoin Layer 1 meta-protocols such as BRC-20 and Runes are stored in the indexer outside the Bitcoin blockchain, like Ethereum, the OP_CAT Covenant on the blockchain cannot know the states outside the blockchain. At this time, it is necessary to introduce the oracle mechanism, that provides the states outside the blockchain and ensures the correctness of the states through a decentralized mechanism. Just like many DeFi applications on Ethereum rely on Chainlink oracle, xWBTC uses oracle to verify whether xWBTC token exists in one UTXO. Oracle is an important infrastructure for DeFi projects. The CAT Protocol provides an implementation of Bitcoin Oracle: https://catprotocol.org/examples/oracle, based on which this protocol designs and implements the BTC Wrapping and Unwrapping.

![image](https://github.com/user-attachments/assets/dd3bd878-cda7-4b01-94bf-ce857f7fb880)
<div style="text-align: center;">
Bitcoin Oracle Designed by CAT Protocol
</div>

## 3. Operations

This chapter will describe the operations of xWBTC. In addition to the original operations introduced by the BRC-20 protocol, xWBTC implements 4 additional operations through OP_CAT Covenant: Wrap, Unwrap, Recover xWBTC, and Merge/Split BTC. These operations will be described in detail below.

### 3.1 Wrap: Lock BTC to Unlock xWBTC

In this protocol, BTC wrapping actually includes two operations: locking BTC and unlocking xWBTC token. These two operations are completed in one transaction, ensuring the atomicity of the two operations. These two operations are controlled by the Locking Contract (locker). The user’s BTC is locked in the Locking Contract (locker), that can only be unlocked to the user when the user unwraps BTC. At the same time, the xWBTC tokens can only be unlocked to user by locking user’s BTC UTXOs to the Locking Contract (locker). The wrapping transaction must follow the following rules to be valid:

- There is exactly one xWBTC token input from locker.
- The xWBTC amount must not be greater than the max value of int32.
- There is exactly one Oracle contract input.
- There is one or more BTC UTXO input from the user.
- The user who receives the xWBTC token must be the same user who locks BTC.
- There is exactly one output BTC to the locker, with the same amount as the locked xWBTC.

![image](https://github.com/user-attachments/assets/61ad20a4-7fb1-4f4d-a8f3-a9f3c0e42577)

### 3.2 Unwrap: Lock xWBTC to Unlock BTC

This protocol introduces a new BTC unlocking method: unwrap, that is exactly the opposite of the wrapping logic. Unwrap actually includes two operations: lock xWBTC token and unlock BTC. These two operations are completed in one transaction, ensuring the atomicity of them. These two operations are controlled by the Locking Contract (locker) too. The BTC locked in the locker will be unlocked to the user along with the user's xWBTC locking. The unwrapping transaction must follow the following rules to be valid:

- There is exactly one xWBTC token input from user.
- The xWBTC amount must not be greater than the max value of int32.
- There is exactly one Oracle contract input.
- There is one or more BTC UTXO input from the locker.
-  The user who inputs the xWBTC token must be the same user who receives the unlocked BTC.
- The xWBTC must be sent to the locker.
- There is one output BTC to the locker if there is any change, the value must be equal to (the total input locked BTC amount – the input xWBTC amount).
- There is exactly one output BTC to the user, with the same amount as the locked xWBTC.

![image](https://github.com/user-attachments/assets/d1b20b72-4043-4025-b543-a13551ad3171)

### 3.3 Recover xWBTC

In order to facilitate the management of xWBTC locked in the Locking Contract (locker), this protocol supports the recovering of xWBTC: transfer the transfer inscription of xWBTC to the locker itself. After the recovering, the xWBTC is still locked in the original locker. Recovering effectively prevents the situation where someone maliciously inscribes the transfer inscription to the locker to make the xWBTC unavailable by the BRC-20 protocol. The recover transaction must follow the following rules to be valid:

- There is exactly one xWBTC token input from locker, at input index 0.
- There is exactly one xWBTC token output to the locker, at output index 0.

![image](https://github.com/user-attachments/assets/3d4c7fc2-beab-4c98-8f0b-52618568a583)

### 3.4 Merge/Split BTC

In order to facilitate the management of BTC UTXO locked in the Locking Contract (locker), this protocol supports the merge/split of BTC UTXO, which can manage the BTC locked by the Covenant. The locked BTC UTXOs can be merged to bigger UTXOs or split to small UTXOs by the locker. After the merge/split, the BTC is still locked in the original locker. The merge/split transaction must follow the following rules to be valid:

- There is no xWBTC token input.
- There is exactly one Oracle contract input.
- There is one or more BTC UTXO input from the locker.
- There is one or more BTC UTXO output to the locker.
- The total amount of the input locked BTC must be equal to the total locked BTC of the output.
- The total amount of the input locked BTC must not be greater than the max value of int32.

![image](https://github.com/user-attachments/assets/08ed049a-95fe-4f8e-b580-b93074868a37)

## 4. Anti-Attacks

The design of xWBTC can prevent arbitrary malicious attacks to ensure the security of the BTC locked by users and the xWBTC locked by the issuer, the security of the entire wrapping and unwrapping process, and the 1:1 pegging to BTC of xWBTC.

### 4.1 Preventing Unlock the Locked xWBTC Arbitrarily

The xWBTC unlocking is controlled by the Locking Contract (locker). The contract verifies that the xWBTC token is only allowed to be unlocked to the user when the user locks the same amount of BTC to the Locking Contract (locker). All verifications are completed in the OP_CAT Covenant: locker. No one can unlock xWBTC arbitrarily under any circumstances.

### 4.2 Preventing Unlock the Locked BTC Arbitrarily

The BTC unlocking is controlled by the Locking Contract (locker). The contract verifies that the BTC is only allowed to be unlocked to the user when the user locks the same amount of xWBTC token to the Locking Contract (locker). All verifications are completed in the OP_CAT Covenant: locker. No one can unlock BTC arbitrarily under any circumstances.

### 4.3 Atomicity to Prevent Attacks from xWBTC Issuer

Another attack method is to censor users by the xWBTC issuer. This protocol is completely based on the OP_CAT Covenant. The user's wrap and unwrap operations are atomic, that is, the user's BTC locking and xWBTC unlocking are either successful at the same time or fail at the same time; the user's xWBTC locking and BTC unlocking are also either successful at the same time or fail at the same time, avoiding the intermediate state: a single operation success. In addition, the processing logic of the OP_CAT Covenant only requires the user's signature, and does not require the additional logic from the xWBTC issuer such as signature.

### 4.4 Preventing Malicious xWBTC Locking

Another attack method is to maliciously lock the locker's xWBTC, that is, generate a xWBTC inscription to the locker to attack the protocol. In extreme cases, all xWBTC tokens can be locked, cannot be used by the wrapping, causing the system unable to operate. Therefore, this protocol supports Recover xWBTC: transferring the xWBTC inscription to the locker itself to deal with this possible risk.

### 4.5 Preventing Dust Attack

Another possible attack is dust attack, that is generating a large number of small amounts BTC UTXOs to the locker to carry out dust attacks to the protocol. Although it will not affect the user's assets and functions, it may still affect the user experience when wrapping and unwrapping. Therefore, this protocol supports Merge/Split BTC UTXOs for the locker to deal with this possible risk.

## 5. References

[1] brc-20, https://domo-2.gitbook.io/brc-20-experiment

[2] BRC2.0: The Programmable Module, https://github.com/bestinslot-xyz/brc20-prog-module-proposal

[3] Best in Slot: Interact with BRC2.0 Contracts, https://signet.bestinslot.xyz/brc2.0/interact

[4] Covenant Attested Token (CAT) Protocol, https://catprotocol.org/

[5] Oracle on Bitcoin by OP_CAT, https://catprotocol.org/examples/oracle

[6] WBTC Protocol by 100Layer: A Decentralized & Programmable Wrapped BTC based on OP_CAT Covenant, https://github.com/100Layer-Labs/WBTC/blob/main/WBTC_Protocol.md

[7] MAST of Taproot upgrade, https://bitcoinops.org/en/topics/mast/

[8] OP_CAT in Tapscript, https://github.com/bitcoin/bips/blob/master/bip-0347.mediawiki

[9] What Is Wrapped Ethereum (WETH), https://coinmarketcap.com/academy/article/what-is-wrapped-ethereum-weth

[10] Bitcoin: A Peer-to-Peer Electronic Cash System, https://bitcoin.org/bitcoin.pdf

[11] Ethereum: A Next-Generation Smart Contract and Decentralized Application Platform, [https://ethereum.org/en/whiteprotocol/](https://ethereum.org/en/whitepaper/)

[12] sCrypt: The full stack Web3 development platform for Bitcoin Compatible Blockchains, https://docs.scrypt.io/

[13] 100Layer: A Liquidity Protocol ond Bitcoin Layer 1 and Fractal by OP_CAT, https://100layer.io/
