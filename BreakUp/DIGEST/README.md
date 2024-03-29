### Account
    local: private key(+ secret)
    statedb: public key ?
    tx: sign
    {"address":"4e264f45edcf2edd9b0b0b49afb8d800b5ea6eeb",
    "crypto":{
    "cipher":"aes-128-ctr",
    "ciphertext":"f72922a1930420814ae03eabad825a7c78613797c0da49184dfecee6513a0c2c",
    "cipherparams":{"iv":"a20f292da98632bdc4f52bbdc1852f63"},
    "kdf":"scrypt",
    "kdfparams":{"dklen":32,"n":262144,"p":1,"r":8,"salt":"769900ba1b0df0ae69f647c182e89dbd0444c47bc948be1f9b5d108f2321ccb1"},
    "mac":"6458c4e37055aa60a5ffd92347345b5500a3c03c2a195d8ea650da6de20ffd5a"},
    "id":"309ccfe5-e1bf-4f62-9847-f76df4340c65",
    "version":3}
### TX
    tx =  tx data + sign
### Block
    Linked List + Merkle Tree(tx) + Patricia Tree(State)
    Block Hash = Block Header Hash
    block header: 200 byte
                  timestamp, nonce, previous block hash, root hash of merkle tree over txs
    block: 70 txs
   Metrics               | Bitcoin  |Ethereum               | TrueChain|Notes
  -----------------------|:--------:|:---------------------:|:--------:|-----
  tx per blk             |1500~2000 |   70                  |          | 
  blk size               |1MegaByte |  1,500,000 wei        |          | Avg Gas per tx: 21,000
  blk time               |    600s  |   15s                 |          | 
  blk reward             | 12.5BTC  |  5ETH+                |          | 
  confirm time           | 6 blks   |                       |          | 
  blks per hour(total)   | 6 blks   | 250 blks              |          |
 blks per hour(discarded)|          | 250 blks              |          |
  uncle counts           |          | 1~2                   |          |
  blk data content       |  tx list |tx list + mrecent state|          |
  tx data                | blk      | blk - Merkle Tree     |          |
  state(UTXO)            | statedb  | blk - Patricia Tree   |          |
  execute/validate       | All Nodes| All Nodes             |          |
  
### [Tries](https://hackernoon.com/getting-deep-into-ethereum-how-data-is-stored-in-ethereum-e3f669d96033)

  ![know](https://i.stack.imgur.com/QpcFh.png)
  
    ------------------
    |    block N     |
    |    tx Root     |<------ Tx Trie
    |    state Root  |<------ State Trie <--------- Storage Trie
    |  receipts Root |<------ Receipts Trie
    ------------------
             |
    ------------------
    |    block N-1   |
    |    tx Root     |
    |    tx Root     |
    |    tx Root     |
    ------------------
   
   Data Type   | key                 | value                | Trie Type      | Existence
  -------------|:-------------------:|:--------------------:|:--------------:|:---------------
  permanent    |                     | transaction          |   tx trie      | local(one per block)
  permanent    |                     | transaction          | receipts trie  | local(one per block)
  ephemeral    |   addr 160bit ID    | account balance      |   state trie   | global(one and only)
  ephemeral    |                     | account nonce        |   state trie   | 
  X            |                     |     code hash        |   state trie   | 
  X            |                     |    storage root      |   state trie   |
  X            | keccak 256bit hash  | contract storage root|   storage trie |     
 
  - Q: trie is (key,value). got it. how to be treed?
    * A:  
### DAG

### TD
    TD(N) = TD(N-1) + sum of TD(uncles) + D(N)
### D
