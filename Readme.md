# Creditcoin Legacy (Sawtooth) Transaction Types

## General Information
* `[amount]` is displayed in smallest unit (e.g. Credo, Wei, Satoshi)
* `[blockchain]` is one of `erc20`, `ethless`, `ethereum` or `bitcoin`
* `[address]` is the actual address string in the given blockchain. ERC20 tokens are displayed as `[erc20ContractAddress]@[ethAddress]`
* `[interest]` is displayed in 10,000ths of a percent, i.e. 10,000 is 1%, 100,000 is 10%
* `[gain]` is the amount of interest is being paid on top of the principle in smallest unit (See _[amount]_ above). This is 0 for investor’s initial loan to fundraiser
* `[maturity]` is a length in a number of creditcoin blocks. Think of this as interest tick rate that starts with one ticked already applied.
* `[fee]` is in creditcoin credo. This is taken from the fundraiser and given to the investor when an investor loans a fundraiser money
* `[expiration]` a length of time as a number of creditcoin blocks (One block is approximately one minute)


## Namespaces and Prefixes

| Type                 | Namespace | Example ID
| -------------------- | --------- | ----------------------------------------------------------------------
| creditCoinNamespace  | `8a1a04`  | `8a1a0400009950ce32a26eb08478aa8dc06f36313920912dcbf01f6a33617d5942b90c`
| settingNamespace     | `000000`  | `000000a87cb5eafdcca6a84ea5ee68fea05586b9b74d5852010cc4e3b0c44298fc1c14`

| Type                 | Prefix | Example ID
| -------------------- | ------ | ------------------------------------------------------------------------
| walletPrefix         | `0000` | `8a1a0400009950ce32a26eb08478aa8dc06f36313920912dcbf01f6a33617d5942b90c`
| addressPrefix        | `1000` | `8a1a041000e9944a674a83036698086f622fd6330ab379a866b66101b7186b09e6c664`
| transferPrefix       | `2000` | `8a1a04200020b993a256eda7633aeed80b1379bd06a49f80216b8ff52fb0c6a0a365a4`
| askOrderPrefix       | `3000` | `8a1a043000c0d4eaf027cfd4f9b08f72b672dc7c3d106d582c602c7588ef5f8ff68eba`
| bidOrderPrefix       | `4000` | `8a1a044000fa2731e55827287b1991d0ffdee5fbdf5b888adee7199782097652bacb26`
| dealOrderPrefix      | `5000` | `8a1a04500063ad608f8b5396f338d1f134e14a498893284de07bf52e44185a46ad685c`
| repaymentOrderPrefix | `6000` | `8a1a0460008880ce32a26eb08478aa8dc06f36313920912dcbf01f6a33617d5942cab1`
| offerPrefix          | `7000` | `8a1a047000df34b005dcc0da352b2edb2c5e940b7f2620cdc583d8f711726fec51edfc`
| erc20Prefix          | `8000` | `8a1a048000999999999999999999999999999999999999999999999999999999999999` (Not a real ID)
| processedBlockPrefix | `9000` | `8a1a049000999999999999999999999999999999999999999999999999999999999999` (Not a real ID)
| feePrefix            | `0100` | `8a1a04010097cf81340280e32394ab6f8232f47bae4a751ca0cf09eae3e26845997f4e`

---

## SendFunds
8300ea0747a01fd1380faf457008e277019a6ba0207285f2b0c3304f3c5f313e231d2a766b71b29b7fd735ae62dda76603e349fa06332962ef19cc5c2b58f16b

`SendFunds [amount] [sighash]`

```
SendFunds 1 9950ce32a26eb08478aa8dc06f36313920912dcbf01f6a33617d5942b90c
```

## RegisterAddress
28270bf6463055ba97246afdbecd798a096d77cb0fa72b64dd1906b08c4b3e2c06b9ddd05875bc0d3810cc6ff66e750a4592d3f851bd53f89f6ef4175c938dae

`RegisterAddress [blockchain] [address] [network]`

```
RegisterAddress ethless 0x4AB30B965A8Ef0F512DA064B5e574d9Ad73c0e79@0x553c22ff883c1FC12a59376aC068Df7140B7066d ngng
```

## RegisterTransfer
4298224c7d3f9ac3db7ee8352adae390c9b974fb193664466ce2bfc062def8e46f8b45b564b41ac818aa9ba9f20c15d0ef7d2dd088cb0ec1a2577675653c8afa

`RegisterTransfer [gain] [dealOrderID] [transactionID]`

```
RegisterTransfer 100000000000000000 8a1a04500063ad608f8b5396f338d1f134e14a498893284de07bf52e44185a46ad685c 0x552a9802ef1407ce7c453a99a30bb0b8a5097decf67eb6b41a41016b4fadc599
```

