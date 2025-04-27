# raft-wallet
Raft-wallet is a raft secure remote wallet for lotus.
## raft
Provides high availability implementation based on Raft consensus algorithm
- Automatic leader election
- Data replication and synchronization
- Automatic failure recovery
- State snapshot and recovery

## Security
### Implement more granular permission control
Raft-wallet tries to improve upon the authenication and authorization model by providing a more fined grained list of permissions on the lotus api. 
The methods WalletHas, WalletList are assigned under the permission Read. Methods WalletNew, WalletImport are assigned Write, WalletSign the Sign permission, leaving WalletExport, WalletDelete to the Admin permission.

### Encrypted storage of private keys
Private keys are encrypted before being saved locally.
### Audit Logs
Raft-wallet records operation requests, making it easier to investigate if someone attempts to misuse private keys.

## Filtering Rules
Raft-wallet supports custom filtering rules.
Rules are sets of conditions that determine whether a given sign can be approved or not. 

Example rules:
- Disallow signing of transfer messages (method=0)
- Allow or Disallow signing of messages for specific actor's specific methods
- Only allow signing messages from specific address
