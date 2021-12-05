# LedgerFunds

##This is a very simple contract, which contians 5 functions and a modifier:
- addBalance : adding an arbitrary amount of eth ( it must be less than 10 ) to the selected address
- createTransaction : This is where the sender can send an amount to the receiver and creates a transaction ID with the two address and the amount saved
- getTransaction : A simple view function, which returns a transaction by the selected ID
- getContractBalance : This view function returns the balance of the contract
- getBalance : This view function returns the balance of the msg.sender's address
