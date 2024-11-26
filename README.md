# Metacrafter-AVAX-3

This Solidity code demonstrates an example custom ERC20 token with an owner only mint, as well as burn and mint functions for any users.
## Description

The code is written in Solidity, a programming language for developing in Ethereum. 

### Executing program
The code can be run using Remix, an online Solidity IDE. Remix can be accessed and used in https://remix.ethereum.org/.

Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension. Copy and paste the code into the editor:
```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.10;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/access/Ownable.sol";

contract CustomToken is ERC20, Ownable {
    constructor() ERC20("FEUToken", "FIT") Ownable(msg.sender) {
        uint initialSupply = 100; 
        _mint(msg.sender, initialSupply);
    }

    function mint(address to, uint amount) public onlyOwner {
        _mint(to, amount);
    }

    function burn(uint amount) public {
        _burn(msg.sender, amount);
    }

    function tokenTransfer(address destination, uint amount) public {
        require(destination != address(0), "Invalid address");
        require(amount > 0, "Cannot transfer a value below zero");
        
        _transfer(_msgSender(), destination, amount);
    }
}
```

To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.10", and then click on the "Compile" button.

Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "CustomToken" contract from the dropdown menu, and then click on the "Deploy" button.

Once the contract is deployed, you can interact with it by calling the mint, burn, and tokenTransfer functions. The contract also includes other built in functions from ERC20 which the user can interact with.

## Authors
TWENTY-2020

## License
This project is licensed under the MIT License - see the LICENSE.md file for details


