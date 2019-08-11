# How to know the best block?

The best block, aka latest block, or highest block, is the most recent produced block.
It can be found by a simple command `connex.thor.status`, or just `thor.status` in **Connex Playground**.

[![asciicast](https://asciinema.org/a/261847.svg)](https://asciinema.org/a/261847?autoplay=1)

```sh
Testnet(100%)> thor.status
{ head:
   { id:
      '0x00362f551c8da113c9917f06b40c3c2c9255ea131e28dcfd7a2f71e4f45aedd6',
     number: 3551061,
     timestamp: 1565539290,
     parentID:
      '0x00362f54d5c4ccd6ea84c98a57c4d46138cd0c580d76285d0aa6639459bf9f71',
     txsFeatures: 1 },
  progress: 1 }
```

Where *head* property is the summary of currently known best block, and *progress* is the synchronization progress of connected node. When *progress* equals to 1, means the node is fully synchronized.

