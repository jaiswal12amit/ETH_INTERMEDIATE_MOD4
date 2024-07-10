# Degen Token

## Overview
- DegenToken is a decentralized ERC20 token with additional functionality for feature purchases and token burning.
- Utilizes OpenZeppelin's libraries for secure and standardized implementations of ERC20, Ownable, and ERC20Burnable.
- Designed for flexibility and control, allowing for rewards and special interactions while ensuring secure and controlled token management.

## Special Features
- **Minting**: 
  - Owners can create and allocate new tokens to specified addresses, enhancing liquidity or incentivizing users (`mint` function).
- **Burning**: 
  - Users can permanently remove tokens from circulation, reducing the total supply (`burn` function).
- **Reward Distribution**: 
  - Owners can distribute additional tokens as rewards to specific addresses, encouraging participation or rewarding behavior (`reward` function).
- **Advanced Transfer Mechanism**: 
  - Enables tokens to trigger actions in recipient contracts upon transfer, expanding functionality beyond simple token transactions (`transferAndCall` function).
- **Ownership Control**: 
  - Only the contract owner has the authority to perform critical operations such as minting, burning, and reward distribution, ensuring secure management of token issuance and incentives.

## Events
- **Reward Event**: `event Reward(address indexed user, uint256 amount)`
  - Emitted when the contract owner distributes rewards to a user. Logs the address of the user receiving the reward and the amount of tokens rewarded.
- **RewardClaimed Event**: `event RewardClaimed(address indexed user, uint256 amount)`
  - Emitted when a user claims their accumulated rewards. Logs the address of the user claiming the reward and the amount of tokens claimed.

## Functions
- **Constructor**: `constructor()`
  - Initializes the token with the name "Degen" and symbol "DGN" and sets the contract deployer as the owner.
- **Mint Tokens**: `mint(address to, uint256 amount) public onlyOwner`
  - Allows the contract owner to create and assign new tokens to a specified address.
- **Burn Tokens**: `burn(uint256 amount) public override`
  - Allows any token holder to permanently destroy a specified amount of their own tokens.
- **Reward Users**: `reward(address to, uint256 amount) public onlyOwner`
  - Enables the contract owner to allocate additional tokens as rewards to a specified address.
- **Claim Rewards**: `claimReward() public`
  - Allows token holders to claim their accumulated rewards that have been allocated to their address.
- **Transfer Tokens and Call Contract**: `transferAndCall(address to, uint256 amount, bytes calldata data) public returns (bool)`
  - Transfers tokens to a specified address and calls a function on the recipient contract with additional data.

## Mapping
- **Rewards Mapping**: `mapping(address => uint256) public rewards`
  - Tracks the amount of rewards assigned to each user's address. When the owner rewards a user, the amount is recorded in this mapping. Users can later claim their rewards based on the values stored here.

## Security Considerations
- The contract ensures that only the owner can perform critical actions such as minting tokens and adding new features.
- Checks are in place to ensure that features exist and that users have sufficient balance before purchasing.
- The contract uses OpenZeppelin's libraries to leverage well-tested implementations and reduce the risk of vulnerabilities.

## Prerequisites
- Solidity ^0.8.9
- OpenZeppelin Contracts

## Conclusion
- The DegenToken contract provides a robust foundation for a decentralized token with advanced functionalities. 
- By incorporating secure and standardized components from OpenZeppelin, it ensures reliability and security while offering versatile features for token minting, burning, and feature purchases.

## License
- This project is licensed under the MIT License - see the LICENSE file for details.
