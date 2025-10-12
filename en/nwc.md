Nostr Wallet Connect (NWC) allows you to easily connect your wallet to a Nostr app, for example for easy one-click zaps.

## Nostr Wallet Connect (NWC)

Nostr Wallet Connect is like a bridge between your Lightning wallet and Nostr apps. It essentially works over three simple steps.

![nwc-flowchart](https://loratu.bitcointxoko.com/3ca8bd26a7b1b0be82778673ccebc9f6b40945f03e307a92d8f671f4937c2fb9.webp)

1. **Set up the connection**: Generate a connection string with your wallet. This connection string contains a public key, relay information, and a secret. This connection string is pasted into the Nostr app you want to use.

2. **Message over relays**: When you want to make a payment in the Nostr app, for example to send a zap, the app sends a request to the relay encrypted with the secret from the previous step. Your wallet listens on the same relay and picks up the request.

3. **Payment**: After receiving the request, the wallet makes the payment. This can be done automatically or require approval.

For more information on NWC, you can check [NIP-47](https://nips.nostr.com/47) or the developer [documentation](https://nwc.dev).

## Set up

Now that we have an understanding of how it works, let's configure some Nostr apps to use our Lightning wallet over NWC with the NWC Service Provider extension in LNbits.

0. **Enable the extension**: In the Extensions section in the sidebar, enable the NWC Service Provider extension. After enabling it, open it.
1. **Select a wallet**: It's a decent idea to create a wallet just for NWC if you want to separate it from your main wallet. You can easily do this by selecting "+ Add a new wallet" in the sidebar.
2. **Add a connection**: Click on the "+" and you can configure your connection settings, or just leave them at the default and add a description so you can later identify the connection. Once you're happy with the settings, click "Connect".
3. **Pairing**: You can now pair the Nostr app by pasting the connection string ("Pairing URL") or scanning the QR code with a compatible app.

That's it! Try it out by sending a zap.
