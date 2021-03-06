# Lab 2.3.2: Escrow Services


In this lab, you are given the initial state that a custom Blockchain network of several miners is hosted on an on-campus machine. The Blockchain machine also runs a daemon that periodically instructs some miner to conduct transactions with other miners.

The lab will feature programming exercises for implementing the
normal workflow of an escrow service (e.g., deposit and final payment) and the dispute
resolution (i.e., returning payment to the buyer).

Create 3 accounts and Mine few Ethers in to all the accounts. Refer Lab 3.1 for more details.

In this lab, you will create a contract for Escrow Service given the System Design for the contract and call the functions. Refer [[link](https://github.com/BlockchainLabSU/SUBlockchainLabs/blob/master/lab4.1/README_solc.md)] to know more about how to deploy simple contract and call its functions.


## Escrow Service and Contract understanding

An escrow protocol is a three-party protocol among a buyer, a seller and an explicit escrow service. At the beginning of the transaction, the buyer makes a security deposit to the escrow service. This is done by the buyer sending a transaction to an address on which the escrow smartcontract runs. After the transaction, if both seller and buyer agree, the escrow smart contract will make the payment to the seller. If there is a dispute, meaning either seller or buyer disagrees, the smart contract will withhold the payment from sending to the seller.

In this lab, we model the Escrow service flow as below:
1.	The buyer makes a security deposit to Escrow service (a smart contract running on the Blockchain)
2. (Case 1): Both the buyer and the seller agree with the deal, the Escrow service sends the funds to the seller. 
3.	(Case 2): The buyer agrees with the deal but the seller doesn't, or the seller agrees with the deal but the buyer doesn't. In this case, an off-chain counterpart of Escrow service will fire a timeout function in the smart contract. The timeout function will then trigger a refund to the buyer. 
4. (Case 3): Both the buyer and the seller disagree with deal. In this case, the buyer will get the refund. 

Notice that in all cases, the Escrow service collects 1% of the secure deposit as the service fee.

Refer [[link](https://www.investopedia.com/terms/e/escrow.asp)] and [[link](https://www.escrow.com/what-is-escrow)]   for more details about escrow service.

![A test image](https://github.com/BlockchainLabSU/SUBlockchainLabs/blob/master/lab4.3/flow.png)


## Contract Design

Create at least 3 accounts (one for Bank to collect the deposited amount and other two for seller and buyer) and mine few ethers, before you deploy the contract. Buyer, Seller and Escrow/Bank addresses can be hard-coded and  let's assume settlement call must be made by Escrow for lab purpose.

Variable list and functions mentioned below are just for reference. You can design the solution for this lab provided all the functionalities are covered.



### Variables

1.	Buyer, seller and bank/escrow address
2.	Boolean variables to keep track of buyer and seller agreement and if both have given their choice (agree/disagree) or not.
3.	Start variable to keep track when contract starts.

## Lab Tasks

***Note: For task 1,2 and 3, you can deploy and run your smart contract using Remix***

### Lab Task 1: Both parties agrees

You should have a Deposit function to increment the balance - Buyer to deposits product price, contract time starts now. This is common for all lab tasks in this lab.
If both the parties agree, transfer 1% of the deposit amount to escrow (transaction fee) and rest to seller.

### Lab Task 2: Both parties disagree

If both disagrees, take transaction fee (1% of teh deposit amount) and refund buyer.

### Lab Task 3: In case of dispute, one of them agree other don't.

If seller agrees but not buyer, take transaction fee and contract should wait for 2 minutes and refund buyer (remember to call this function after 2 minutes). 
If buyer agree and seller don't, escrow will call the kill function and buyer gets refunded


Make sure your contract works for multiple calls and settlement happens only if both parties have explicitly given their approval/disapproval.

### Bonus Task (20%): 

Deploy and run the code of Task 1,2,3 on our on-campus Blockchain. Include screenshots of the results in your report. You can use [[this tutorial](https://github.com/BlockchainLabSU/SUBlockchainLabs/blob/master/lab4.1/README_solc.md)] as a reference of how to deploy smart contracts on a on-campus Blockchain.



 




