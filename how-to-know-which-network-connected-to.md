# How to know which network connected to

The VeChain network is defined and identified by genesis block ID. [VeChain Thor golang implementation](https://github.com/vechain/thor) pre-defines 3 networks: **mainnet**, **testnet** and **solo**. 

|Network|Genesis ID|
| - | - |
| Mainnet| `0x00000000851caf3cfdb6e899cf5958bfb1ac3413d346d43539627e6be7ec1b4a` |
| Testnet | `0x000000000b2bce3c70bc649a02749e8687721b09ed2e15997f466536b20bb127` |
| Solo | `0x00000000973ceb7f343a58b08f0693d6701a5fd354ff73d7058af3fba222aea4` |


[![asciicast](https://asciinema.org/a/261762.svg)](https://asciinema.org/a/261762?autoplay=1)


To get genesis block ID, type command `connex.thor.genesis.id` or shorter `thor.genesis.id`.

```sh
Testnet(100%)> thor.genesis.id
'0x000000000b2bce3c70bc649a02749e8687721b09ed2e15997f466536b20bb127'
```
