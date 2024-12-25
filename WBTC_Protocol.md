## WBTC Protocol: A Decentralized & Programmable Wrapped BTC based on OP_CAT Covenant

**Powered by** [**100Layer**](https://100layer.io/)

**Dec. 20th 2024**

**X:** [**https://x.com/100_Layer**](https://x.com/100_Layer)

The WBTC protocol is a completely decentralized Wrapped BTC protocol based on OP_CAT Covenant. The WBTC protocol aims to make BTC more programmable, so that BTC can be used in the DeFi applications (AMM, Stablecoin, Lending, etc.) based on OP_CAT Covenant or other technologies on Bitcoin Layer 1, similar to WETH's empowerment for ETH programmability on Ethereum Layer 1. The Covenant can be regarded as the Smart Contract on Bitcoin Layer 1. The WBTC protocol is compatible with the CAT20 protocol, and proposes an implementation method of BTC wrapping and unwrapping based on OP_CAT Covenant. The OP_CAT Covenant manages the user's locked BTC without any trusted third party to custody user assets, truly realizing a completely decentralized, trustless, non-custodial, censorship-resistant, and 1:1 BTC-pegged WBTC.

The WBTC protocol evolved from the CAT20 protocol and is compatible with the CAT20 protocol. Like the CAT20 protocol, the WBTC token can be issued on any UTXO blockchain that enables OP_CAT. At the same time, any application that supports CAT20 token natively supports the WBTC token. Similarly, the WBTC protocol has the same advantages as the CAT20 protocol: Bitcoin miner validated and uses smart contracts, specifically covenants, to manage WBTC token mints, transfers and burns, as well as the BTC wrapping and unwrapping.

## 1. Principles

### 1.1 1:1 BTC-Pegged WBTC

In this protocol, when the user wraps BTC, the BTC will be locked into the OP_CAT Covenant, which locked the same BTC amount as the WBTC supply. Any user can unwrap WBTC to the same amount of BTC at any time, and no one can interfere with the user's wrapping and unwrapping, like WETH (Wrapped ETH) does.

### 1.2 CAT20 Compatible

The WBTC protocol is implemented by the OP_CAT Covenant and is compatible with the CAT20 protocol, which means that the deploy, mint, transfer, and burn of WBTC token are consistent with the rules in the CAT20 protocol, ensuring that all CAT20 infrastructures can support the WBTC token, and the WBTC token can be used in any DeFi application that supports CAT20 token (AMM, Stablecoin, Lending, etc.).

### 1.3 Completely Decentralized

The WBTC protocol is on Bitcoin Layer 1 and is implemented by the decentralized OP_CAT Covenant. It does not rely on off-chain indexers and is verified by the Bitcoin minter. No one, including the WBTC issuer, can change the operating mechanism and algorithm of the on-chain OP_CAT Covenant.

### 1.4 Trustless

WBTC deploy, mint, transfer, and burn, and BTC wrap and unwrap are all implemented through OP_CAT Covenant, that does not require any trusted third party to manage BTC or WBTC, truly realizing the trustless BTC management on Bitcoin Layer 1.

### 1.5 Non-Custody of User Assets

Users can lock BTC to mint WBTC Token. The locked BTC is managed by the OP_CAT Covenant instead of being managed by a third party. The locked BTC can only be unlocked when the user burns the corresponding WBTC token. No one can abuse the locked BTC managed by the OP_CAT Covenant.

### 1.6 Censorship-Resistant

All the operations of the WBTC protocol are completed on the OP_CAT Covenant and are atomic. No additional process (like signature) is required from the WBTC issuer. After the user agrees to the transaction by signing, the subsequent operations are automatically completed by the Covenant and then verified by the Bitcoin minter. No one can change the behavior and results, and no one can censor the user.

## 2. Innovations

The WBTC protocol has 4 important innovations: Wrap, Unwrap, Wrapper (BTC Wrapping Contract) and Refill Minter, which will be introduced in details below.

### 2.1 Wrap: Lock BTC to Mint WBTC

In the WBTC protocol, users can lock BTC to the BTC Wrapping Contract (wrapper) to mint the same amount of WBTC token that is compatible with the CAT20 protocol. This process is atomic and in one transaction, that means locking BTC and minting WBTC either succeed or fail at the same time. The BTC Wrapping Contract (wrapper) is the Smart Contract based on OP_CAT Covenant, which is responsible for managing the BTC assets locked by users. The WBTC token users received can participate in any DeFi application (AMM, Stablecoin, Lending, etc.) that supports CAT20 on Bitcoin Layer 1.

### 2.2 Unwrap: Burn WBTC to Unlock BTC

In the WBTC protocol, the WBTC token holders can burn WBTC to unlock the same amount of BTC. The entire process is controlled by the Smart Contract based on OP_CAT Covenant: BTC Wrapping Contract (wrapper), and no one can censor the user. This process is also atomic and in one transaction, that means burning WBTC and unlocking BTC can either succeed or fail at the same time.

### 2.3 Wrapper: BTC Wrapping Contract

Wrapper (BTC Wrapping Contract) is the management contract of the locked BTC. When users wrap BTC, they lock BTC to the wrapper to receive the same amount of WBTC. Similarly, for the unwrapping, when users burn WBTC, the wrapper will unlock the same amount of BTC to the user. Both processes are verified by Bitcoin minter, are completely decentralized and trustless, and cannot be controlled by anyone. Wrapper is the core of the WBTC protocol.

### 2.4 Refill Minter

WBTC and BTC should have the same max supply: 21,000,000, but in the original CAT20 protocol, as the burned WBTC token increases, the WBTC token that can be minted will decrease and eventually drop to 0, then users cannot mint new WBTC token, that means the real WBTC max supply will decrease. To change this situation, this protocol proposes a minter refill mechanism, which can increase the WBTC remaining amount in the minter when users burn WBTC, so as to ensure that the WBTC max supply remains unchanged when users unwrap/burn WBTC, and is always equal to the BTC max supply.

## 3. Operations

This chapter will describe the WBTC operations. The WBTC protocol supports 5 operations: Deploy, Wrap, Unwrap, Merge/Split Wrapper, and Transfer. Deploy and Transfer are completely consistent with CAT20 protocol, and Mint is partially consistent with CAT20, ensuring the full compatibility with the CAT20 protocol.

### 3.1 Deploy

The deploy of WBTC protocol uses the same method as CAT20: commit and reveal scheme utilizing Taproot (P2TR). This protocol adds a new attribute: toSatoshiRatio, which indicates the exchange ratio between the currently deployed WBTC token and BTC Satoshi. Generally, this attribute should be 100,000,000, which is equal to the exchange ratio between BTC and Satoshi. The byte sequence cat (0x636174 in hex) signifies that this envelope is part of the CAT Protocol and WBTC Protocol. For more information, please refer to the CAT20 Deploy: https://catprotocol.org/cat20#1-deploy.

### 3.2 Wrap: Lock BTC to Mint WBTC

In the WBTC protocol, wrap BTC actually includes two operations: mint WBTC token and lock BTC. These two operations are completed in one transaction, ensuring the atomicity of the two operations. These two operations are controlled by the Mint Contract (minter). The user's BTC is locked into the BTC Wrapping Contract (wrapper). The locked BTC in the wrapper can only be unlocked to users when users burn WBTC token. The mint part is completely consistent with the CAT20 mint logic to ensure the CAT20 compatibility. The mint operation can generate new minter UTXOs, which in turn can be spent to mint more tokens recursively. New WBTC tokens can only be issued by spending minter UTXOs and locking BTC UTXOs to the BTC Wrapping Contract (wrapper). A mint transaction must follow the following rules to be valid:

- There is exactly one minter input.
- There is exactly one WBTC token output.
- There is one or more wrapper output.
- The WBTC token amount must be equal to the total locked BTC amount to the wrapper.
- The WBTC token output must be right after a minter output, if any. Note there can be zero and multiple minter outputs.
- The wrapper output must be right after the token output.
 
![wrap drawio](https://github.com/user-attachments/assets/4a3ff0a1-9810-4ee0-8ef1-e01c916509f8)

### 3.3 Unwrap: Burn WBTC to Unlock BTC

Besides the burn method supported by CAT20 protocol, the WBTC protocol introduces a new burn method: unwrap, which is exactly the opposite of the wrap logic. Unwrap actually includes two operations: burn WBTC token and unlock BTC. These two operations are completed in one transaction, ensuring the atomicity of the two operations. These two operations are controlled by the Burn Guard Contract, the BTC Wrapping Contract (wrapper) and the Mint Contract (minter). The BTC locked in the Wrapping Contract (wrapper) will be unlocked to the user along with the user's WBTC burn. In order to prevent the WBTC token remaining amount in minter from being exhausted, the WBTC protocol restores the WBTC token remaining amount in minter during unwrapping, and the restored amount is equal to the burned WBTC token amount, that is called minter refill. A unwrap transaction must follow the following rules to be valid:

- There is exactly one minter input, at index 0.
- There is one or more WBTC token input.
- There is exactly one burn guard input.
- There is one or more locked BTC (wrapper) input.
- The total locked BTC amount in input should be greater than or equal to the total WBTC token amount in input.
- The locked BTC (wrapper) in input must be locked by the same minter as the input minter.
- There is exactly one minter output.
- There is no token output.
- There is one or more locked BTC (wrapper) output, if there is any locked BTC change.
- The minter token remaining amount in output should be equal to the minter token remaining amount in input + the burned token amount.
- The locked BTC (wrapper) in input should be unlocked to the user, with amount: the burned token amount.

![unwrap drawio](https://github.com/user-attachments/assets/fb0adadb-84c2-4798-8cd6-27d531356e24)

### 3.4 Merge/Split Wrapper

In order to facilitate the management of BTC UTXO locked in the BTC Wrapping Contract (wrapper), this protocol supports the Merge/Split of the wrapper. The locked BTC UTXO can be merged or split by the locked minter. After the merge/split, the BTC UTXO is still locked in the original wrapper by the original minter. A merge/split transaction must follow the following rules to be valid:

- There is exactly one minter input, at index 0.
- There is one or more locked BTC (wrapper) input.
- There is one or more minter output.
- There is one or more locked BTC (wrapper) output.
- All the locked BTC (wrapper) in input must be locked by the same minter.
- All the locked BTC (wrapper) in output must be locked with the same minter of the locked BTC (wrapper) in input.
- The total locked BTC amount in output must be equal to the total locked BTC amount in input.
- The minter token remaining amount in output must be equal to the total minter token remaining amount in input.

![merge drawio](https://github.com/user-attachments/assets/a231ad98-7062-432f-8f93-7461ba321c03)

### 3.5 Transfer

The transfer logic of the WBTC protocol is exactly the same as the CAT20 protocol to ensure the CAT20 compatibility. WBTC token UTXO can be split into small amounts. Multiple WBTC token UTXOs can be merged into a single UTXO, if only they descend from the same genesis transaction. In general, there can be multiple token inputs and token outputs in a token transfer transaction, and they can appear anywhere in the transaction. The preservation of token balance is enforced by miners: the quantity of tokens in the inputs must equal that in the outputs. For more information, please refer to the CAT20 Transfer: https://catprotocol.org/cat20#3-transfer.

## 4. Anti-Attacks

The design of the WBTC protocol can prevent arbitrary malicious attacks to ensure the security of the locked BTC, WBTC issuance, and the entire wrapping and unwrapping process.

### 4.1 Preventing Mint WBTC Arbitrarily

The WBTC mint is controlled by the WBTC Minter Contract. Users are only allowed to mint WBTC token if they lock the same amount of BTC to the BTC Wrapping Contract (wrapper). The entire verification is completed in the OP_CAT Covenant. No one can mint WBTC arbitrarily under any other circumstances.

### 4.2 Preventing Unlock Locked BTC Arbitrarily

There are two types of attacks for the locked BTC: using the wrong minter, and burning the wrong WBTC token. In the first attack, the BTC Wrapping Contract (wrapper) will check whether the minter is consistent with the minter when it was locked, and the wrong minter will be rejected by the wrapper. In the second attack, the wrapper will check whether the burned WBTC token is consistent with the token in the minter, if not, it will be rejected by the wrapper.

### 4.3 Atomicity to Prevent Attacks from WBTC Issuer

Another attack method is to censor users. The WBTC protocol is completely based on OP_CAT Covenant. The user's wrapping and unwrapping operations are atomic, that is, locking BTC and minting WBTC are either successful or fail at the same time, and the burning WBTC and unlocking BTC are also either successful or fail at the same time, avoiding the intermediate state: a single operation success. Also, the processing logic of the OP_CAT Covenant only requires the user's signature, and does not require additional logic such as the signature of the WBTC issuer.

### 4.4 Preventing Dust Attack

Another possible attack is dust attack, that is generating a large number of small amount wrappers to carry out dust attacks to the WBTC protocol. Although it will not affect the user's assets, it may still affect the user experience when wrapping and unwrapping. Therefore, this protocol supports Merge/Split wrappers to deal with this possible risk.

## 5. References

[1] Covenant Attested Token (CAT) Protocol, https://catprotocol.org/

[2] OP_CAT in Tapscript, https://github.com/bitcoin/bips/blob/master/bip-0347.mediawiki

[3] What Is Wrapped Ethereum (WETH), https://coinmarketcap.com/academy/article/what-is-wrapped-ethereum-weth

[4] Bitcoin: A Peer-to-Peer Electronic Cash System, https://bitcoin.org/bitcoin.pdf

[5] Ethereum: A Next-Generation Smart Contract and Decentralized Application Platform, https://ethereum.org/en/whitepaper/

[6] 100Layer: A Liquidity Protocol on Bitcoin Layer 1 and Fractal by OP_CAT, https://100layer.io/
