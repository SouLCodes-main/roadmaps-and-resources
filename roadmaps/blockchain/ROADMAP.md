# Blockchain Roadmap

> How a shared ledger works, how a wallet's keys actually protect it, and how to deploy a small contract on a test network.

You can finish this without buying cryptocurrency. The hands-on parts run on Sepolia, a public Ethereum test network. The ETH there is free and has no market price. The seed phrase is still a real secret, so treat the paper like it matters.

## Prerequisites

- A computer and a browser
- Somewhere to keep notes
- No programming for the first half. Before section 6, you want variables, functions, and objects. [MDN's JavaScript guide](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting) is enough.

## Learning Path

### 1. Blocks and hashes

A blockchain is a log that many computers keep a copy of. New updates are grouped into a block. Each block stores a hash of the block before it.

A hash is a short fingerprint of some data. The same input always gives the same hash. Change one letter and the hash looks unrelated. You cannot turn the hash back into the original data. Edit an old block and every later fingerprint stops matching, so the rewrite is visible.

That is useful when several parties want a record and none of them should be the only editor. Payments were the first famous use. Programs that live on the record came later. That second idea is Ethereum, in section 4.

A chain stores what was submitted. It does not check that the submission was true. On a public chain the history is also readable by anyone with a browser.

#### Learn

- [Blockchain demo](https://andersbrownworth.com/blockchain/blockchain)
- [What is Ethereum?](https://ethereum.org/what-is-ethereum/)
- [But how does bitcoin actually work?](https://www.youtube.com/watch?v=bBC-nXj3Ng4) (3Blue1Brown)

#### Build

Open the demo. Type your name into a block, change one letter, and watch the hash jump. Switch to the chain view, edit an early block, and watch a later block show the link is broken. Write two sentences on what the hash caught.

#### You should learn

- Block, transaction, hash, node
- Why the next block stores the previous hash
- Consensus: the rule for which block gets added
- A public chain preserves a history. It does not prove the input was true, and it does not hide the history

---

### 2. Keys and signatures

The coins sit on the ledger. The ledger records that an address may spend them. The wallet holds the key that can produce a valid signature for that address. Delete the app, keep the seed, and a new install can sign again. Lose the seed and the key together, and the coins are still listed, with nobody able to move them.

Four objects, and only the last one is safe to paste around:

- Seed phrase: a list of words that recreates the keys. Paper, offline.
- Private key: the secret the wallet uses to sign.
- Public key: what nodes use to check a signature.
- Address: a short name derived from the public key. This is what you give someone who wants to pay you.

A signature shows that the holder of the private key approved that exact message. Publishing the signature does not publish the key. Edit the message and the check fails.

A faucet, a support chat, or an "airdrop" page never needs those words. Close any form that asks you to type them.

#### Learn

- [Ethereum accounts](https://ethereum.org/developers/docs/accounts/)
- [Wallets](https://ethereum.org/wallets/)
- [How bitcoin works](https://bitcoin.org/en/how-it-works)

#### Build

On paper, write seed phrase, private key, public key, and address. Mark the one you would put on a poster. Then write three places a seed must not go, picked from the ones you would actually use by accident: a notes app, a screenshot, a chat, a cloud photo, a website form.

#### You should learn

- A hash says the data has not changed. A signature says a key holder approved this message.
- An address is public. A seed phrase is the master secret.
- A node checks the signature. It never receives your private key.

---

### 3. Bitcoin

Bitcoin records outputs: specific chunks of bitcoin, created by earlier transactions, waiting to be spent. There is no single field that says "Sam has 20." To spend an output, a transaction names it as an input and writes new outputs.

It works like cash, where you cannot tear a note in half. Say you hold one output worth 0.5 bitcoin and you want to pay 0.2. The transaction spends the whole 0.5, writes 0.2 to the recipient, and writes about 0.29 back to you as a new output. That new output is your change. The small gap left over is the fee, and the miner who includes the transaction collects it. The old 0.5 output is finished. It cannot be spent a second time. An output that is still spendable is a UTXO, an unspent transaction output. The number your wallet calls a balance is just the sum of UTXOs you can still sign.

A second transaction that tries to spend the same output is rejected. That is how the network stops a double spend of that coin.

Miners choose the next block with proof of work. They bundle valid transactions and vary a number until the block's hash is small enough to meet a target. The search costs electricity and hardware. Rewriting an old block means doing that search again, then outrunning every honest block mined after it. You do not need to mine anything for this section. Mining is an industry. The idea is enough.

A new transaction waits until a miner includes it. A higher fee makes it more attractive to include. After it is in a block, later blocks built on top are called confirmations. Each one makes a rewrite more expensive.

#### Learn

- [How bitcoin works](https://bitcoin.org/en/how-it-works)
- [mempool.space](https://mempool.space/)
- [Bitcoin whitepaper](https://bitcoin.org/bitcoin.pdf), sections 1 to 4. Skip the math on the first read.

#### Build

On mempool.space, open a recent block. Write down the height and how many transactions it holds. Open one transaction and name an input, an output, and the fee. If several outputs show up, mark which one you think is the payment and which is change, and add the word "guess". The chain does not tell you.

#### You should learn

- Input, output, UTXO, change, fee
- Why an output is spent in full
- What miners are searching for
- What a confirmation is counting

---

### 4. Ethereum

Ethereum keeps a hash-linked chain and runs programs on it. People and programs both have accounts. ETH is the asset that pays for computation. A transaction can move ETH, or it can call a program stored on the network. Those programs are smart contracts. The word "smart" means the code runs as written. A bug runs as written too.

| | Bitcoin | Ethereum |
| --- | --- | --- |
| Record | Unspent outputs | Accounts with balances |
| Next block | Proof of work, miners | Proof of stake, validators |
| A simple payment | Spend an output, create new ones | Decrease one balance, increase another |

Two account types:

- An externally owned account is controlled by a private key. It has an ETH balance and a nonce.
- A contract account holds code and storage, plus a balance. It runs when a transaction calls it.

Gas meters the work a transaction asks the network to do. The fee is roughly gas used times the price you offered. A call that fails can still cost gas: the nodes ran the computation, then threw away the state change. Reading data can be simulated locally. Writing storage needs a signature and a fee.

Validators lock ETH as stake and take turns proposing blocks. Other validators vote. A validator who breaks the rules can lose stake. Ethereum moved to this in 2022. Articles from before that still talk about Ethereum miners. Use them for accounts and transactions. Use the proof-of-stake docs for how blocks are chosen now.

After you sign, the transaction sits in the mempool, a waiting room each node keeps for transactions not yet in a block. An explorer is a website that reads node data and draws it. The chain is the nodes, not the website.

Mainnet is where ETH has a price. Sepolia is the testnet app developers use. Its chain id is `11155111`. The same seed can derive the same-looking address on both networks. The balances are separate. Look at the network name before you trust a number in the wallet.

#### Learn

- [Intro to Ethereum](https://ethereum.org/developers/docs/intro-to-ethereum/)
- [Transactions](https://ethereum.org/developers/docs/transactions/)
- [Gas](https://ethereum.org/gas/)
- [Proof of stake](https://ethereum.org/developers/docs/consensus-mechanisms/pos/)

#### Build

From the transactions page, write what `nonce`, `to`, `value`, and `data` each do. Open any successful transaction on [Sepolia Etherscan](https://sepolia.etherscan.io/) and match those fields on the page. You do not need a wallet for this.

#### You should learn

- Externally owned account vs contract account
- What gas is metering
- Signature, mempool, block, explorer
- Mainnet ETH and Sepolia ETH are different ledgers

---

### 5. Wallet safety

Do this before you deploy a contract. The software will ask you to save 12 or 24 words, and you want a habit ready before that screen.

This guide uses [MetaMask](https://metamask.io/download) because beginner docs show its screens. Another wallet you already understand is fine. Type the address yourself, or use that link. Skip the ads above the search result. Bookmark the real page, then compare the extension's publisher with the bookmark.

The app password locks the keys on this device. It does not recreate the wallet on a new computer. The seed does that. Write the seed on paper. Do not photograph it, and do not put it in a notes app that syncs.

Turn on test networks, select Sepolia, and check the chain id is `11155111`. If you add the network by hand, check that number before you approve. Get practice ETH from a faucet on the [networks page](https://ethereum.org/developers/docs/networks/). A faucet may ask for an email or an address. Pasting an address is normal. Typing a seed is not.

Create a second account in the same wallet. Send a small amount from the first account to the second. On the prompt, check four things: network (Sepolia), recipient (the second account, start and end of the address), amount (a small slice), and data (empty for a plain transfer). Surprise data means stop.

#### Learn

- [Security and scam prevention](https://ethereum.org/security/)
- [Networks](https://ethereum.org/developers/docs/networks/)
- [Find a wallet](https://ethereum.org/wallets/find-wallet/)

#### Build

Send Sepolia ETH from account 1 to account 2. Open the transaction on [Sepolia Etherscan](https://sepolia.etherscan.io/). In your notes, save the hash and write the network, from, to, value, and whether it succeeded. Lock the wallet and unlock it with the password. You should not need the seed for that.

#### You should learn

- The practice seed can also sign on mainnet, so it stays a secret
- What a faucet is allowed to ask for
- What you read on a wallet prompt before you confirm
- Chain id `11155111` is Sepolia

---

### 6. A first contract

Solidity is the language these contracts are written in. A compiler turns it into bytecode the EVM can run, plus an ABI: a description of the functions so a wallet knows how to call them.

Type this yourself. The eye catches more when you type it.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.24;

contract Notebook {
    string public note;

    function write(string calldata newNote) external {
        note = newNote;
    }
}
```

`string public note` is storage, and `public` also creates a free reader named `note`. Calling that reader asks a node for the current value. It does not need a transaction. `write` changes storage, so it needs a signature and gas. The contract gets its own address when you deploy. That address is not your wallet address.

Use [Remix](https://remix.ethereum.org/). No install.

1. Create `Notebook.sol`, compile with a 0.8 compiler that satisfies the pragma, and fix errors before you deploy.
2. Deploy to the Remix VM (the fake chain in the browser). Call `write`, then `note`.
3. In the wallet, select Sepolia and confirm you still have faucet ETH.
4. In Remix, set the environment to Injected Provider. Confirm the page shows Sepolia. If the wallet says mainnet, cancel.
5. Deploy, copy the contract address, and open it on [Sepolia Etherscan](https://sepolia.etherscan.io/).
6. Call `write` again with a new sentence and find that transaction on the explorer.

Anyone can call `write` on this contract. There is no owner check yet. The next section adds one, so you can feel the difference.

#### Learn

- [Introduction to smart contracts](https://docs.soliditylang.org/en/latest/introduction-to-smart-contracts.html)
- [Hello World smart contract](https://ethereum.org/developers/tutorials/hello-world-smart-contract/)
- [Cyfrin Updraft: Solidity](https://updraft.cyfrin.io/courses/solidity), after the Remix deploy, as the course to continue with

#### Build

Deploy the notebook on Sepolia. Save the wallet address, the contract address, the creation hash, and the `write` hash. In one paragraph, explain why the write cost gas and reading `note` did not.

#### You should learn

- Source, bytecode, and ABI. The EVM runs bytecode.
- A read and a state change are different requests
- What you check on the wallet prompt during a deploy
- Which address holds the string

---

### 7. A tip jar, and what a token is

A dapp is an ordinary website plus one or more contracts. The site prepares a transaction. The wallet asks a person to sign. If the site went away, the contract would still be on Sepolia, and someone could call it from a wallet directly.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.24;

contract TipJar {
    address public owner;

    event TipReceived(address indexed from, uint256 amount);

    constructor() {
        owner = msg.sender;
    }

    function tip() external payable {
        require(msg.value > 0, "Send some ETH");
        emit TipReceived(msg.sender, msg.value);
    }

    function withdraw() external {
        require(msg.sender == owner, "Not the owner");
        (bool ok, ) = owner.call{value: address(this).balance}("");
        require(ok, "Withdraw failed");
    }
}
```

`constructor` runs once, in the deploy transaction, and stores the deployer as `owner`. `msg.sender` is the address that called. `payable` and `msg.value` mean the call can carry ETH. The tipped ETH is the contract's own balance, `address(this).balance`. `withdraw` sends that balance to the owner and reverts for everyone else. The event is a log. Explorers can filter logs. The balance only tells you what is there now.

Deploy on the Remix VM first. Tip from a second account if the VM lets you switch, and confirm `withdraw` fails from that account. Then repeat on Sepolia with the two accounts from section 5.

A token is a contract that stores balances, or unique ids, behind a shared interface so wallets know how to display it. It is not a second kind of ETH.

- [ERC-20](https://ethereum.org/developers/docs/standards/tokens/erc-20/): each unit is interchangeable. The contract remembers a balance per address.
- [ERC-721](https://ethereum.org/developers/docs/standards/tokens/erc-721/): each id is distinct. The contract remembers an owner per id. This is the usual NFT shape.

The interface does not make the contract safe, useful, or honest. Read [OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts/5.x/) before you write your own accounting. Skip minting a token that strangers can buy. A tested tip jar and a clear README are a stronger portfolio piece than a mainnet ticker.

#### Learn

- [ERC-20](https://ethereum.org/developers/docs/standards/tokens/erc-20/) and [ERC-721](https://ethereum.org/developers/docs/standards/tokens/erc-721/)
- [Smart contract security](https://ethereum.org/developers/docs/smart-contracts/security/)
- [OpenZeppelin Contracts](https://docs.openzeppelin.com/contracts/5.x/)

#### Build

Deploy `TipJar` on Sepolia from account 1. Tip from account 2. Withdraw from account 1. Open the tip transaction and find the `TipReceived` log. Then write two sentences on where an ERC-20 balance lives, compared with the ETH sitting in this contract.

#### You should learn

- `msg.sender`, `msg.value`, and `owner`
- Why the second account cannot withdraw
- ETH held by a contract, versus a number stored in an ERC-20
- A website click asks the wallet to sign. The click itself moves nothing.

---

## Projects

Stay on Sepolia, chain id `11155111`.

### Beginner

- The notebook, deployed, with the sentence visible on Sepolia Etherscan
- The tip jar, tipped from a second account, withdrawn by the owner, log visible

### Intermediate

- Add an owner check to `write` on the notebook, the same idea as `withdraw` on the jar
- Read the Charity Donation Tracker in [blockchain-projects](https://github.com/0xPixelNinja/blockchain-projects). It is the closest cousin of the tip jar: campaigns, deposits, an owner withdraw. Contracts are Foundry. The site is Next.js. Run `forge test` before you connect a wallet.

### Advanced

- Pick one toolkit and finish one project in it. [Foundry](https://book.getfoundry.sh/) keeps tests in Solidity. [Hardhat](https://hardhat.org/tutorial) plus [viem](https://viem.sh/) fits a JavaScript frontend. Both deploy contracts. The choice is where you want to spend the hours.
- After you can read the tip jar line by line, work through a few [Ethernaut](https://ethernaut.openzeppelin.com/) levels. Write the bug in your notes before you open a walkthrough. Those contracts are a practice range. Using the same tricks on a contract you do not own is out of bounds.

Leave these until you have a real reason: a mainnet token, a bridge, a pool holding other people's funds, your own rollup or wallet.

## Additional Resources

- [Blockchain Basics](https://updraft.cyfrin.io/courses/blockchain-basics) on Cyfrin Updraft, a free video course, about 6 hours, good beside sections 1, 2, and 4
- [ethereum.org Learn](https://ethereum.org/learn/)
- [Mastering Bitcoin](https://github.com/bitcoinbook/bitcoinbook), when section 3 feels short
- [Solidity by Example](https://solidity-by-example.org/), as a lookup after the Cyfrin Solidity course
- [Solidity docs](https://docs.soliditylang.org/en/latest/)
- [Layer 2](https://ethereum.org/layer-2/), once a Sepolia deploy feels ordinary
- [Ethereum glossary](https://ethereum.org/glossary/)

When a video and a doc disagree, trust the doc. A course filmed against an old compiler can still teach storage. Its install steps, and any talk of Ethereum miners, may be leftovers. Keep the idea. Take the commands from the current page.

## Completion Checklist

- [ ] Broke a hash link on purpose in the demo
- [ ] Can sort seed phrase, private key, public key, and address by who should see them
- [ ] Opened a live Bitcoin transaction and named an input, an output, and the fee
- [ ] Can explain an ETH account balance and a UTXO as two different books
- [ ] Sent Sepolia ETH between two of your own accounts
- [ ] Deployed the notebook on Sepolia and read `note` on an explorer
- [ ] Tipped the jar from a second account and withdrew as the owner
- [ ] Can say where an ERC-20 balance is stored

## Contributing

Found a stale link or a clearer exercise?

See the repository [CONTRIBUTING.md](../../CONTRIBUTING.md).
