# metacrafters3-4

Here's a README file for your `DegenToken` smart contract:

---

# DegenToken Smart Contract

## Overview

The `DegenToken` smart contract is an ERC20 token implementation on the Ethereum blockchain. It leverages OpenZeppelin's ERC20 and Ownable contracts to provide a standard token interface along with ownership and additional functionalities such as minting, burning, redeeming, and transferring tokens.

## Features

- **ERC20 Standard:** Inherits from OpenZeppelin's ERC20 contract.
- **Ownership:** Uses OpenZeppelin's Ownable contract to restrict certain functions to the contract owner.
- **Minting:** The owner can mint new tokens.
- **Burning:** Users can burn their tokens.
- **Redeeming:** Users can redeem their tokens, which internally burns the tokens.
- **Transfer:** Users can transfer tokens to another address.
- **Event Emission:** Emits events for minting, redeeming, burning, and transferring tokens.

## Prerequisites

- Solidity `^0.8.20`
- OpenZeppelin Contracts

## Installation

1. Install OpenZeppelin Contracts:
   ```bash
   npm install @openzeppelin/contracts
   ```

## Contract Details

### Constructor

```solidity
constructor() ERC20("Degen", "DGN") Ownable(msg.sender) 
```

Initializes the contract with the token name "Degen" and symbol "DGN". Sets the deployer as the contract owner.

### Events

- `TokensMinted(address indexed account, uint256 amount)`: Emitted when tokens are minted.
- `TokensRedeemed(address indexed account, uint256 amount)`: Emitted when tokens are redeemed.
- `TokensBurned(address indexed account, uint256 amount)`: Emitted when tokens are burned.
- `TokensTransferred(address indexed from, address indexed to, uint256 amount)`: Emitted when tokens are transferred.

### Functions

- `mintTokens(address to, uint256 amount)`: Mints `amount` tokens to `to` address. Only the owner can call this function.
  ```solidity
  function mintTokens(address to, uint256 amount) public onlyOwner
  ```

- `redeemTokens(uint256 amount)`: Redeems (burns) `amount` tokens from the caller's balance.
  ```solidity
  function redeemTokens(uint256 amount) public
  ```

- `burnTokens(uint256 amount)`: Burns `amount` tokens from the caller's balance.
  ```solidity
  function burnTokens(uint256 amount) public
  ```

- `transferTokens(address to, uint256 amount)`: Transfers `amount` tokens from the caller to `to` address.
  ```solidity
  function transferTokens(address to, uint256 amount) public
  ```

- `getTokenBalance(address account)`: Returns the token balance of `account`.
  ```solidity
  function getTokenBalance(address account) public view returns (uint256)
  ```

## Usage

### Minting Tokens

Only the owner can mint new tokens.

```solidity
function mintTokens(address to, uint256 amount) public onlyOwner
```

Example:

```solidity
degenToken.mintTokens(recipientAddress, 1000);
```

### Redeeming Tokens

Any user can redeem their tokens.

```solidity
function redeemTokens(uint256 amount) public
```

Example:

```solidity
degenToken.redeemTokens(500);
```

### Burning Tokens

Any user can burn their tokens.

```solidity
function burnTokens(uint256 amount) public
```

Example:

```solidity
degenToken.burnTokens(300);
```

### Transferring Tokens

Tokens can be transferred from one address to another.

```solidity
function transferTokens(address to, uint256 amount) public
```

Example:

```solidity
degenToken.transferTokens(recipientAddress, 200);
```

### Getting Token Balance

Retrieve the balance of a specific account.

```solidity
function getTokenBalance(address account) public view returns (uint256)
```

Example:

```solidity
uint256 balance = degenToken.getTokenBalance(accountAddress);
```

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

Feel free to customize the README further to suit your specific needs and project details!
