### What is Cashu?
[Cashu](https://cashu.space/) is an open-source ecash protocol for Bitcoin that offers instant, zero fee transactions with near-perfect privacy. See our [explainer] for details. 
### Nutstash
[Nutstash](https://github.com/gandlafbtc/nutstash-wallet) is an awesome web based Cashu wallet by nostr:npub1cj6ndx5akfazux7f0vjl4fyx9k0ulf682p437fe03a9ndwqjm0tqj886t6 that implements most of the [NUTs](https://github.com/cashubtc/nuts/), as well as sending and receiving over nostr. You can also install it as a Progressive Web App (PWA) on your phone. 

⚠️ Nutstash and Cashu are still in beta. Loss of funds is possible. Read about the risks before you use the app. Test with small amounts you are comfortable with losing. 
### Try it
We will walk through how to interact with a mint, receiving and sending ecash, backups, cashing out to Lightning and swapping between mints, at the end we will test out the nostr contacts functionality. 
#### Adding a mint
In order to interact with ecash, you first need to have access to a mint, where your ecash tokens are minted and redeemed. 

1. Head to the [Txoko Mint](https://bitcointxoko.com/cashu/mint/dMk78c5aR7uhHzcqH3Bwqp). 
2. Open the mint in Nutstash. 

💡 You can add additional mints in Nutstash by going to `Mint`, pasting the mint host URL and pressing `Add Mint`. Some public mints can be found at [MintIndex](https://mintindex.gandlaf.com/). Note that some mints will reserve a certain amount of sats to pay for routing fees, meaning that you cannot withdraw all of your sats.
#### Minting tokens
You can fund your ecash wallet either by receiving ecash directly or minting new ecash tokens by paying a Lightning invoice. 

1. In the `Mint` tab, choose the mint where you want to mint new tokens at, and press `Mint`. 
2. Choose an amount. Try a small amount like 100 sats. 
3. Create the invoice and pay it from a Lightning wallet. Once the invoice has been paid, you should now have ecash tokens. 
#### Transacting with ecash
Transacting on ecash is basically sending and receiving blobs of data. As such, you can test these functionalities by sending and receiving to yourself. 

1. To send ecash, go to `Wallet` > `Send`. 
2. Select the mint you want to send from. 
3. Choose an amount. Optionally use coin selection. 
4. Click on send tokens. 
5. Copy the token. 

At this point you can either send the token to someone else, or redeem it in your own wallet. Since we are just testing things out, we will do the latter. 

1. To receive ecash, click on `Wallet` > `Receive`. 
2. Paste the cashu token. 
3. Click on `Receive`. 

💡 You can check pending ecash tokens and reclaim them if the recipient has not redeemed them yet. To do this, go to the `Wallets` tab and look under `Tokens`. Make sure the `Pending` column is checked. There should be a list of pending tokens, click on the refresh button to check their status. If they are unclaimed, you can copy and redeem the token. 
#### Multimint swaps
You might have wondered if different mints can send and receive from each other. The answer is yes. Well, kind of. Instead of sending cashu tokens to one another, transactions between mints fall back to Lightning. To test this out, you can add another mint if you haven't already, for example the LNbits [mint](https://legend.lnbits.com/cashu/mint/4gr9Xcmz3XEkUNwiBiQGoC). But note that some mints will reserve a certain amount of sats to pay for routing fees, meaning that you cannot withdraw all of your sats. To get around this, you can also create your own mint with your Bitcoin Txoko LNbits wallet by activating the Cashu extension. Bitcoin Txoko doesn't require any reserves so you can withdraw all of your sats. 

1. Go to the `Mint` tab and add a new mint if you haven't already done so. 
2. Once you have multiple mints, the option `Inter-Mint Swap` will be available to you. Open the option and read the warning. 
3. If you want to proceed, choose a mint to **swap out** of and a mint to **swap into**. 
4. Choose an amount
5. `Confirm amount`, check the estimated routing fees, and proceed to `Swap`. 

Now in the background the sending mint is paying a Lightning invoice from the receiving mint. Once the invoice is settled, the swapped token should show up in your wallet balance at the receiving mint. 
#### Cash out
When you want to convert your cashu sats back to Lightning sats, you can cash out or "melt" your cashu tokens. 

1. Click on `Pay`, or tap on the camera icon to scan a QR code. 
2. Enter or scan an invoice. 
3. Optionally use coin selection. 
4. Press `Pay`. 

The mint melts the cashu tokens and pays the Lightning invoice. 
#### Backups
Backing up cashu tokens is probably different to the process you might be used to for backing up Bitcoin and Lightning wallets. Since the funds are represented by tokens which are just blobs of data, you are just backing up these pieces of data when you back up cashu tokens. This also means that your backups will change every time you make a transaction and you would need to make a new backup after each transaction. 

Different wallet clients have implemented backups differently and will only work with the same wallet that has created the backup. Nutstash uses a json file as a backup, which also includes your transaction history along with the mints you have added. 

1. To download the backup json, go to `Settings` > `Backup Tokens`, download the json file and save it in a safe place. 
2. To restore the backup, go to `Settings` > `Restore`. Read the warning. Your current wallet data will be overwritten. 
#### Nostr
Since you can send Cashu tokens over any text-based protocol, Nostr is a great match for Cashu. Nutstash makes sending Cashu tokens over Nostr super easy. 

First, you need to connect an external nostr signer to Nutstash so that Nutstash can encrypt and sign direct messages used to send ecash tokens. To do this, 

1. Go to the `Settings` tab and find the `Nostr` section. 
2. Turn on `Nostr`. 
3. You can `Configure` relays manually, or let Nutstash read your relay list after completing the next step. 
4. Turn on `Use external key`. You need to have a Nostr signer extension installed in your browser. Some good options are [nos2x](https://chrome.google.com/webstore/detail/nos2x/kpgefcfmnafjgpblomihpgmejjdanjjp), [Alby](https://getalby.com/#alby-extension) and [Nostore](https://apps.apple.com/us/app/nostore/id1666553677) (for Safari on iOS). 
5. Once Nutstash detects your signer extension, allow it to read your relay list and public key. 
6. If you allow Nutstash to decrypt messages, it will look for Cashu tokens in your direct messages. Once found, these will show up in the `Wallet` tab under `Inbox`. There, you can redeem them to your wallet.  

To send Cashu over Nostr, 
1. Go to `Send`. 
2. Choose a mint. 
3. Choose an amount. Optionally use coin selection. 
4. Press `Send`. 
5. Under `Send via Nostr` enter a npub, hex or NIP-05 nostr address. Alternatively scan someone's profile QR code. 
6. Press `Send over Nostr` and sign the kind 4 message with your external signer. 
7. Tell the recipient to check their inbox, they should have some Cashu waiting for them there!
### Conclusion
Did you find this guide helpful? Try sending us some Cashu tokens over nostr! 
