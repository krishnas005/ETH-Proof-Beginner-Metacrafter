# MyToken Smart Contract
 
## Description
MyToken is a basic Solidity smart contract designed to simulate a simple cryptocurrency. It allows the creation (minting) and destruction (burning) of tokens, with functionality to track the balance of tokens for each address. The primary purpose is to demonstrate the core concepts of token management on the Ethereum blockchain.

## Getting Started
Requirements

### Token Details:

Token Name: KANNU
Token Abbreviation: KAN
Total Supply: The initial supply of tokens, which starts at 0 and increases as tokens are minted.
Mapping Balances: A mapping to keep track of token balances for each address.

Mint Function: Increases the total supply of tokens and assigns them to a specified address.

Burn Function: Decreases the total supply of tokens and removes them from a specified address, with a check to ensure the address has enough tokens to burn.

## Code Explanation
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract MyToken {

    // Public variables to store token details
    string public tokenName = "KANNU";
    string public tokenAbbrv = "KAN";
    uint public totalSupply = 0;

    // Mapping to store balances of addresses
    mapping(address => uint) public balances;

    // Mint function to create new tokens
    function mint(address _address, uint _value) public {
        totalSupply += _value;            // Increase total supply by the value
        balances[_address] += _value;     // Increase balance of the given address
    }

    // Burn function to destroy tokens
    function burn(address _address, uint _value) public {
        if (balances[_address] >= _value) { // Check if the address has enough tokens
            totalSupply -= _value;         // Decrease total supply by the value
            balances[_address] -= _value;  // Decrease balance of the given address
        }
    }
}
```



## Example Interaction

### Minting Tokens:

```
mint("0xYourAddress", 100); // This will add 100 tokens to the specified address
```

### Burning Tokens:
```
burn("0xYourAddress", 50); // This will remove 50 tokens from the specified address, if it has sufficient balance
```







