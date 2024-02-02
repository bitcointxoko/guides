[Mutiny Wallet](https://www.mutinywallet.com/) is an open-source self-custodial Bitcoin and Lightning wallet that works in the browser as well as for native apps on Android and iOS (TestFlight, paid). Not only is it probably the most comfortable way to send self-custody one-tap zaps on nostr, but also the easiest way to onboard new users to self-custodial Bitcoin. In this guide we will dive into how the Mutiny team has made this possible using the magic that is nostr. 

⚠️ Mutiny Wallet is beta software. Use signet coins for testing and do not deposit more funds than you are willing to lose. 
## Run Mutiny
### Web
Mutiny can run a Lightning node in a web browser. How does this work? A simple explanation is that a Lightning node consists of several parts, including the gossip syncer, block explorer, state machine and signer. Mutiny separates these parts such that only the signer is stored locally whilst the other parts are accessed remotely over API. 

To run Mutiny in your browser, simply navigate to https://app.mutinywallet.com. You can then save the page as a Progressive Web App for easy access. In most browsers, this option is either called "Install App" or "Add to Home Screen". 

Alternatively, you can try [Mutiny self-hosted by Bitcoin Txoko](https://mutiny.bitcointxoko.com), but some features like gifting and nostr contacts do not work yet. You can track this [issue](https://github.com/MutinyWallet/mutiny-deploy/issues/5) on GitHub for updates. 

If you do choose to use Bitcoin Txoko, keep in mind that we are only running the frontend, the websockets proxy for connecting to the Lightning Network and the Versioned Storage Service (VSS) for storing Lightning states. For the gossip syncer and block explorer, we recommend you to use the default ones provided by Mutiny. To add them, 
- Navigate to `Settings` > `Servers`. 
- Under `Esplora`, paste in `https://mutiny.mempool.space/api`
- Under `RGS`, paste in `https://scorer.mutinywallet.com/v1/rgs/snapshot/`
- The other fields should be filled in by default, including the LSP. 
- Press `Save`
### Android
The Android APK for Mutiny can be downloaded directly from [GitHub](https://github.com/MutinyWallet/mutiny-web/releases). We recommend using [Obtainium](https://github.com/ImranR98/Obtainium) to manage your Android apps, check out our [Guide]. 
### iOS (TestFlight)
Mutiny Wallet is available for free, but you can also pay for it to unlock features and support its development by subscribing to Mutiny+. 

To subscribe to Mutiny+ you first need to have at least 10500 sats in Lightning balance in your Mutiny Wallet. We will cover funding your wallet later in this guide. After you have funded the wallet, go to `Settings` > `Mutiny+` to subscribe. After you've paid for your subscription, click on the iOS beta access link in the Mutiny+ tab to obtain a TestFlight invite. 
## Funding
The simplest way to start transacting with your Mutiny wallet is to receive a Lightning payment. A channel will be automatically opened for you in this process from the [Voltage Flow 2.0](https://amboss.space/node/03aefa43fbb4009b21a4129d05953974b7dbabbbfb511921410080860fca8ee1f0) LSP. To do this, press `Receive`, carefully read the notice about the minimum channel size and setup fees, then set an amount to receive. Pay the invoice and you should have a channel up and running within minutes. 

Alternatively, you can also send on-chain funds to your Mutiny wallet and open a channel yourself. After the on-chain balance is confirmed, there will be a swap button. Clicking on it allows you to swap it to Lightning. 

💡 With Mutiny you are not locked into using a single node. You can connect Mutiny to another node instead of the default Voltage Flow 2.0 LSP. To connect to the node of your choice, navigate to `Settings` > `Admin Page`. First connect your node as a peer under `Connect Peer` by pasting in the node's address following the `pubkey@address` format, then open a channel to the node entering `Pubkey` and `Amount`. The channel will need to reach 6 confirmations before it can be used. 
## Backup
You can already start transacting with Mutiny once you have loaded up the wallet in your browser or app, but the prudent thing to do would be to secure your funds by making a backup. 

The process for this is simple. Click on `Backup` on the main page and write down the 12 words. You can optionally add a password to encrypt your seed words. 

If you've forgotten your seed words, you can still come back to see them under `Settings` > `Backup`. 
## Nostr
### Zaps
One-tap zaps! This is made possible using [NIP-47 Nostr Wallet Connect (NWC)](https://github.com/nostr-protocol/nips/blob/master/47.md). 

To start using Wallet Connect, 
- Go to `Settings` and `Wallet Connections` under `Beta Features`. 
- Create a new connection with `Add Connection`. 
- Give it a name to remind yourself about what it is for. 
- If you want the true one-tap zap experience, check the box next to `Auto Approve` and set a budget for this wallet connection. Otherwise, you will need to come back to Mutiny to approve the pending transactions manually. 
- Once you are happy with the budget, click on `Create Connection` and you will be shown a QR code. You can either scan it from a Nostr client on a separate device or select `Open in Nostr Client` to open it on the same device. The Nostr client must support NWC for it to work. 
	- On Amethyst, you might need to paste in the different fields separately. 
### Contacts
You can import your npub to see whom your contacts are zapping. Go to `Settings` > `Sync Nostr Contacts`. Introduce your Nostr npub and within seconds you will be able to see your contacts zapping away. 
### Gifting
Mutiny makes onboarding no-coiners easier than ever. If someone can access a web browser, they can be gifted sats. No excuses. What is even better is that the entire process is self-custodial! The only instruction you have to give? Scan the QR code. 

To create a gift, you need to be a Mutiny+ subscriber. Once that's done (and you really should do it, it's a no-brainer), go to `Gifting` under `Beta Features`. Enter a name of the recipient for record keeping and select an amount. After the clicking on `Create a gift`, you will have a QR code and a URL. 

To redeem a gift, the new user simply needs to scan the QR code or open the link in a browser. The LSP will open a channel to them as they redeem the gift. Keep in mind that your wallet needs to be open and online for the recipient to redeem the gift. 

Behind the scenes, this is all using Nostr Wallet Connect. 🤯 The QR code contains the information the recipient needs to create an invoice. The sender's wallet is listening for the invoice from a relay and pays it once it sees it. 

💡 If you are really cheap and don't want to pay for Mutiny+, you can [self-host Mutiny](https://blog.mutinywallet.com/self-hosting-mutiny/). Regardless, we still strongly encourage you to support Mutiny's development. You can zap them here: nostr:npub1mutnyacc9uc4t5mmxvpprwsauj5p2qxq95v4a9j0jxl8wnkfvuyque23vg. 
### Mutiny+
Mutiny built automatic subscription billing over Lightning using... you guessed it, NWC. A subscription is a NWC event, which will create invoices on a monthly basis. Isn't that cool? Furthermore, you can cancel any time you want, just by removing the wallet connection. You can read all about Mutiny's subscription feature [here](https://blog.mutinywallet.com/solving-subscriptions-on-bitcoin-one-zap-at-a-time/). 
## Migrating
There are two options when it comes to migrating your wallet to another device, or migrating from browser to native apps. You can migrate using the state file, which is the recommended method, or you can use your backup seed phrase. Consult the [official guide](https://blog.mutinywallet.com/migrate-mutiny-wallet-to-the-native-apps/) to see all the steps. 
## Conclusion
When Nostr meets Lightning, beautiful things happen. Mutiny Wallet has demonstrated this with one-tap zaps, subscriptions and gifting, all working with Nostr Wallet Connect. 

But wait, that's not all that Mutiny has to offer. There are new exciting features in the pipeline such as RedShift and Synthetic USD. Stay up to date with Mutiny over at [Mutiny Blog](https://blog.mutinywallet.com/). 

Did you find this guide helpful? Try sending us a one-tap zap from your brand new Mutiny wallet. :)
