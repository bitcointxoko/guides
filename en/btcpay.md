Are you a merchant looking to start accepting Bitcoin in your business? Or are you a passionate Bitcoiner who wants to onboard local businesses? Or maybe you don't give two damns about Bitcoin and just want to use a fast and cheap payment processor? If the answer is yes to any of these questions, then this guide is for you. You can set up a store on [BTCPay Server](https://btcpayserver.org/) hosted by Bitcoin Txoko and start selling your goods and services for Bitcoin in under ten minutes, for free. 
## What do I need?
If you have a smartphone or computer with internet access and an email account, then you are good to go!
## Create an account
Creating a BTCPay Server account at Bitcoin Txoko is free. Navigate to https://btcpay.bitcointxoko.com to register an account. Check your inbox for an email from bitcointxoko@gmail.com containing the confirmation link. 
## Create your first store
Clicking on the confirmation link will bring you to the store creation page. Give your store a name and choose the default currency and a preferred price source. For example, you can choose EUR and Kraken, which is the recommended price source. BTCPay Server will convert the price of your goods or services from EUR to Bitcoin using the price source at the time of purchase. 
## Set up a wallet
To start accepting payments, you first need to link a wallet to your store. Unless you are expecting frequent transactions of large amounts (more than 500 EUR), we recommend setting up a Lightning wallet and skip the (on-chain) Bitcoin wallet for now. 

💡 Lightning is the ideal payment settlement network for accepting Bitcoin payments because it offers instant settlement and low fees compared to on-chain transactions. 

The easiest way to connect a Lightning wallet is to use LNDhub because you do not need to run your own Lightning node. If you do not have a LNDhub wallet yet, fear not, Bitcoin Txoko offers free LNDhub wallets and it takes three minutes to set up. Check nostr:naddr1qqxnzd3exuerqdfkxccnyv3cqgs9n8m87l0hd9xxqwndqcmwzh4uvyxmwlw0637kuhg98pkcy8ana2grqsqqqa28nkyu7t on how to get your own LNDhub wallet and come back once you're ready. 

With your LNDhub wallet ready, 
- go to your BTCPay account and look for `Wallets` in the sidebar and select `Lightning`. 
- Choose `Use custom node`. 
- Copy your LNDhub admin URL and paste it in the connection configuration. 
- Test your wallet connection. 
- If it went well, you should get the message `Connection to the Lightning node successful, but no public address has been configured`. You can ignore the part about no public address has been configured, this only applies if you are running your own node. 
- Click `Save` once you've successfully tested the wallet connection. 
- After clicking `Save`, turn off `Enable LNURL` under the `LNRUL` section. Don't forget to click `Save` again after making changes. 
- (Optional) At this point we also recommend checking the box next to `Display Lightning payment amounts in Satoshis` since that is easier to read. A satoshi is the smallest divisible unit of Bitcoin; there are 100 million satoshis in one Bitcoin. 

💡 The set up process is similar if you are using your own Lightning node. Just make sure you provide the correct connection string for your node implementation. 
## Create a Point of Sale
If you've made it to this step, pat yourself on the back because the boring part is over. Now you get to create your Point of Sale (PoS) and start accepting your first Bitcoin payment through BTCPay!

To create your Point of Sale, 
- Go to `Plugins` > `Point of Sale`. 
- Give your Point of Sale a name and hit `Create`. 

We will cover a couple of simple things you can do with your PoS app. Since BTCPay has a lot of features, we will only cover the basics in this guide to help you get started. 

💡 Remember that you can create multiple Points of Sale within BTCPay Server, each for its own use. 
### Keypad
For a simple demonstration, we will first go over the keypad style PoS. 

- Give your PoS a name and a display title. 
- Choose `Keypad` under `Choose Point of Sale style`. 
- Hit `Save` in the top right corner, and then `View` to check it out. 

The payments will be received into the LNDhub wallet you have configured earlier. Play around with generating invoices and the `Discount` and `Tip` options. If you are on a phone that supports it (i.e. not an iPhone), you can also let your customers pay with NFC cards like the BoltCard (see nostr:naddr1qqxnzd3e8qcr2wfn8qcrgwf4qgs9n8m87l0hd9xxqwndqcmwzh4uvyxmwlw0637kuhg98pkcy8ana2grqsqqqa28qjzxr4). How cool is that?

💡 You can save the Keypad PoS as a Progressive Web App (PWA) on your phone for easy access. On most mobile browsers this option is called `Install App` or `Add to Home Screen`. 
### Product list (with cart)
It is also possible to create a Point of Sale app with specific products, each with its own price. You can use this feature to set up a simple cashier, customer self-checkout or web shop. 

- To create a new Point of Sale app, just go back to the sidebar and select `Point of Sale` again. 
- This time, under `Choose Point of Sale Style`, choose `Product list with cart`. The "with cart" option allows the customer to purchase multiple items at once. 
- Create your own products, or go straight to `Save` and `View` the sample products to test things out. 
## Conclusion
In this guide we've covered the basic steps to start accepting Bitcoin in your business using BTCPay Server. BTCPay Server is an [open source project](https://github.com/btcpayserver/btcpayserver) that is constantly evolving. There are many many more features and functionalities within BTCPay Server that you can explore and use, such as Shopify integration, crowdfunding and automatic payment splits. You can also customise your store to your liking with theming, custom checkout appearance, user management, email notification and much more. If you would like to take full advantage of BTCPay Server, we recommend you to consider setting up your own [Lightning node](https://v2.minibolt.info/home/readme) and and [host your own](https://docs.btcpayserver.org/Deployment/) BTCPay Server. Check out their [documentation](https://github.com/btcpayserver/btcpayserver) and [videos](https://www.youtube.com/@BTCPayServer) for more information. 

If you still have questions and doubts, let us know! We would love to hear from you and help answer any related questions. 
