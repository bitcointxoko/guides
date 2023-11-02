### What is Cashu?
[Cashu](https://cashu.space/) is an open-source Ecash protocol for Bitcoin that offers instant, zero fee transactions with near perfect privacy, created by nostr:npub12rv5lskctqxxs2c8rf2zlzc7xx3qpvzs3w4etgemauy9thegr43sf485vg. 

Here is a table comparing Cashu and on-chain Bitcoin, taken from nostr:npub1cj6ndx5akfazux7f0vjl4fyx9k0ulf682p437fe03a9ndwqjm0tqj886t6's [Nuts and Bolts](https://nuts-and-bolts.gandlaf.com/) presentation at Bitcoin Conference Bangkok 2023. 

| Cashu | Bitcoin (on-chain) |
|--|--|
| No Ledger | Distributed Ledger |
| Bearer Token | UTXO |
| Blinded Transactions | Public Transactions|
| Centralised | Decentralised |
| Trusted | Trustless |
| Ephemeral Transactions| Eternal Transactions |

As we can see, Cashu sacrifices trustlessness and decentralisation for privacy. These trade-offs makes a lot of sense when it comes to custodial solutions, as the user is already using a centralised and trusted service. Traditional custodial solutions have horrible privacy as the custodian knows how much funds a user has and with whom they are transacting. This means that individuals can be easily targeted and censored. Data records can also become a honeypot. 

In contrast, Cashu mints can act as custodians that do not know who their users are, how much funds they have, nor with whom they are transacting. The only data record the mint has is a list of spent secrets that cannot be reused, with no way to associate them with users. 

Some use cases for Cashu include vouchers which are already centralised and custodial; pay-per-resource usage such as APIs, nostr relays and mixnets; integrated systems replacing the account and balance model; and exchange/mixing services to unlink deposits and withdrawals. 
### History
Ecash was first conceived by David Chaum in 1982 as an electronic value transmission protocol using blind signatures. Cashu is an Ecash implementation using David Wagner's [variant](https://cypherpunks.venona.com/date/1996/03/msg01848.html) of Chaumian blinding from 1996, created by nostr:npub12rv5lskctqxxs2c8rf2zlzc7xx3qpvzs3w4etgemauy9thegr43sf485vg. 
### Terminology
To help us understand how Cashu works, we will cover some essential terminology first. 
#### Mint
The Cashu mint is the custodian of user funds. Its job is to mint and burn tokens and prevent double spending. 

The Cashu mint sits on top of a Lightning node, so it can send and receive Lightning payments. This includes swapping with other mints. However, you can still transact with ecash tokens even if the Lightning node is offline. 

The mint does not know who the user is, how much funds they have, nor with whom they are transacting with. 

However, since the mint is the custodian of user funds, you should choose a mint that you trust and know the operator. Use small amounts or immediately redeem tokens. 
#### Token
A Cashu token is essentially a piece of data signed by the mint. The user holds these tokens in their wallet. 

Cashu uses a coin based system with fixed denominations. 

An analogy is the denomination of bills in fiat. For example, in euro there are 5, 10, 20, 50, 100 EUR bills...

In Cashu, tokens are denominated by powers of 2. For example 1, 2, 4, 8, 16, 32, 64, 128 sats and so on...

The point of using denominations is to increase the anonymity set amongst the users. 
### How does it work? Explained Like I'm 5

![image]()

User Alice wants to mint new Cashu tokens. So she goes to the mint, Bob, and says, "Hey! I want to mint new Cashu tokens."

Bob responds saying, "OK, pay me and send me a blinded secret." Blinded secret means Alice knows the secret, but Bob cannot see it. 

Alice generates a secret and then blinds it so that Bob does not know what the secret is. She pays Bob and sends him her proof of payment and blinded secret. 

When Bob is satisfied that he has been paid, he signs Alice's blinded secret and gives her back the signed blinded secret. Since Bob signed it, in the future he can be sure that the token is valid. 

Alice wants to pay Carol. She sends Carol her secret, along with a key to unblind the signed blinded secret. 

Carol wants to redeem her token. So she goes to the mint, Bob, and shows him the secret and the unblinded key that Alice gave her. 

Bob has never seen the secret before and has no idea it was Alice who generated it, since Alice blinded it before sending it to him. But he can verify that he signed it earlier, so he can treat it as a valid spend of the token. He now signs a new token for Carol, or gives her sats back, and adds the secret to a list of spent secrets. If someone tries to redeem with the same secret again in the future, Bob will reject them because it is a double spend. 
#### How does the mint know what amount of sats to give Carol?
Earlier we mentioned that Cashu tokens are denominated in powers of 2 (1, 2, 4, 8, 16, 32...), kind of like paper money bills. 

Bob, the mint, has a distinct private key he uses to sign each denomination. For example, he has a unique private key for 1 sat denomination tokens, another one for the 2 sat denomination, another one for 8 and so on...

This way, when Carol comes to Bob to redeem tokens, Bob knows with which private key he has signed the token before and therefore which denomination the tokens belong to. 
#### What about change?
There is no change in Cashu. You just need to tell the mint to destroy the old tokens and mint new ones in the same exact amount. 

To demonstrate this, let's say Alice has two tokens worth 10 sats. One is 8 sats and another is 2 sats. 

She wants to send 9 sats to Carol. So she goes to the mint and tells Bob to split her 2 sat token into two 1 sat tokens. She can now send 9 sats to Carol in the form of a 8 sat token and a 1 sat token, and keep the other 1 sat token for herself. 
#### Lightning as the connective tissue
What happens when Alice wants to pay David, who does not trust Bob's mint but knows Erin and uses Erin's mint?  

Alice redeems her tokens at Bob's mint, instructing Bob to melt the tokens or convert them back to Lightning sats. Bob's mint then sends a Lightning transaction to Erin's mint. Erin's mint then mints new tokens with David with the Lightning sats she has just received from Bob's mint. 
### What's next for Cashu?
#### Programmable ecash
We can attach spending conditions to ecash, which are enforced by the mint. This can unlock powerful smart contracts without hitting the base chain nor the Lightning network, which can enable public, offline and high-frequency payments. 
#### Proof of Liabilities Scheme
Calle's Proof of Liabilities (PoL) Scheme for Cashu makes it harder for a custodian mint to rug its users by introducing the concept of epochs. In this scheme, the custodian mint regularly rotates the set of private keys they are using once each epoch and publishes publicly auditable lists of tokens minted and burned in the last epoch. Combined with a Proof of Reserves scheme where reserves are held in an on-chain multisig, a cheating mint cannot reduce its liabilities without risking being caught caught by its users. For a more detailed description of how this works, check out the [full write up](https://gist.github.com/callebtc/ed5228d1d8cbaade0104db5d1cf63939). 
### Try it
You can try out Cashu with our guides for [Nutstash] and [eNuts]. All you need is a Lightning wallet and a phone or computer. 
### References
- [Cashu.space](https://docs.cashu.space/)
- [Learn about Cashu](https://docs.cashu.space/resources/learn)
- [Cashu in media](https://docs.cashu.space/resources/media)
- nostr:npub1yn3hc8jmpj963h0zw49ullrrkkefn7qxf78mj29u7v2mn3yktuasx3mzt0 [interview](https://www.youtube.com/watch?v=zdtRT7phXBo) with calle
### See also
- [Support Cashu](https://docs.cashu.space/contribute)
- [NUTs](https://github.com/cashubtc/nuts) - Notation, Usage, and Terminology, the protocol specifications for Cashu
- [X-Cashu](https://github.com/cashubtc/xcashu) - HTTP 402: Payment Required using Cashu
- [Proxnut](https://github.com/gandlafbtc/proxnut) - protect or monetise web resources with using tokens
- [Proof of Liabilities Scheme for Cashu](https://gist.github.com/callebtc/ed5228d1d8cbaade0104db5d1cf63939)
- [Fedimint](https://fedimint.org/) - federated ecash implementation
