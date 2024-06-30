#Project title
# ArpitToken 
This Solidity program is an ERC-20 token contract named "ArpitToken". It demonstrates the basic functionality of the ERC-20 token standard, including minting, transferring, and burning tokens. This program is designed for those who are new to Solidity and ERC-20 token development on the Ethereum blockchain.

#Description
# Description
The ArpitToken contract is a smart contract written in Solidity for the Ethereum blockchain. It implements an ERC-20 token with the following features:

Minting Tokens: Upon deployment, 100 ARP tokens are minted to the contract's address. Token Transfer: The admin can transfer tokens from the contract's address to a recipient. Token Burning: Any user can burn their tokens, reducing the total supply. This contract demonstrates the use of OpenZeppelin's ERC-20 implementation, providing a secure and standard way to create tokens. It can serve as a foundation for more complex projects.

#code
# Executing Program
pragma solidity ^0.8.0;
// SPDX-License-Identifier: MIT

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";

contract ArpitToken is ERC20 {
    address admin;

    constructor() ERC20("Arpit", "ARP") {
        admin = msg.sender;
        _mint(address(this), 100 * 10 ** decimals());
    }

    modifier onlyAdmin() {
        require(msg.sender == admin, "This does not belong to the Owner");
        _;
    }

    function createtheToken(address recipient, uint256 quantity) public onlyAdmin {
        uint balance = balanceOf(address(this));
        require(balance >= quantity, "There is Not sufficient balance");
        _transfer(address(this), recipient, quantity);
    }

    function destroytheToken(uint256 amount) public {
        _burn(msg.sender, amount);
    }

    function transfertheToken(address recipient, uint256 amount) public returns (bool) {
        _transfer(msg.sender, recipient, amount);
        return true;
    }
}

# Author
Arpit https://github.com/Arpit554

# License
This project is licensed under the MIT License - see the LICENSE file for details
