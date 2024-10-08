### What is a lightning address?

A lightning address looks like a human readable email address, for example username@domain.com, but actually allows you to be paid in bitcoin instantaneously and cheaply, without needing an online node on your device and manually generating an invoice every time someone wants to pay you. 

Pretty cool, no?
### So how does it work?

It works using the [LNURL pay protocol](https://github.com/lnurl/luds/blob/legacy/lnurl-pay.md), a layer on top of the Lightning Network.  

![Here's a simple diagram of what is happening in the background](https://blob.satellite.earth/908a8572fe3ec8c5b17bcbae1065b69af15b39958401c87128723f3250122cec)Here's a simple diagram of what is happening in the background. 

In short, when a user wants to pay you using your Lightning Address, their wallet converts the Lightning Address into a LNURL payRequest. A successful LNURL payRequest is then used to obtain a BOLT11 invoice. 

💡 Lightning Address > LNURLp > BOLT 11 invoice. 
### Sounds good, but what's the catch?

Many Lightning Address implementations are custodial (although not all), because a domain and a node that is always online are needed for Lightning Addresses to work. Because it's custodial, the custodian can rug you at any time and monitor your transactions. 

You need to trust the owner of the domain not to change the record of your Lightning Address. And it doesn't work if the LNURL server is not online. 

Bitcoin Txoko offers a simple Lightning Address solution backed by [LNbits](https://lnbits.com/). This too is custodial so please only keep a small amount in your Bitcoin Txoko wallet and withdraw to your self-custodial wallet as you receive more sats!
### I'm ready, what do I need to start?

All you need is a mobile phone or computer and an Internet connection!
### 1. Creating your wallet

If you haven't done so already, go to https://bitcointxoko.com and create a wallet. You can name it whatever you want. 

### 2. Activate extensions

The extension `Pay Links` is needed for Lightning Addresses to work. 

Go to `Extensions` in the toolbar and activate `Pay Links`. 
### 3. Creating your pay link

- Open the `Pay Links` extension and click on `New Pay Link`. 

- Choose the wallet you have created. 

- For the `Item Description`, you can enter whatever you want. 

- Choose a your Lightning Address username. Your Lightning Address will look like `username@bitcointxoko.com`. 

- Uncheck `Fixed Amount` and change the `Min` value to 1 and `Max` value to 500000. 

⚠️ You can also change the `Max` value to something higher, but larger payments are more likely to fail due to the limited inbound channel capacity of the [Bitcoin Txoko Lightning node](https://amboss.space/node/03fb64900a7647b4499a88a6c30976333074dad3bb7702d0219bd84dc4ac4a241e). So we recommend keeping it at 500000 sats. 

- Now open `Advanced Options` and change the `Comment maximum characters` to 799. This step is not required but allows more functionalities later on. 

- Check `Enable nostr zaps` at the bottom, so that you can use your Lightning Address to receive zaps.

- The other `Advanced options` are optional, you can configure them if you want, or leave them blank. 

![In the end it should look something like this. ](https://cdn.satellite.earth/4b62fbb4084d198ebd1dfb985db448577bf3bb6b138dfbbd456bc6228751729e.webp)
In the end it should look something like this. 

- When you've checked everything is correct, go ahead and click on `Create Pay Link`. 
### Testing

You can test if your new Lightning Address works by going to another wallet, going to `Send` and typing in your Lightning Address as the destination, then send yourself a few sats. 

Go back to your Bitcoin Txoko wallet and check if you've received your own payment. You might need to refresh the page. 

If everything worked correctly, congratulations! 🥳

If not, let us know. We are always here to help.
### Next steps

#### Nostr zaps
You can add your Bitcoin Txoko Lightning Address to your nostr profile and use it to receive zaps. Usually this is done by going to `Profile` > `Edit` > `Lightning Address` and changing the Lightning Address. 
#### LNDhub
You can import your LNbits wallet as a LNDhub onto your phone using an app like [Zeus](https://zeusln.app/) or [BlueWallet](https://bluewallet.io/), instead of visiting the wallet in your browser every time you want to check your balance or make a payment. Check out nostr:naddr1qvzqqqr4gupzqkvlvlma7a55ccp6d5rrdc27h3ssmdmael286mjaq5uxmqslk04fqqxnzd3exuerqdfkxccnyv3cs0uvul on how to do this. 
#### QR code
You can also share or print your LNURLp QR code so people can easily scan it with their phones. Very useful if you're onboarding your favourite local merchant so that they can receive Lightning tips!

Simply share the link to your `Sharable Page`, 

or print the QR code as a PDF by going to `View Link` > `Print`. 
