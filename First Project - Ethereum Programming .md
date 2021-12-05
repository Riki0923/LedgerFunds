//SPDX-License-Identifier: MIT 

pragma solidity ^0.8.1; 

pragma abicoder v2;

contract LedgerFunds {

address[] private participants;

constructor(address[] memory _participants){
     participants = _participants; }

modifier onlyOwner (){
     bool participant = false; 
     for(uint i =0; i<participants.length; i++){ 
         if (participants[i] == msg.sender){
              participant = true; 
              } 
                } 
         require(participant = true);
          _; 
                    } 
         
         struct Transactions { 
            uint256 id;
            address payable _receiver; 
            address _sender; 
            uint256 _amountSent; 
            uint256 _balanceRemained;

}

Transactions[] transactionNumber;

mapping(address => uint256) balances;

function addBalance() onlyOwner public payable {
     require(msg.value <= 10 ether, "The amount you want to add is too big"); 
     balances[msg.sender] += msg.value; 
     }

function createTransaction(address payable _receiver, uint _amount) public payable onlyOwner {
    require(balances[msg.sender] >= _amount, "insufficient balance"); 
    balances[msg.sender] -= _amount;
    balances[_receiver] += _amount;
    uint _balanceRemained = balances[msg.sender] -= _amount;

    Transactions memory newTransaction = Transactions(transactionNumber.length, _receiver, msg.sender, _amount, _balanceRemained); 
    transactionNumber.push(newTransaction); 
}

function getTransaction(uint256 _id) external view returns(address, address, uint256, uint256 ){
     return (transactionNumber[_id]._receiver, transactionNumber[_id]._sender, transactionNumber[_id]._amountSent, transactionNumber[_id]._balanceRemained);

}

function getContractBalance() public view returns(uint256){ 
    return address(this).balance;

}

function getBalance() public view returns(uint256){
     return balances[msg.sender];

}

  }
