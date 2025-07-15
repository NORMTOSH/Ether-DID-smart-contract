# Ethereum DID Registry

A smart contract for managing Decentralized Identifiers (DIDs) and their associated data on the Ethereum blockchain. This registry allows identity owners to manage delegates, attributes, and store associated IPFS CIDs for both DID Documents and Profiles.

## 📌 Features

- 🔐 **Ownership Management**  
  Assign and transfer ownership of an Ethereum address acting as a DID.

- 👥 **Delegate Management**  
  Add or revoke delegates by type with a validity period.

- 📝 **Attribute Management**  
  Add or revoke attributes associated with a DID.

- 🧾 **DID Document & Profile Storage**  
  Store and retrieve IPFS CIDs representing:
  - DID Documents
  - Profile metadata

- 🔑 **Meta-transaction Support**  
  Most write operations can be signed off-chain and relayed by another party.

## 🛠 Contract Functions

### Ownership

- `changeOwner(identity, newOwner)`
- `changeOwnerSigned(...)`

### Delegation

- `addDelegate(...)`
- `addDelegateSigned(...)`
- `revokeDelegate(...)`
- `revokeDelegateSigned(...)`
- `validDelegate(...)`

### Attributes

- `setAttribute(...)`
- `setAttributeSigned(...)`
- `revokeAttribute(...)`
- `revokeAttributeSigned(...)`

### DID/PROFILE Document CIDs (IPFS)

- `setProfileCID(identity, cid)`
- `getProfileCID(identity)`
- `setDIDDocumentCID(identity, cid)`
- `getDIDDocumentCID(identity)`

## 🧪 Events

- `DIDOwnerChanged`
- `DIDDelegateChanged`
- `DIDAttributeChanged`
- `ProfileCIDUpdated`
- `DIDDocumentCIDUpdated`

## 🧾 Example Usage

```solidity
// Set profile CID for your DID
registry.setProfileCID(msg.sender, "Qm...");

// Set DID document CID
registry.setDIDDocumentCID(msg.sender, "Qm...");

// Add a delegate valid for 30 days
registry.addDelegate(msg.sender, keccak256("veriKey"), delegateAddress, 30 days);

// Set an attribute (e.g., service endpoint)
registry.setAttribute(msg.sender, keccak256("service"), abi.encode("https://example.com"), 365 days);
