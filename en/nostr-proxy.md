Connecting to many nostr relays can quickly drain your battery and bandwidth, especially if you are using nostr on your phone. Proxying your relay connections through a nostr proxy can reduce bandwidth and battery consumption and comes with the additional privacy benefit of hiding your real IP address from the relays. 
### How does it work?

A nostr proxy connects to a bunch of relays. It fetches and publishes events to those relays. The client app only needs to open one websocket connection towards the proxy to access all the relays the proxy is connected to. 

![bostr](https://github.com/Yonle/bostr/blob/master/img/how_it_works.png?raw=true)
*Image courtesy of nostr:npub1x3azxuysp5vmfer4vgs4jn5tmfcx4ew8sh0qnev7gczljxsr7jwqa3g4el 2023*

Since the client only opens one connection instead of many, it saves bandwidth and battery. 

As the proxy connects to the relays on the behalf of the client, the IP address of the proxy is exposed to the relays instead of the client's. (Although you still need to trust your proxy provider). 

### How to use it

A nostr proxy can easily be self hosted. Check out this [repo](https://github.com/Yonle/bostr/) by nostr:npub1x3azxuysp5vmfer4vgs4jn5tmfcx4ew8sh0qnev7gczljxsr7jwqa3g4el for self-hosting instructions. 

For those of us who do not have the resources to self-host, Bitcoin Txoko hosts a [community instance](https://bostr.bitcointxoko.com). 

To use it, simply add 

```
wss://bostr.bitcointxoko.com
```

to your relay list. 

You can also remove the redundant relays now that you no longer need direct connections to them. 

That's it. Happy zapping and see you on nostr!

---
The bostr.bitcointxoko.com community service is distributed with the following copyright notice. 

Copyright 2023 Yonle [yonle@lecturify.net](mailto:yonle@lecturify.net)

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
    
2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
    
3. Neither the name of the copyright holder nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
    

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

---
The following information is outdated. The nproxy community instance is no longer maintained. Use at your own risk. Many thanks to nostr:npub1gzuushllat7pet0ccv9yuhygvc8ldeyhrgxuwg744dn5khnpk3gs3ea5ds for his correction. 

*A nostr proxy can easily be self hosted. Check out this [repo](https://github.com/Dolu89/nostr-proxy) by nostr:npub1txukm7xckhnxkwu450sm59vh2znwm45mewaps4awkef2tvsgh4vsf7phrl for self-hosting instructions.* 

*For those of us who do not have the resources to self-host, Bitcoin Txoko hosts a [community instance](https://nproxy.bitcointxoko.com).*

![nostr-proxy](https://raw.githubusercontent.com/bitcointxoko/guides/main/images/nostr-proxy/instance.png)

*To use it, simply add* 

```
wss://nproxy.bitcointxoko.com
```

*to your relay list.*
