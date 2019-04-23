
This is the suggested template to use for creating Orioneum Protocol Descriptions.  
Some of the fields are required and some are optional.  

> *opdid*: `<to be assigned>` (required)  
> *title*: `<A clear title>` (required)  
> *author*: `Firstname Lastname (GitHub username)` (required)  
> *type*: `Protocol | Standard` (required)  
> *status*: `Draft | Update | Final` (required)  
> *updated* : `<date in yyyy-mm-dd format>` (required)

# OPD Title (required)

| opdid | author | type | status | created |
| ----- | ------ | ---- | ------ | ------- |
|       |        |      |        |         ||

## Summary (required)
A short description of the protocol update or amendment or technical issues being addressed in the OPD. Explained in a simple and layman-accessible way.

## Specification (required)
Detailed explanation of the OPD and should describe all specifications and schematics for an easy usage of the OPD. This section should act as documentation for any syntax, features, APIs, etc.

## Rationale (required)
The why behind the specifications. It should describe related work, alternate designs, design decisions, and future work.

## Implementation (optional)
Provide details on the implementation of the OPD. Before the status can be set to *Final*, a link to the Pull Request into mainstream code must be provided. This section can be omitted for proposals in *Draft* or *Update*, but it is recommended to provide implementation info as much as possible.
