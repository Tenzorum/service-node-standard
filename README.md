## Tenzorum Service Node Architecture
Tenzorum's Smart Contract builds around personal multisignature wallets and key recovery are building at the core a gasless transaction protocol. 

# Tenzorum Gasless TXs
We are building around the concept that relayers can listen out for transactions and be randomly selected from different pools. The likeliness of you being selected is based on how much tokens you have staked. Up for debate are topics around being rewarded with tokens and how that may affect relayers on the network.

# SDK
Between a dapp implementing our SDK and the service node network is Tenzorum's SDK.

### Format

```javascript
{
      uint8 _v, bytes32 _r, bytes32 _s,
      address _from, //the subscriber
      address _to, //the publisher
      uint _value, //wei value of transfer
      bytes _data, //data input
      address _rewardType, //reward relayers in tokens or ETH
      uint _rewardAmount //amount to reward
}
```

### Rx
```javascript
    ##Client SDK

    HTTP POST https://login.tenzorum.app/execute + {payload}
    GRAPHQL endpoint mutation ExecuteGaslessTx($from: $WalletAddress!, $to: $WalletAddress!, $amount: Int!) {
                       executeTransaction(from: $from, to: $to) {
                            amount
                       }
                     }

    ##Relay RPG
    - Coming
```

### Tx
```javascript
{
    function execute(
      uint8 _v, bytes32 _r, bytes32 _s,
      address _from,
      address _to,
      uint _value,
      bytes _data,
      address _rewardType, uint _rewardAmount) public
}
```

### Example Implementation Links
- Coming

[Tenzorum](https://github.com/austintgriffith/meta-transaction-format-share/blob/master/tenzorum.org.md)