## AddAskOrder
2c0167a437f04227f551e3a4af7345b91e54022959716541bc98e997aaec569d7b9c930f3d9c96984049169c8841d27af5c585bf88d294a043ad9d598f4cf8dc

`AddAskOrder [addressID] [amount] [interest] [maturity] [fee] [expiration]`

```
AddAskOrder 8a1a041000ad34025c7aea1d0c8840ab28adc8f52771df8900ff68b1b47b0323aa919a 10 11000 100 100000000000000000 100
```

## AddBidOrder
9e8e98e247d28a83459b488fb390774cef499284f1f2717342f98d703791dbb7215030d790c660d3f24468d98cc6c513ba0ec6339c767e8fb07b8a3b7bf2707d

`AddBidOrder [addressID] [amount] [interest] [maturity] [fee] [expiration]`

```
AddBidOrder 8a1a041000e9944a674a83036698086f622fd6330ab379a866b66101b7186b09e6c664 10 11000 100 100000000000000000 100
```

## AddOffer
90c4e9226dbdcc2c1176a8a2d1f695c93973ea19335a22910d72c00361f0ad63672a33793f5ca1e2186e520ca64dc033273f3c3021b604b3da338c2725655ab2

`AddOffer [askOrderID] [bidOrderID] [expiration]`

```
AddOffer 8a1a043000c0d4eaf027cfd4f9b08f72b672dc7c3d106d582c602c7588ef5f8ff68eba 8a1a044000fa2731e55827287b1991d0ffdee5fbdf5b888adee7199782097652bacb26 86400
```

## AddDealOrder
c625dfdca50526f7de09a8ac4ca4c22ebdb6cc48be6efeebdb86165fbba1e9151d86eda698e36da14efc769e7889cc4f9b8115acb54b150e526d497036c4b104

`AddDealOrder [offerID] [expiration]`

```
AddDealOrder 8a1a047000df34b005dcc0da352b2edb2c5e940b7f2620cdc583d8f711726fec51edfc 86400
```

## CompleteDealOrder
2da1132e768eb4299cbc4f9697dfd0705881396349a91dc2147fa52adaab23f31442292b9f0ee214c9103d55df4440faa85c6ec7b33bacab16903d207f0f905c

`CompleteDealOrder [dealOrderID] [transferID]`

```
CompleteDealOrder 8a1a04500063ad608f8b5396f338d1f134e14a498893284de07bf52e44185a46ad685c 8a1a04200020b993a256eda7633aeed80b1379bd06a49f80216b8ff52fb0c6a0a365a4
```

## LockDealOrder
5d00925b910df19963b342c2bdeb5bc17386a866cf2026a392e99a62b8c8e5325301b6bdcc98fe3db8c57cde7e5777c17c69762949803c95948526b8b407a873

`LockDealOrder [dealOrderID]`

```
LockDealOrder 8a1a04500063ad608f8b5396f338d1f134e14a498893284de07bf52e44185a46ad685c
```

## CloseDealOrder
761415841fae708f45e6b05cab203d9b357403d83536b4d41eae2ca8174c9ed76ccba07a07820d59a113ed05b55df4464b73d5d93d71bd314ca93da4a3ee616b

`CloseDealOrder [dealOrderID] [transferID]`

```
CloseDealOrder 8a1a04500063ad608f8b5396f338d1f134e14a498893284de07bf52e44185a46ad685c 8a1a042000ab3fdb91429f06872f2a7efcee73e69b84dc4dc7d06f8f851aedf79dacf4
```

## Exempt
No example transaction available

`Exempt [dealOrderID] [transferID]`

## AddRepaymentOrder
No example transaction available

`AddRepaymentOrder [dealOrderID] [addressID] [amount] [expiration]`

## CompleteRepaymentOrder
No example transaction available

`CompleteRepaymentOrder [repaymentOrderID]`

## CloseRepaymentOrder
No example transaction available

`CloseRepaymentOrder [repaymentOrderID] [transferID]`

## CollectCoins
33c174e9276ac9a8a98e94ee20c20ab167ad18b6094b5d82cdeca6859c784e01098f1500a874576d416b703f499b88c5a43d2014378dba47a1ddf6715d1a0c4f

`CollectCoins [ethAddressID] [amount] [transactionID]`

```
CollectCoins 0xCc31Bd78e138C9C27e0EFaC487Fa6fDdc02859Bf 1000000000000000000 0x773b4636248b2bfc6d744f5edbc95d2907127d2029ad2c52cd6662f218372468
```

## Housekeeping
15483feff155539d01c2bf93267aca310efc24e44144c7123709e8ec60be735c36f64a05352215dae2b7654f97a37918494a4a268cd722defe9a44d304a6da9b

`Housekeeping [blockNum]`

```
Housekeeping 462242
```
