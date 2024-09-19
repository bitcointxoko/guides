LNDhub allows you to easily import a wallet into compatible applications. While you can save your Bitcoin Txoko LNbits wallet to your phone as a progressive web app (PWA), a native app like [Zeus](https://zeusln.app/) or [BlueWallet](https://bluewallet.io/) offers a better user experience and better security. With [Alby](https://getalby.com/), you can also import the wallet into your browser extension for easy Lightning payments on the web and for Nostr zaps. Luckily for us, these wallets all speak a common language called [LNDhub](https://github.com/BlueWallet/LndHub/tree/master). 

In this guide, we will cover how to import the wallet into your browser and your phone. If you want to use your wallet in both the browser and on your phone, start with the [Alby setup](#Alby), as one of the steps will easily allow you to import your wallet into Zeus as well. But if you are only interested in using the wallet on your phone, you can skip straight to the [Zeus section](#Zeus). 
### Alby
nprofile1qqsyv47lazt9h6ycp2fsw270khje5egjgsrdkrupjg27u796g7f5k0s8jq7y6 is a browser extension that brings Lightning and Nostr to your browser. Using the [WebLN](https://www.webln.dev/) protocol, the extension can easily detect invoices on webpages and pay them as well as let you sign into websites with Lightning. You can also set budgets for your favourite Lightning sites. Furthermore, it can act as a Nostr signer using [NIP-07](https://github.com/nostr-protocol/nips/blob/master/07.md), which is much more secure than entering your private key into web clients. 
#### What do I need? 
- Web browser that supports Chrome or Firefox extensions. 
- Access to your LNbits wallet. If you do not have a LNbits wallet yet, head over to [our wallet page](https://bitcointxoko.com) and create one. 
- (Optional) A mobile device for setting up Zeus. 
#### 1. Enable the LNDhub extension on your LNbits wallet
In your browser, head over to your wallet link. Click on `Extensions` and enable the `LNDhub` extension. After it has been enabled, go to the LNDhub extension page. 
#### 2. Install Alby extension
Head over to [getalby.com](https://getalby.com/) and click on `Add Browser Extension`. Install the extension from your browser's extension store. Set up your unlock password and store it in a safe place. 
#### 3. Import into Alby
![alby-config](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/lndhub/alby-config.png)

In the next screen, choose `Connect`, then choose `LNDhub`. Go back to your LNDhub extension and copy the connection URL. Paste that into the `LNDhub export URI` field. Press continue. You should now have been connected to your LNbits wallet with LNDhub!

💡 You can choose between invoice URL and admin URL. They give Alby different permissions to interact with your LNbits wallet. 
- Invoice URL allows you to generate invoices and receive payments. 
- Admin URL also allows you to send payments. 
#### 4. (Optional) Set up Zeus with Alby
![alby-export](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/lndhub/alby-export.png)

Now that you have connected your LNbits with Alby, you can also easily import it into Zeus with Alby. Simply open the extension, click on your wallet name, and go to Account Settings. Under ``Account`` you can find the option to `Connect your mobile wallet`. When you press `Connect`, you will be shown a QR code to scan from Zeus. 

If you haven't installed Zeus previously, go to [zeusln.app](https://zeusln.app/) and download Zeus for your mobile operating system. 

Once Zeus has been downloaded, go to `Settings` > `Add a new node`. Here you can scan the QR code that Alby is showing to import the wallet. 

Voilà! Now you have the power of Lightning at your fingertips. Do you feel like a god yet?

### Zeus
nprofile1qqsrf5h4ya83jk8u6t9jgc76h6kalz3plp9vusjpm2ygqgalqhxgp9g84ctjf is an awesome open-source app that allows you to connect your own node to your mobile device. It supports all the major Lightning node implementations, such as LND, CLN and Eclair, as well as connections over both Tor and clearnet. Recently they have also announced their own LSP (Lightning Service Provider), you can join the waitlist [here](https://olympusln.com/). 
#### What do I need?
- Android or iOS phone
- Another device on which you can access your LNbits wallet (for displaying the QR code to scan)
- Access to your LNbits wallet. If you do not have a LNbits wallet yet, head over to [our wallet page](https://bitcointxoko.com) and create one. 
#### 1. Download Zeus
You can download the Zeus app for your operating system [here](https://zeusln.app/).
#### 2. Enable the LNDhub extension on your LNbits wallet
In your LNbits wallet page, click on `Extensions` and enable the `LNDhub` extension. After it has been enabled, open the LNDhub extension page. 
#### 3. Import into Zeus
Go to `Settings` > `Add a new node` on Zeus.

Scan the desired wallet to import it. 

💡 You can choose between invoice URL and admin URL. 
- Invoice URL allows you to generate invoices and receive payments. 
- Admin URL also allows you to send payments. 

Once you have scanned the QR code, all the fields should be automatically filled in Zeus. You can add a nickname for your wallet as well. 

![zeus-config](https://github.com/bitcointxoko/guides/blob/main/images/lndhub/zeus-config.png)

Now you can `Save Node Config` and control the wallet from your phone!
#### Bonus
Zeus also offers cool features such as custom themes, price conversions, lurker mode and biometric verification. These are beyond the scope of this guide, play around in the app and discover all those features for yourself!
