[Bitcoin Connnect](https://bitcoin-connect.com/) is an easy way to connect lightning wallets to websites on any browser using WebLN. This can be especially useful on mobile browsers that do not allow you to install extensions. 

nostr:nevent1qqs9h5lk24vu4ms9s873d8yvmwzs90h37zn68ck0krj886fe89vgdrcpz4mhxue69uhhyetvv9ujuerpd46hxtnfduhszxthwden5te0wfjkccte9eekummjwsh8xmmrd9skctcpzamhxue69uhkzarvv9ejumn0wd68ytnvv9hxgtcpzamhxue69uhhyetvv9ujuurjd9kkzmpwdejhgtcppemhxue69uhkummn9ekx7mp0qythwumn8ghj7un9d3shjtnwdaehgu3wvfskuep0qywhwumn8ghj7mn0wd68ytnzd96xxmmfdejhytnnda3kjctv9uq3zamnwvaz7tmwdaehgu3wwa5kuef0qyfhwumn8ghj7ur4wfcxcetsv9njuetn9uq3yamnwvaz7tmsw4e8qmr9wpskwtn9wv4drcwx

Bitcoin Connect can connect a number of different types of Lightning wallets, from Nostr Wallet Connect (NWC, [NIP-47](https://github.com/nostr-protocol/nips/blob/master/47.md)) to using your own node. Let's try it!

## Create a zap wallet

If you are new to Bitcoin Txoko, first create a wallet at [bitcointxoko.com](https://bitcointxoko.com). 

Since there is a certain degree of trust in the website and that there are no malicious third party scripts reading the connection from storage or memory, it would be wise to configure a separate wallet for use with Bitcoin Connect with its own budget instead of linking your main wallet. Fortunately, this only takes two clicks on LNbits. Simply click on `+ Add a new wallet` in the toolbar, name the wallet and create it. Transfer a small zapping budget into the newly created wallet. 

Once you have a wallet ready, find the `API docs` section and make a note of your *admin key*. We will need it later to connect this wallet using Bitcoin Connect. 

![adminkey](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/bitcoin-connect/adminkey.png)

## noStrudel

A number of web apps, especially in the Nostr ecosystem, have already implemented Bitcoin Connect as a wallet connection method, including [Habla](https://habla.news/), [Snort](https://snort.social/)/[Iris](https://iris.to/) and [Zap.stream](https://zap.stream/), and more are sure to follow. However, as far as I am aware, [noStrudel](https://nostrudel.ninja/) is the only one to allow using Bitcoin Connect with a [LNbits](https://lnbits.com/) wallet. 

If you are unfamiliar with it, noStrudel is a Nostr web client for power users with support for a wide range of NIPs and can be installed as a Progressive Web App (PWA). A killer feature is that it also supports Nostr Connect ([NIP-46](https://github.com/nostr-protocol/nips/blob/master/46.md)), which allows you to sign in using a server that signs events on your behalf like [nsecbunker](https://nsecbunker.com/). This means that, paired with Bitcoin Connect, you can use it without any extensions, for example, on mobile browsers. 

## Trying Bitcoin Connect

1. Navigate to [nostrudel.ninja](https://nostrudel.ninja) (or [nostrudel.bitcointxoko.com](https://nostrudel.bitcointxoko.com) for our community instance) and sign in with your preferred method. 
2. Go to `Settings` and find the `Lightning` section. 
3. Tap on `Connect Wallet`. 
4. Choose `LNbits` as your connection method. Note that you can also use NWC or a number of other connection methods. 
5. Enter the *admin key* you have noted down earlier and `https://bitcointxoko.com` as the LNbits URL. Connect the wallet. 
6. You should now see your wallet balance. You are now ready to zap!

![nostrudel]

## Conclusion

We think the combination of Bitcoin Connect and Nostr Connect overcomes a big user experience hurdle when it comes to using Nostr clients on mobile. Not only are mobile users are no longer dependent on fiddly extensions like Alby, but also allows web clients to compete with native clients which often lag in development and lack certain features. 

We hope you found this short guide useful. If you did, try zapping this article with your newly connected wallet!
