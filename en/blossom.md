## What is Blossom?

nostr:nevent1qqspttj39n6ld4plhn4e2mq3utxpju93u4k7w33l3ehxyf0g9lh3f0qpzpmhxue69uhkummnw3ezuamfdejsygzenanl0hmkjnrq8fksvdhpt67xzrdh0h8agltwt5znsmvzr7e74ywgmr72

[Blossom](https://github.com/hzrd149/blossom) stands for _Blobs Simply Stored on Mediaservers_. _Blobs_ are chunks of binary data, like files but without names. Instead of names, they have are identified by their [sha256](https://en.wikipedia.org/wiki/SHA-2) hash. The advantage of using sha256 hashes instead of names is that the hashes are universal IDs that can be computed from the file itself using the sha256 hashing algorithm.

💡 file -> sha256 -> hash

Blossom is therefore a set of HTTP endpoints that allow users to store and retrieve blobs stored on servers using their nostr identity.

## Why Blossom?

As we alluded to just now, by using nostr keys as their identity, Blossom allows data to be "owned" by the user. This greatly simplifies the question of "what is spam" for server hosting. For example, on our Blossom we only allow uploads by verified community members that have a [NIP-05](nips.nostr.com/5) with us.

Users can upload to multiple blossom servers, for example, one hosted by their community, one paid, another public and free, to establish redundancy of their data. Blobs can be [mirrored](https://github.com/hzrd149/blossom/blob/master/buds/04.md) between blossom servers, much like how nostr relays can stream events to each other. This further improves the censorship resistance of blossom.

Below is a brief comparison table comparing torrents, Blossom and centralised CDN servers. (Assuming plentiful seeders for torrents and multiple servers are used with Blossom).

|                                                    | Torrents | Blossom | Centralised CDN |
| -------------------------------------------------- | -------- | ------- | --------------- |
| Decentralised                                      | ✅       | ✅      | ❌              |
| Censorship-resistance                              | ✅       | ✅      | ❌              |
| Can I use it to post cat pictures on social media? | ❌       | ✅      | ✅              |

## How does it work?

Blossom uses several nostr event kinds to communicate with the mediaserver.

| kind  | description         | BUD                                                                |
| ----- | ------------------- | ------------------------------------------------------------------ |
| 24242 | Authorisation event | [BUD01](https://github.com/hzrd149/blossom/blob/master/buds/01.md) |
| 10063 | User Server List    | [BUD03](https://github.com/hzrd149/blossom/blob/master/buds/03.md) |

### kind:24242 - Authorisation

This is essentially what we already described with using nostr keys as user IDs. In the event, the user tells the server they want to upload or delete a file and sign it with their nostr keys. The server makes a few checks on this event and then executes the user's command if everything looks good.

### kind:10063 - User Server List

This is used by the user to advertise which mediaservers they are uploading to. This way, when the client sees this list, it knows where to upload the user's files. It may also upload to multiple servers defined in the list to ensure redundancy. On the retrieval side, if for some reason one of the servers in the user's list is down, or the file can no longer be found there, the client can use this list to try to retrieve the file from other servers on the list. Since blobs are identified by their hashes, the same blob will have the same hash on any mediaserver. All the client needs to do is swap out the url for a different server.

Now, aside from the basics of how Blossom works, there are also some other event kinds that make Blossom even more interesting.

| kind  | description    |
| ----- | -------------- |
| 30563 | Blossom Drives |
| 36363 | Server Listing |
| 31963 | Server Review  |

### kind:30563 - Blossom Drives

This event kind makes it easy to organise blobs into folders, like we are used to with cloud drives (think Google Drive, iCloud, Proton Drive etc). The event contains information about the folder structure and metadata of the drive.

### kind:36363 and kind:31963 - Listing and Review

These event kinds allow users to discover and review media servers over nostr. kind:36363 is a server listing containing the url of the server. kind:31963 is a review, where the users can rate servers.

## How do I use it?

### Find yourself a server

First you will need to choose a Blossom server where you will be uploading your files. You can browse the public ones at [blossomservers.com](https://blossomservers.com/). Some of them are paid, others might require your nostr keys to be whitelisted.

Then, you can head over to their server url and try uploading a small file, like a photo. If you're happy with the server (it's fast and hasn't rugged you yet), you can add it to your User Server List. We'll briefly cover how to do this in noStrudel and Amethyst (but you only need to do this once, once your up-to-date list is published, clients can just retrieve it from nostr).

### noStrudel

1. Find Relays in the sidebar, then choose Media Servers.
2. Add a media server, or even better, several.
3. Publish your server list. ✅

### Amethyst

1. In the sidebar, find Media Servers.
2. Under Blossom Servers, add your media servers.
3. Sign and publish. ✅

Now when you go to make a post and attach a photo, for example, it will upload to your blossom server.

### Blossom Drive

As we mentioned earlier, we can publish events to organise our blobs into folders. This can be great for sharing files with your team, or just for keeping things organised.

To try it out, go to [blossom.hzrd149.com](https://blossom.hzrd149.com/) (or our community instance at [blossom.bitcointxoko.com](https://blossom.bitcointxoko.com)) and sign in with your preferred method.

You can create a new drive and add blobs to it from there.

### Bouquet

If you use multiple servers to give yourself redundancy, Bouquet is a nice way to get an overview of all your files. Use it to upload and browse your media on different servers and sync blobs between them.

### Cherry Tree

nostr:nevent1qvzqqqqqqypzqfngzhsvjggdlgeycm96x4emzjlwf8dyyzdfg4hefp89zpkdgz99qyghwumn8ghj7mn0wd68ytnhd9hx2tcpzfmhxue69uhkummnw3e82efwvdhk6tcqyp3065hj9zellakecetfflkgudm5n6xcc9dnetfeacnq90y3yxa5z5gk2q6

Cherry Tree allows you to split a file into chunks then upload them to multiple blossom servers, and later reassemble them somewhere else.

## Conclusion

Blossom is still in development but there are already lots of cool things you can do with it to make yourself and your community more sovereign. Give it a try!

If you'd like to stay up-to-date on Blossom development, follow nostr:nprofile1qyghwumn8ghj7mn0wd68ytnhd9hx2tcpzfmhxue69uhkummnw3e82efwvdhk6tcqyqnxs90qeyssm73jf3kt5dtnk997ujw6ggy6j3t0jjzw2yrv6sy22ysu5ka and give him a big fat zap for his fine work.

## References

- [hzrd149/blossom on GitHub](https://github.com/hzrd149/blossom)
- [Blossom Drive](https://github.com/hzrd149/blossom-drive/blob/master/docs/drive.md)
