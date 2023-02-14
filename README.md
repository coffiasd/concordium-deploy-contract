# TASK2.Deploy Your First Smart Contract

## build
```shell
cargo concordium build -e --out ./record-contract.wasm.v2
```

## deployed contract && transaction hash
```shell
 ~/concordium-client --grpc-ip node.testnet.concordium.com --grpc-port 10000 module deploy record-contract.wasm.v2 --name record-contract --sender dev-wallet
```

![alt ""](/images/deploy-v2.png)

```shell
Using default energy amount of 24720 NRG.
Deploy the module 'record-contract.wasm.v2' and name it 'record-contract'.
Allowing up to 24720 NRG to be spent as transaction fee.
Confirm [yN]: y
y
Deploying module...
Enter password for credential with index 0 and signing key with index 0:
Transaction '1ab32c996fa6f2a7fbb4d6ab05b024ba9773cd43f3036fcf7aa7f056762dc9bc' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status 1ab32c996fa6f2a7fbb4d6ab05b024ba9773cd43f3036fcf7aa7f056762dc9bc'.
[18:28:31] Waiting for the transaction to be committed...........
Transaction is finalized into block ce9b37e6e037b62760bc51428e0f18e3db77d12ff642af249cd4ba657e9fc2d2 with status "success" and cost 50.523865 CCD (24719 NRG).
[18:28:52] Transaction finalized.
Module successfully deployed with reference: '8a2bc2b8667a43cf5d214c9f15c3102dd625128080c84e3b77e80069096ce522'.
Warning: Adding module name 'record-contract', but this name is already used for module '7932944dda389597e63647967954cc097c10c14e13140557a4c5d561d525d58f'.
Specify a new name to map to this module: record-contract-v2
Module reference 8a2bc2b8667a43cf5d214c9f15c3102dd625128080c84e3b77e80069096ce522 was successfully named 'record-contract-v2'.


```


## contract hash of init 
```shell
~/concordium-client --grpc-ip node.testnet.concordium.com --grpc-port 10000 contract init record-contract-v2 --contract hackaton_concordium_task_2_record_contract  --sender dev-wallet --energy 10000
```
![alt ""](/images/init.png)
```shell
um_task_2_record_contract  --sender dev-wallet --energy 10000
Initialize contract 'hackaton_concordium_task_2_record_contract' from module '8a2bc2b8667a43cf5d214c9f15c3102dd625128080c84e3b77e80069096ce522' with no parameters. Sending 0.000000 CCD.
Allowing up to 10000 NRG to be spent as transaction fee.
Transaction expires on Tue, 14 Feb 2023 11:08:07 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0:
Transaction '9a1ff67ac04660265546bd264a9f19252678df037bffb38718e5a3cf4e4bfec8' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status 9a1ff67ac04660265546bd264a9f19252678df037bffb38718e5a3cf4e4bfec8'.
[18:58:12] Waiting for the transaction to be committed.........
Transaction is finalized into block 428e189d8c9ad0a7d9e0c101e587e17fe0bb7b3008551bfa12b5ecb193bf0fb8 with status "success" and cost 2.527308 CCD (1238 NRG).
[18:58:27] Transaction finalized.
Contract successfully initialized with address: {"index":3036,"subindex":0}

```


## contract hash of update
```shell
~/concordium-client --grpc-ip node.testnet.concordium.com --grpc-port 10000 contract update 3036 --entrypoint receive --energy 10000 --sender dev-wallet 
```
![alt ""](/images/receive.png)
```shell
Update contract 'hackaton_concordium_task_2_record_contract' using the function 'receive' with JSON parameters from 'param.json'. Sending 0.000000 CCD.
Allowing up to 10000 NRG to be spent as transaction fee.
Transaction expires on Tue, 14 Feb 2023 11:41:14 UTC.
Confirm [yN]: y
y
Enter password for credential with index 0 and signing key with index 0:
Transaction 'c8155d8cf8a24510919144239ff6b9fe27c9148d613daafc500c5b1b3e288827' sent to the baker.
Waiting for the transaction to be committed and finalized.
You may skip this step by interrupting the command using Ctrl-C (pass flag '--no-wait' to do this by default).
The transaction will still get processed and may be queried using
  'concordium-client transaction status c8155d8cf8a24510919144239ff6b9fe27c9148d613daafc500c5b1b3e288827'.
[19:31:21] Waiting for the transaction to be committed......
Transaction is committed into 2 blocks with status "success" and cost 2.092795 CCD (1028 NRG):
- 527285abfe54e4d504715be5bd1304cce86b70cd5422ba24f4cd715fca270321
- 6460624d4cff8952efd374f6b92f352cc4c4285059ef24a69e94f6d0f9ace5c4
[19:31:31] Waiting for the transaction to be finalized....
Transaction is finalized into block 527285abfe54e4d504715be5bd1304cce86b70cd5422ba24f4cd715fca270321 with status "success" and cost 2.092795 CCD (1028 NRG).
[19:31:38] Transaction finalized.
Successfully updated contract instance {"index":3036,"subindex":0} using the function 'receive'.
```
## contract invoke && parameter 
```shell
~/concordium-client --grpc-ip node.testnet.concordium.com --grpc-port 10000 contract invoke 3036 --entrypoint view
```
![alt ""](/images/view.png)


## mainnet address
>4DcMhn1cs1sF2SD2okNKaKK2K1kekTxBFcwSTLcnujLNM3PQyG

## references
- [1] document. <http://developer.concordium.software/>