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
