# Deflationary Token

This is a simple Solidity smart contract implementing a deflationary token. The total supply decreases with every transfer due to a burn mechanism.

## Features

- Basic token with a burn-on-transfer mechanism.
- No external imports or dependencies.
- Fixed total supply that reduces over time.

## Contract Address

```
0x60625F7C83c64BF1250240BDb7Dc0DE87A1096C9
```

## How It Works

1. The deployer receives the total initial supply.
2. When a transfer occurs, 1% of the amount is burned.
3. The recipient gets the remaining 99% of the transferred tokens.

## Example Usage

```solidity
// Deploy the contract
DeflationaryToken token = new DeflationaryToken();

// Transfer tokens
token.transfer(address(0x123), 1000);
```

## Smart Contract Code

```solidity
pragma solidity ^0.8.0;

contract DeflationaryToken {
    mapping(address => uint256) public balanceOf;
    uint256 public totalSupply = 1000000;
    
    constructor() {
        balanceOf[msg.sender] = totalSupply;
    }
    
    function transfer(address to, uint256 amount) public {
        balanceOf[msg.sender] -= amount;
        balanceOf[to] += amount - (amount / 100);
        totalSupply -= amount / 100;
    }
}
```

## License

This project is open-source and can be used freely.

