---
layout: post
title: Interacting with an Ethereum Voting Smart-Contract 
subtitle: using Pythons web3
cover-img: /assets/img/ethpaper.png
thumbnail-img: /assets/img/ethpaper.png
share-img: /assets/img/ethpaper.png
tags: [web3, python, voting, etherium, blockchain]
---

In this article, we will use the [web3.py](https://pypi.org/project/web3/) python library to demonstrate that anyone can interact with the [DigiPol](https://digipol.app/) smart-contract in their own way by demonstrating how to get the vote count of a particular ballot.

The [DigiPol](https://digipol.app/) app uses smart contracts on the Ethereum network to publish ballots, make votes and get voting results. Ethereum is a decentralized cryptocurrency with smart contract capability. This means that the information on the Ethereum blockchain and the smart contract methods may be accessible by the anyone!

## Set-up

Before starting, you will need to install web3.py onto your system. You can do this via pip:

```bash
pip install web3
```

You will also need to have an private key and save as an environmental variable. Here we will save it as **PRIVATE_KEY**. If you don’t have one, you can generate one using a service like [MetaMask](https://metamask.io/). Now let’s start coding!

## Using web3

```python
from web3 import Web3, HTTPProvider
from eth_account import Account
from web3.middleware import construct_sign_and_send_raw_middleware
```

In order to interact with the DigiPol smart contract, we will need:

- A private key
- The testnet endpoint (an ethereum testnet)
- The smart contract address
- The smart contract abi (a json file to help define the smart contract methods with web3)

```python
import os
import json
PRIVATE_KEY = os.getenv('PRIVATE_KEY')
CONTRACT_ADDRESS = '0xca733a39b72DA72078DBc1c642e6C3836C5b424E'
PROVIDER_HTTP_ENDPOINT = "http://54.153.142.251:8545"
abi = json.load(open("voting.json"))
```

*Note, the json file for the abi can be produced from the [smart contract repo](https://github.com/voteflux/voting-alpha-mini-sc) or you can use [one I prepared earlier](https://github.com/voteflux/voting-alpha-mini-sc/blob/master/VotingAlpha.abi.json).*

Next, we get the smart contract as a python object:

```python
w3 = Web3(Web3.HTTPProvider(PROVIDER_HTTP_ENDPOINT))
VotingContract = w3.eth.contract(address=CONTRACT_ADDRESS, abi=abi)
```

We then add our **private key** to web3 via the middleware:

```python
acct = Account.from_key(PRIVATE_KEY)
w3.middleware_onion.add(construct_sign_and_send_raw_middleware(acct.privateKey))
```

## Getting the vote count

Each ballot has an associated **‘ballotspec hash’**, a unique identifier string for that bill. All of the spec hashes are publicly available. Here we will use an existing one to get the ballot id via the **getProposalId** smart contract method. Then we can get the ballot (proposal) information using the getProposal method which returns a list of related information.

```python
spec_hash = "0xf0b9270d28dba8782ed9e079…81ca198f21b9b3e1c57d0bd"
p_id = VotingContract.functions.getProposalId(spec_hash).call()
proposalInfo = VotingContract.functions.getProposal(p_id).call()
```

Finally we can get the vote counts for the ballot. The *no* votes are in position **3** of the **proposalInfo** list and the *yes* votes are in position **4**.

```python
print("No votes:", proposalInfo[3])
print("Yes votes:", proposalInfo[4])
```

### *Voilà!*

Now you can check the votes on the blockchain directly and don’t have to trust the results that are shown in DigiPol app. You should use the DigiPol app though as it’s pretty cool and looks a lot nicer!

## Full Example

Here is the full script wrapped in a *get_votes_from_blochchain* function:

```python
import os
import json
from web3 import Web3, HTTPProvider
from eth_account import Account
from web3.middleware import construct_sign_and_send_raw_middleware


PRIVATE_KEY = os.getenv('PRIVATE_KEY')
CONTRACT_ADDRESS = '0xca733a39b72DA72078DBc1c642e6C3836C5b424E'
PROVIDER_HTTP_ENDPOINT = "http://54.153.142.251:8545"

def get_votes_from_blochchain(spec_hash):
    w3 = Web3(Web3.HTTPProvider(PROVIDER_HTTP_ENDPOINT))
    acct = Account.from_key(PRIVATE_KEY)
    abi = json.load(open("voting.json"))

    VotingAlpha = w3.eth.contract(address=CONTRACT_ADDRESS, abi=abi)

    w3.middleware_onion.add(construct_sign_and_send_raw_middleware(acct.privateKey))
    print(spec_hash)
    p_id = VotingAlpha.functions.getProposalId(spec_hash).call()
    proposalInfo = VotingAlpha.functions.getProposal(p_id).call()

    return(proposalInfo[4], proposalInfo[3])
```