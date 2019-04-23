
# Orioneum Warehouse

| opdid | author                      | type     | status | created    |
| ----- | --------------------------- | -------- | ------ | ---------- |
| 2     | Tore Stenbock (@tastenbock) | Protocol | Draft  | 2019-04-23 ||

## Summary
The Orioneum Warehouse is Orioneum's implementation for a Data Segregation design pattern to enable a key component of any software development project; upgradeability. As they Orioneum Registry keeps being added and updated with new features and improvements, the Orioneum Warehouse will manage the data storage and provide access through appropriate getters and setters. This ultimately separate logic from data storage, and is a key design pattern in smart contract development and for decentralized applications.

The smart contract itself will be owned and maintained by the Orioneum Registry through the implementation of [Ownable.sol](https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/ownership/Ownable.sol). Also, the Warehouse will enforce access control from the Orioneum Registry only meaning that the Warehouse's ownership and access controls must be transferred to the latest Orioneum Registry when necessary, and appropriate functions are provided for those actions. These access control restrictions are in effect to limit interactions of other non-Orioneum players with the Warehosue smart contract.

#### BaseOAD Abstract Smart Contract
Due to the Warehouse nature of fixed data storage, what gets to be stored must be generalized as much as possible but still maintain a control on what gets stored. Therefore, all assets that are stored in the Orioneum Warehouse is required to inherit from the *BaseOAD abstract smart contract*. This smart contract is effectively a provider of certain required code implementation as well as empty functions for higher level OADs to implement themselves.

Importantly, every OAD smart contract compliant with the Orioneum Protocol (i.e. inherits BaseOAD and have correct access controls) will be deployed as part of the overall Orioneum ecosystem but will always be owned by users in the system. Orioneum never, and never will, claim or enforce ownership of assets deployed onto Orioneum. *BaseOAD* implements the [Ownable.sol](https://github.com/OpenZeppelin/openzeppelin-solidity/blob/master/contracts/ownership/Ownable.sol) as set by the creator of the asset.

## Specification
The Orioneum Warehouse simply maintains a mapping of all assets and its information into its storage in a private **oads** mapping.
```solidity
struct AssetStorage {
  address oad_addr;
  address oad_owner;
  uint oad_type;
  BaseOAD base_oad;
}
mapping(address => AssetStorage) private oads;
```

And the Orioneum Registry can add assets through the **addAsset()** function.
```solidity
function addAsset(address _oad_addr) external {
  require(oads[_oad_addr].oad_owner != address(0x0));

  BaseOAD _base_oad = BaseOAD(_oad_addr);
  require(_base_oad.oad_type() > 0);

  ...
}
```
As can be seen, there's a few requirements checks that occur before adding an asset.

`require(oads[_oad_addr].oad_owner != address(0x0));`  
This requirement does a simple check if the mapping already contains the OAD. The methodology to check simply exploits Ethereum's all-zero initialization, where if it can find a non-zero entry in the mapping it must exist.

` BaseOAD _base_oad = BaseOAD(_oad_addr);`  
Converts the address type to BaseOAD type. If this fails, an error is thrown.

`require(_base_oad.oad_type() > 0);`  
Simple check that the higher level OAD implementation has set the *OADType* in the BaseOAD information.

#### BaseOAD Abstract Smart Contract
The BaseOAD abstract smart contract will be provided together in the same package as the Orioneum Warehouse, but it will however not be deployed. It is meant to be imported and inherited in other smart contracts that is to represent OADs.

```solidity
import "../node_modules/openzeppelin-solidity/contracts/ownership/Ownable.sol";

contract BaseOAD is Ownable {

  uint public oad_type = 0;
  uint public creation_time = now;

  function setOADType(uint _oad_type) external;
}
```

## Rationale
To allow for upgradeability of the Orioneum software development project, a data segregation from its logic is required. The Orioneum Warehouse along with the BaseOAD abstract smart contract allows a design pattern to enable Orioneum to be upgradeable of its logic while maintaining a controlled storage.

## Implementation
