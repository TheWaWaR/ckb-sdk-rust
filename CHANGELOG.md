
# 2.2.0
* **breaking change** Use ckb-indexer from ckb rpc
  - `DefaultCellCollector::new` API changed
  - remove `IndexerRpcClient::get_indexer_info` rpc method
  - rename `IndexerRpcClient::get_tip` to `IndexerRpcClient::get_indexer_tip`

# 2.1.0
* Support omni-lock supply mode
* Use anyhow::Error to replace Box<dyn std::error::Error>
* **breaking change**: Use hash instead pubkey directly when create `Identity` and `OmniLockConfig`:
  - From `Identity::new_pubkey_hash(pubkey: &Pubkey)` to `Identity::new_pubkey_hash(pubkey_hash: H160)`
  - From `Identity::new_ethereum(pubkey: &Pubkey)` to `Identity::new_ethereum(pubkey_hash: H160)`
  - From `OmniLockConfig::new_pubkey_hash(pubkey: &Pubkey)` to `OmniLockConfig::new_pubkey_hash(lock_arg: H160)`
  - Remove `OmniLockConfig::new_pubkey_hash_with_lockarg(lock_arg: H160)`
  - From `OmniLockConfig::new_ethereum(pubkey: &Pubkey)` to `new_ethereum(pubkey_hash: H160)`


# 2.0.0
* Add omni-lock support
  - Support administrator mode
  - Support anyone-can-pay mode
  - Support time-lock mode
  - Support Unlock via owner's public key hash (sighash/multisig/ethereum)
  - Support Unlock via owner's lock script hash
* Add `acceptable_indexer_leftbehind` field in `DefaultCellCollector`
* **breaking change**: change `CapacityProvider::new(lock_scripts)` argument type 
  - from `Vec<(Script, WitnessArgs)>` to `Vec<(Script, WitnessArgs, SinceSource)>`
  - Add `CapacityProvider::new_simple` for compatible with old function

# 1.1.0
* Update ckb to v0.104.0

# 1.0.1
* Fix sync_state rpc return data type

# 1.0.0
* Add several key traits to abstract different functionality
  - CellCollector
  - CellDepResolver
  - HeaderDepResolver
  - TransactionDependencyProvider
  - Signer
  - ScriptSigner
  - ScriptUnlocker
  - TxBuilder
* Add default implementation to several traits
  - DefaultCellCollector
  - DefaultCellDepResolver
  - DefaultHeaderDepResolver
  - DefaultTransactionDependencyProvider
  - SecpCkbRawKeySigner
* Implement common script signer
  - SecpSighashScriptSigner
  - SecpMultisigScriptSigner
  - AcpScriptSigner
  - ChequeScriptSigner
* Implement common script unlocker
  - SecpSighashUnlocker
  - SecpMultisigUnlocker
  - AcpUnlocker
  - ChequeUnlocker
* Implement common transaction builder
  - AcpTransferBuilder
  - ChequeClaimBuilder
  - ChequeWithdrawBuilder
  - DaoDepositBuilder
  - DaoPrepareBuilder
  - DaoWithdrawBuilder
  - CapacityTransferBuilder
  - UdtIssueBuilder
  - UdtTransferBuilder
* Remove `ckb-sdk-types` (use `ckb-mock-tx-types` instead)
* Remove `TxHelper` (use `TxBuilder` instead)
* Remove `KeyStore` (use `ckb-wallet` instead)
* Add `IndexerRpcClient` as `ckb-indexer` client
* Add `anyone-can-pay` address support for `AddressPayload` type (short address only support `mainnet`/`testnet`)
* Add new common data type `ScriptId`

# 0.101.3
* Copy init code from: https://github.com/nervosnetwork/ckb-cli/tree/163ed210f526b69a1f957bbf17a31e05defb3182
