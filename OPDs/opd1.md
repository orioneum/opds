
# Orioneum Asset Registry

| opdid | author                      | type     | status | created    |
| ----- | --------------------------- | -------- | ------ | ---------- |
| 1     | Tore Stenbock (@tastenbock) | Protocol | Draft  | 2019-04-23 ||

## Summary
Like any store, Orioneum provides a registry of deployed assets. The registry is responsible for maintaining an updated inventory list as well as owner information. Users of Orioneum are provided with several public functions, such as *Add*, *Update*, *Delist*, and *Read*. Full specifications and more information provided in this Protocol Description.

The core concept of the Orioneum Registry is that Users can deploy Orioneum Assets (as defined using Orioneum Asset Definitions, or OADs) into the Registry along with the information required as part of the OAD. The Orioneum Registry is very flexible on what the OAD represents (usually a digital twin of a real world asset), as long as the protocol is followed using the [BaseOAD](Citation needed) abstract smart contract. On registration, the Orioneum Registry will enforce an inheritence of the BaseOAD contract to make sure a controllable and standardized set of information is present in deployed assets.

The Orioneum Registry is the main entry point for any Orioneum Dapps and is the core smart contract deployed onto the Ethereum Blockchain. Most publically facing interfaces will be from this contract.

The Orioneum Registry itself will leverage on a separate storage contract. Reasoning for this is that Orioneum itself will be a fast-paced development project and updating contract addresses every time in already available dapps is simply unfeasable. Not only that, from the immutability nature of Ethereum, and all blockchains, only way to update a contract is to completely redeploy the smart contract meaning all prior stored assets will be lost as they are linked to the "old" smart contract. Therefore, the Orioneum Registry will be interfacing with a separate deployed smart contract called the Orioneum Warehouse ([OPD2](link)) acting as an Eternal Storage from the Data Segregation design pattern.  

## Specification

```solidity
function registerAsset(address _oad_addr) public {
  warehouse.addAsset(_oad_addr);
  emit AddedAssetEvent(_oad_addr);
```

## Rationale
Registering assets onto Orioneum is a fundamental feature. This OPD provides the description of the protocol to do so and provide further information and documentation of the workings in the code.

## Implementation
