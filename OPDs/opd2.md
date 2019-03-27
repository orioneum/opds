
# Orioneum Asset Factory

| opdid | author                      | type     | status | created    |
| ----- | --------------------------- | -------- | ------ | ---------- |
| 2     | tore.stenbock@blockpayd.com | Protocol | Draft  | 2019-03-26 ||

## Summary
Factory of smart contract to create Orioneum Asset Definitions (OADs). The Orioneum Asset Factory will take several inputs, produce a smart contract of the asset, and return the smart contract address. Ownership is maintained to ensure owners of the OADs are the only ones who can modify the contract during its lifecycle. The factory will also maintain a list of created OADs, think of records of serial numbers, which will be used when registering onto Orioneum (see [OPD1](https://gitlab.com/orioneum/opds/blob/master/OPDs/opd1.md)).

Read the [OAD types list](#oad-types) in the _Specification_ section for a full list of supported OAD types available in Orioneum.

## Specification
This contract maintains a list of created contracts and their owners.

#### <a name="oad-types"></a> List of available OAD types
| OAD | Title                      | Status | OPD Link |
| --- | -------------------------- | ------ | -------- |
|     |                            |        |          ||

## Rationale


## Implementation
