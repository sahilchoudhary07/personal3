# personal3
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract MyToken {
    // Public variables to store the token details
    string public name;
    string public symbol;
    uint256 public totalSupply;

  // Mapping to store the balance of each address
    mapping(address => uint256) public balances;

  // Constructor to initialize the token details
    constructor(string memory _name, string memory _symbol, uint256 _initialSupply) {
        name = _name;
        symbol = _symbol;
        totalSupply = _initialSupply;
        balances[msg.sender] = _initialSupply;
    }

   //Mint function to increase the total supply and the balance of the specified address
     function mint(address _to, uint256 _value) public {
        require(_to != address(0), "Invalid address");

  totalSupply += _value
  balances[_to] += _value;
    }

  // Burn function to decrease the total supply and the balance of the specified address
    function burn(address _from, uint256 _value) public {
        require(_from != address(0), "Invalid address");
        require(balances[_from] >= _value, "Insufficient balance");
     totalSupply -= _value;
     balances[_from] -= _value;
   }
}

