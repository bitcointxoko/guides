### What is Cashu?
[Cashu](https://cashu.space/) is an open-source ecash protocol for Bitcoin that offers instant, zero fee transactions with near-perfect privacy. See our [explainer] for details. 
### eNuts
[eNuts](https://www.enuts.cash/) is an excellent mobile wallet client for cashu, available on both Android and iOS (TestFlight). It supports multiple mints as well as sending over nostr. 

⚠️ eNuts and Cashu are still in beta. Loss of funds is possible. Read about the risks when you install the app. Test with small amounts you are comfortable with losing. 
### Try it
We will walk through how to interact with a mint, receiving and sending ecash, backups, cashing out to Lightning and swapping between mints, at the end we will test out the nostr contacts functionality. 
#### Install
Head to the [eNuts](https://www.enuts.cash/) website and install the application for your operating system. 
#### Adding a mint
In order to interact with ecash, you first need to have access to a **mint**, where your ecash tokens are minted and redeemed. The mint is the custodian of your Bitcoin but does not know who you are, who you are transacting with nor how much funds you have. You can use the Txoko mint for testing. 

1. Head to the [Txoko Mint](https://bitcointxoko.com/cashu/mint/dMk78c5aR7uhHzcqH3Bwqp). Copy the mint URL. 
2. In eNuts, go to `Options` > `Mint management` and press the `+` button. Paste the mint URL you have copied from the previous step. 

💡 You can add additional mints. Some public mints can be found at [MintIndex](https://mintindex.gandlaf.com/). Note that some mints will reserve a certain amount of sats to pay for routing fees, meaning that you cannot withdraw all of your sats.
#### Minting tokens
Once you have added the mint, eNuts will automatically ask you if you want to mint new cashu tokens from that mint. 

1. Answer `Yes`. 
2. Create an invoice for the amount you want to mint. Try a small amount, for example 100 sats. 
4. Pay the invoice from a Lightning wallet. Once the invoice has been paid, you should now have ecash tokens. 
#### Transacting with ecash
Transacting on ecash is basically sending and receiving blobs of data. As such, you can test these functionalities by sending and receiving to yourself. 

1. To send ecash, click on `Send` > `Send Ecash`
2. If using multiple mints, select the mint you want to send from. Then choose `Copy & quickshare`. 
3. Choose an amount. 
4. Optionally add a memo, click `Continue`. 
5. Confirm the payment details and `Create Token`. At this point you can use the `Coin Selection` feature to choose which tokens you want to spend. Notice that the tokens are denominated in 1 sat, 2 sats, 4 sats, 8 sats, 16 sats and so on. You can think of them like 10 euro, 20 euro, 50 euro bills as an example. 
6. Copy the token. 

At this point you can either send the token to someone else, or redeem it in your own wallet. Since we are just testing things out, we will do the latter. 

1. To receive ecash, click on `Receive` > `Paste & redeem Ecash`. eNuts should automatically read your clipboard and redeem the token. 

💡 You can check pending ecash tokens in your transaction history and reclaim them if the recipient has not redeemed them yet. To do this, tap on an outgoing transaction in your transaction history and then `Check if token has been spent`. If the `Token is pending`, you can `Claim token` back to your wallet. 
#### Multimint swaps
You might have wondered if different mints can send and receive from each other. The answer is yes. Well, kind of. Instead of sending cashu tokens to one another, transactions between mints fall back to Lightning since a mint is also a Lightning node. Cashu tokens themselves are not fungible across nodes. To test this out, you can add another mint if you haven't already, for example the cashme LNbits [mint](https://legend.lnbits.com/cashu/mint/4gr9Xcmz3XEkUNwiBiQGoC) or the default eNuts mint. But note that some mints will reserve a certain amount of sats to pay for routing fees, meaning that you cannot withdraw all of your sats. To get around this, you can also create your own mint with your Bitcoin Txoko LNbits wallet by activating the Cashu extension. 

1. Go to `Options` > `Mint management` and select the mint you want to swap **out** from. Then go to `Multimint swap` under `Funds`. 
2. Choose a mint to swap **into**. 
3. Choose an amount and tap on `Estimate fee` to estimate the Lightning fees that may occur. 
4. Click `Continue`. 
5. Check the details and optionally use `Coin selection`, then press `Swap Now`. 

Now in the background the sending mint is paying a Lightning invoice from the receiving mint. Once the invoice is settled, the swapped token should show up in your wallet balance at the receiving mint. 
#### Cash out
When you want to convert your cashu sats back to Lightning sats, you can cash out. 

1. Click on `Send` > `Pay Lightning invoice`
2. Select a mint to send from if using multiple mints. 
3. Under `LN invoice or LNURL`, enter an invoice, LNURL or Lightning Address; or simply scan a QR code. 
4. Choose amount and `Estimate fee`.
6. Check the details before pressing `Cash out`. 

The mint redeems the cashu tokens and pays the Lightning invoice. 
#### Backups
Backing up cashu tokens is probably different to the process you might be used to for backing up Bitcoin and Lightning wallets. Since the funds are represented by tokens which are just blobs of data, you are just backing up these pieces of data when you back up cashu tokens. This also means that your backups will change every time you make a transaction. Different wallet clients have implemented backups differently and will only work with the same wallet that has created the backup. 

eNuts creates a cashu token with all your funds in it and which mint they belong to. 

- To create a backup, go to `Options` > `Security` > `Create a backup token`. Copy the token and save it in a safe place. 

Alternatively, you can back up each of your mints individually. 

- To do this, go to `Options` > `Mint management` and select the mint you want to back up. Go to `Backup funds`, copy the token and save it in a safe place. 

To restore, simply copy the backup token and open the eNuts app. The app should read your clipboard and ask if you want to restore the token. 
#### Nostr
eNuts integrates Nostr to allow you to send ecash to your contact list. 

To use this feature, go to `Contacts` and paste your nostr public key. eNuts then pulls your contacts list from relays. Unfortunately the search function has not been implemented yet, which can make finding the correct contact a bit cumbersome if you have many contacts. 

The recipient should get a Nostr kind 4 direct message containing the cashu token which they can redeem in their wallet. 
