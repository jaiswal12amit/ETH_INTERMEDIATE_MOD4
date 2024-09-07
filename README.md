# DegenToken

DegenToken is a customizable ERC20 token built using OpenZeppelin libraries. It introduces a burnable token with additional reward and redemption mechanisms, which allows users to earn and redeem rewards for virtual items.

## Features

### 1. **ERC20 Token Standard**
   - Implements the ERC20 token standard, with functions like `mint`, `burn`, `transfer`, `approve`, and more.
   - Token Name: `Degen`
   - Token Symbol: `DGN`

### 2. **Ownable**
   - The contract is ownable, which means only the contract owner can execute certain functions such as minting tokens or setting item costs.

### 3. **Minting**
   - Only the owner can mint new tokens using the `mint` function.
   - Example: 
     ```solidity
     mint(address recipient, uint256 amount);
     ```

### 4. **Burning**
   - Users can burn their own tokens with the `burn` function, reducing the total supply.

### 5. **Reward System**
   - **Reward**: The owner can reward users with tokens, which are tracked but not immediately available to spend. 
   - **Claim**: Users can claim their rewards, which are minted to their account.
   - Example:
     ```solidity
     reward(address recipient, uint256 amount);
     claimReward();
     ```

### 6. **Redemption System**
   - Users can redeem their tokens for virtual items like `rocket` or `shield`.
   - The cost of each item is pre-defined by the owner.
   - When a user redeems an item, the corresponding amount of tokens is burned.
   - Users can check whether they have redeemed an item with `hasRedeemedItem`.

### 7. **Events**
   - `Reward(address indexed user, uint256 amount)`: Emitted when a reward is assigned.
   - `RewardClaimed(address indexed user, uint256 amount)`: Emitted when a user claims their reward.
   - `ItemRedeemed(address indexed user, string itemName)`: Emitted when an item is redeemed.

## Setup

### Prerequisites
This contract depends on OpenZeppelin libraries. Install the required OpenZeppelin packages:

```bash
npm install @openzeppelin/contracts
```

### Deploying

To deploy this contract, you will need to:

1. Have a Solidity development environment set up (such as Hardhat or Truffle).
2. Deploy the contract using a migration or deploy script.

Example deployment with Hardhat:

```javascript
async function main() {
  const DegenToken = await ethers.getContractFactory("DegenToken");
  const degenToken = await DegenToken.deploy();
  
  console.log("DegenToken deployed to:", degenToken.address);
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

### Usage

1. **Minting Tokens**
   Only the owner can mint new tokens.
   ```solidity
   mint(address recipient, uint256 amount);
   ```

2. **Burning Tokens**
   Any token holder can burn their tokens:
   ```solidity
   burn(uint256 amount);
   ```

3. **Rewarding Users**
   The owner can assign rewards to users:
   ```solidity
   reward(address recipient, uint256 amount);
   ```

4. **Claiming Rewards**
   Users can claim their rewards:
   ```solidity
   claimReward();
   ```

5. **Redeeming Items**
   Users can redeem virtual items such as `rocket` or `shield`:
   ```solidity
   redeemItem(string memory itemName);
   ```

6. **Setup Items**
   The owner can set up initial item costs with:
   ```solidity
   setupItems();
   ```

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

This token is ideal for applications that want to introduce a reward and redemption system along with a standard ERC20 token.
