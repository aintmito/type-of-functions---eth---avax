# ERC20 Token

This Solidity program is a simple Contract program that demonstrates the basic syntax and functionaly of the Solidity programming language. The purpose of this program is to serve as a starting point for people like me who are new to Solidity and wants to know the fundamentals of how crypto wallet works.

## Description

This program is a simple contract written in Solidity, a programming language used for developing smart contracts on the Ethereum blockchain. The contract can create an ERC20 token and has three functions that mints, transfer, and burn tokens. This program serves as a simple introduction to Solidity programming. It can be used as a basis and can further improve to a more complex projects in the future.

## Getting Started

### Executing program

* To run this program, you can use Remix, an online Solidity IDE. To get started, go to the Remix website at https://remix.ethereum.org/.

* Once you are on the Remix website, create a new file by clicking on the "+" icon in the left-hand sidebar. Save the file with a .sol extension (e.g., HelloWorld.sol). Copy and paste the following code into the file:

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "@openzeppelin/contracts@4.9.0/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts@4.9.0/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts@4.9.0/access/Ownable.sol";

contract Token is ERC20, ERC20Burnable, Ownable {
    
    constructor(string memory name, string memory symbol, uint256 initialSupply) ERC20(name, symbol) {
        _mint(msg.sender, initialSupply);
    }

    function mint(address account, uint256 amount) public onlyOwner {
        _mint(account, amount);
    }

    // Transfer token
    function transfer(address recipient, uint256 amount) public virtual override returns (bool) {
        _transfer(_msgSender(), recipient, amount);
        return true;
    }

    // Burn token
    function burnFrom(address account, uint256 amount) public override  {
        _burn(account, amount);
    }

}
```

* To compile the code, click on the "Solidity Compiler" tab in the left-hand sidebar. Make sure the "Compiler" option is set to "0.8.18" (or another compatible version), and then click on the "Compile MyToken.sol" button.

* Once the code is compiled, you can deploy the contract by clicking on the "Deploy & Run Transactions" tab in the left-hand sidebar. Select the "Token - Token.sol" contract from the dropdown menu, input the name of your token, its symbol, and initial supply. Then, click on the "transact" button.

* Once the contract is deployed, you can interact with it by checking the name, owner, symbol, and totalSupply variables to check their values. After checking their values, in the left-hand sidebar, scroll up so you can check the "Account" that gives example addresses that you can use for testing the program and copy the default address that is already selecting in the dropdown menu.

* From the "Account" above, select the second wallet address and enter the same token name, symbol, and initial supply. Do it again for the third wallet address from the dropdown in the "Account.

* Select the third wallet address in the Deployed/Unpinned Contracts and click on mint, enter any non-negative value from the field then press "transact". To check the updated value, you can press the totalSupply.

* Copy the wallet address of the second account. From the third account, go to transfer and expand it by pressing the arrow down symbol, paste the wallet address of the second account in the recipient field and enter an amount. To verify, you can paste the wallet address of the second account from the balanceOf and press "call" to check the updated value.

* Lastly, go to the burn function and enter an amount, press transact afterwards. To verify, go press the totalSupply and this will display the updated value.

## Authors

[Miguel Andre Encomienda](https://www.linkedin.com/in/miguel-encomienda-526593292/)


## License

This project is licensed under the [NAME HERE] License - see the LICENSE.md file for details