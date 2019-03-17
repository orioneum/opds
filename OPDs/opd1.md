
# Orioneum Asset Registry

| opdid | author                      | type     | status | created    |
| ----- | --------------------------- | -------- | ------ | ---------- |
| 1     | tore.stenbock@blockpayd.com | Protocol | Draft  | 2019-03-17 ||

## Summary
Main contract of the Orioneum ecosystem. A simple registry mapping asset contracts to its owner. Users can add assets into the registry through public *add* functions.

## Specification
This contract maintains an array of AssetsInfo structures. The structure and array is as follows:
```solidity
struct AssetInfo {  
  address oad_addr;  
  address owner;  
}
AssetInfo[] private assets;
```
Users can add assets into the registry by providing the address of the contract of the asset and calling the following function:
```solidity
function addAssetListing(address _oad) public {
  ...
}
```

## Rationale
Registering assets onto Orioneum is a fundamental feature. This OPD provides the description of the protocol to do so and provide further information and documentation of the workings in the code.

## Implementation
