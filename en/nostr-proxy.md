Connecting to many nostr relays can quickly drain your battery and bandwidth, especially if you are using nostr on your phone. Proxying your relay connections through a nostr proxy can reduce bandwidth and battery consumption and comes with the additional privacy benefit of hiding your real IP address from the relays. 
### How does it work?

A nostr proxy connects to a bunch of relays. It fetches and publishes events to those relays. The client app only needs to open one websocket connection towards the proxy to access all the relays the proxy is connected to. 

Since the client only opens one connection instead of many, it saves bandwidth and battery. 

As the proxy connects to the relays on the behalf of the client, the IP address of the proxy is exposed to the relays instead of the client's. (Although you still need to trust your proxy provider). 
### How to use it

A nostr proxy can easily be self hosted. Check out this [repo](https://github.com/Dolu89/nostr-proxy) for self-hosting instructions. 

For those of us who do not have the resources to self-host, Bitcoin Txoko hosts a [community instance](https://nproxy.bitcointxoko.com). 

![nostr-proxy](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/nostr-proxy/nostr-proxy.png)

As you can see, it is connected to some of the most popular relays. 

To use it, simply add 

```
wss://nproxy.bitcointxoko.com
```

to your relay list. 

You can also remove the redundant relays now that you no longer need direct connections to them. 

That's it. Happy zapping and see you on nostr!
