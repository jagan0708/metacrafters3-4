---

# DegenToken Smart Contract

## Overview

The `DegenToken` contract is an ERC20 token implemented in Solidity that allows users to earn and spend tokens on various digital items. The contract is built on the Ethereum blockchain and includes functionalities for minting, burning, transferring tokens, and redeeming items from a store.

### Key Features

- **ERC20 Token**: Standard token functionality including minting, burning, and transferring.
- **Item Redemption**: Users can redeem tokens for specific digital items.
- **Store Display**: Displays available items in the store.
- **Player Inventory**: Users can view the items they have redeemed.

## Contract Address

Replace `YOUR_CONTRACT_ADDRESS` with the actual deployed contract address when available.

## Installation

Ensure you have the following dependencies installed:

- [Solidity](https://soliditylang.org/)
- [OpenZeppelin Contracts](https://openzeppelin.com/contracts/)

You can install OpenZeppelin Contracts using npm:

```bash
npm install @openzeppelin/contracts
```

## Usage

### Contract Initialization

The contract is initialized with the deployer's address as the owner and pre-configured with specific items available for redemption.

```solidity
constructor(address initialOwner) ERC20("Degen", "DGN") Ownable(initialOwner)
{
    items[1] = Item("Ram Charan Ticket NFT", 1000);
    items[2] = Item("Ram Charan Autograph NFT", 500);
    items[3] = Item("Ram Charan Global Star NFT", 200);
    items[4] = Item("Ram Charan Stamp NFT", 100);
}
```

### Minting Tokens

The owner can mint new tokens:

```solidity
function mint(address to, uint256 amount) public onlyOwner 
{
    _mint(to, amount);
}
```

### Burning Tokens

Users can burn tokens to reduce their balance:

```solidity
function burn(uint256 amount) public 
{
    require(balanceOf(msg.sender) >= amount, "Insufficient balance");
    _burn(msg.sender, amount);
}
```

### Transferring Tokens

Users can transfer tokens to another address:

```solidity
function transferToken(address receiver, uint256 amount) external 
{
    require(balanceOf(msg.sender) >= amount, "Sorry, not enough Degen tokens available");
    transfer(receiver, amount);
}
```

### Redeeming Items

Users can redeem tokens for items listed in the store. Each item has a cost in Degen tokens:

```solidity
function redeem(uint256 item) external 
{
    Item storage selectedItem = items[item];
    require(bytes(selectedItem.name_of_brands).length > 0, "Invalid redeem item");
    require(balanceOf(msg.sender) >= selectedItem.cost_of_brands, "Insufficient balance to redeem");

    _burn(msg.sender, selectedItem.cost_of_brands);
    
    playerItems[msg.sender].push(selectedItem.name_of_brands);
    delete items[item];
}
```

### Viewing the Store

Retrieve the list of available items:

```solidity
function showStore() external pure returns (string memory) 
{
    return "1. Ram Charan Movie Ticket NFT (1000 tokens) 2. Ram Charan Autograph NFT (500 tokens) 3. Ram Charan Global Star NFT (200 tokens) 4.  Ram Charan Stamp NFT (100 tokens)";
}
```

### Viewing Player Items

Retrieve the items redeemed by a specific address:

```solidity
function getPlayerItems(address player) external view returns (string[] memory) 
{
    return playerItems[player];
}
```

## License

This contract is licensed under the MIT License. See the [LICENSE](./LICENSE) file for details.

## Contact

For any questions or issues, please contact [saijagankotni@gmail.com].

---
