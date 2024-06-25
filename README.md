# TH-AVAX-PROOF-Intermediate-EVM-Course-MODULE-2

## Overview
This module provides practical guidance on developing decentralized applications (Dapps) for both Ethereum and Avalanche blockchains using Solidity. Participants will learn how to create smart contracts, integrate them with wallets, design user interfaces, and deploy Dapps. This review focuses on the second module of the course.

## Getting Started
To begin, the project involves creating a simple contract with 2-3 functions and displaying their values in the frontend of the application. Below is a starter template:

``` javascript
contract MyBank {
    uint public balance;
    address public owner;
    mapping(address => uint) public AvailableBalance;
```
Here it defines a smart contract called MyBank that has variables declared seperately using uint (public balance) and address (public owner), and a mapping of addresses to available balances.
Next, 
```javascript    

    modifier onlyOwner() {
        require(msg.sender == owner, "Only the owner can Withdraw.");
        _;
    }
```
This code defines a modifier called "onlyOwner"() that requires the function caller to be the owner of the contract.
```javascript

    constructor(uint initialSupply) {
        balance = initialSupply;
        AvailableBalance[msg.sender] = balance;
        owner = msg.sender;
    }
```
The first line declares a constructor for the MyBank contract. 
The next line sets the initial balance of the contract to the value of the initialSupply.  It is passed in when the contract is deployed.The next line sets the available balance of the contract owner to the initial balance. 
The msg.sender contains the address of the person who is deploying the contract.The next line sets the owner of the contract to the person who is deploying the contract.

```javascript
    function CheckBalance() view public returns (uint){
        return balance;
    }
```
The CheckBalance() function is a function that returns the total balance of the contract. In other words, it allows anyone to view the total amount of money that is stored in the contract.

```javascript

    function Deposite(address WalletAddress, uint Amount) public {
        AvailableBalance[WalletAddress] += Amount;
        balance += Amount;
    }
```
The Deposite() function is a function that adds the entered amount to the available balance of the specified address. Then it sets the balance as the amount added to the previous balance.
```javascript

    function Withdraw(address WalletAddress, uint Amount) public onlyOwner {
        if (AvailableBalance[WalletAddress] >= Amount) {
            AvailableBalance[WalletAddress] -= Amount;
            balance -= Amount;
        }
    }
}
```
Explanation
The MyBank contract is defined with variables like balance (publicly accessible total balance), owner (address of the contract owner), and AvailableBalance (mapping of addresses to their respective balances).

Functions
CheckBalance(): Returns the total contract balance.
Deposite(address WalletAddress, uint Amount): Deposits a specified amount into the balance of a given wallet address.
Withdraw(address WalletAddress, uint Amount): Withdraws a specified amount from the balance of a given wallet address, restricted to the contract owner.
Usage
After compiling the contract without errors, the development environment is switched to an Injected Provider like Metamask for transactional interactions, which are subsequently visible in Metamask.

Author
This document was authored by Krish Jha.
Contact email: kptiwary706@gmail.com.
