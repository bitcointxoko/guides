Nostr proxy baten erabilera modu oso eraginkorra da internet banda-zabaleraren eta mugikorretan bateriaren kontsumoa optimizatzeko.

Proxy batek hainbat errelei-konexio konexio bakarrean biltzen dituenez, baliabideen erabilera nabarmen murrizten du, eta erabiltzailearen IP helbidea ezkutatuz pribatutasun-geruza bat gehitzen du.

Hona hemen nola funtzionatzen duen eta nola konfigura daitekeen:

### Nola funtzionatzen du?

Nostr proxy batek hainbat erreleirekin konektatzen du. Errele horietara gertaerak eskuratu eta argitaratzen ditu. Bezeroaren aplikazioak WebSocket konexio bakarra ireki behar du proxy-ra, eta horren bidez proxy-ak konektatuta dituen errele guztiak eskuragarri izango ditu.

![bostr](https://github.com/Yonle/bostr/blob/master/img/how_it_works.png?raw=true)

*Irudiaren egiletza: nostr:npub1x3azxuysp5vmfer4vgs4jn5tmfcx4ew8sh0qnev7gczljxsr7jwqa3g4el 2023*

Bezeroak konexio bakarra irekitzen duenez, datuak eta bateria aurrezten ditu.

Proxy-ak bezeroaren izenean erreleekin konektatzen denez, erreleek proxy-aren IP helbidea ikusten dute, eta ez bezeroarena. (Hala ere, proxy hornitzailearengan konfiantza izan behar duzu).

### Erabiltzeko Modua

Nostr proxy bat erraz auto-ostata daiteke. Auto-ostatatzeko jarraibideak lortzeko, begiratu nostr:npub1x3azxuysp5vmfer4vgs4jn5tmfcx4ew8sh0qnev7gczljxsr7jwqa3g4el erabiltzailearen [biltegi](https://github.com/Yonle/bostr/) hau.

Auto-ostatzeko baliabiderik ez dutenentzat, [Bitcoin Txoko-k komunitate-instantzia](https://bostr.bitcointxoko.com) bat ostalaratzen du.

Erabiltzeko, gehitu besterik ez duzu:

```
wss://bostr.bitcointxoko.com
```

zure errele zerrendara. 

Orain ez duzunez zuzeneko konexioak behar, errele bikoiztuak ezabatu ditzakezu.

Ikusiko dugu elkar Nostr-en!
