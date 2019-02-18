# invoice
Chaincode and rest/json based node.js application


Creating Invoice using Hyperledger Fabric | Mandatory


GO Version: go version go1.11.5 linux/amd64
OS: Ubuntu 18.04 LTS

Installing the prerequisites

Step 1

Download Go Language in this link https://golang.org/doc/install  and follow the step by step installation.
Set your gopath by opening the terminal and run echo $GOPATH

Step 2

Clone this repository by running 
git clone https://github.com/ssvergara/invoice.git
Open the Fabcar folder and copy all the files except the node modules
Create a folder named Fabcar under fabric-samples/  and paste the files we copied earlier.


Output
	fabric-samples/
                      |-Fabcar
		|- openFabric.sh
		|--enrollAdmin.js
|---mainregisteruser.js
|---1stparticipantUser.js
|---2ndparticipantUser.js
|--- OEM.js
|---bankuser.js
|---appmain.js
|---app1stparticipant.js
|---appOEM.js
|---appBank.js

4. Create a folder fabcar under fabric-samples/chaincode/
5. Make a new folder go.
6. Inside the cloned repository, under chaincode, Copy the go folder and paste it on to fabric-samples/chaincode/


Output

	fabric-samples/
		|- chaincode
                      |-fabcar
		|--go
|---scm.go





Step 3.

Open terminal and go to this directory fabric-samples/Fabcar/
Start the fabric  ./openFabric.sh
Run npm install to create the modules.
Run enrollAdmin.js
Run node mainregisteruser.js
Run node appmain.js

Output 
Step 4 

Test the endpoints using Insomnia REST Client. [Download Insomnia REST Client here: https://insomnia.rest/download/ ]

Choose the function GET and enter the localhost:3000/queryAllinvoice. You must see a data like this:


Create a new tab and choose the function POST and enter the localhost:3000/invoice. Create the parameters and create your own invoices and click Send;

Raise Invoice
Parameters
invoiceNumber
billedTo
invoiceDate
invoiceAmount
itemDescription
gr
isPaid
paidAmount
repaid
repaymentAmount

Note: gr, isPaid, paidAmount, repaid, repaymentAmount, default values are as follows:

gr = N
isPaid = N
paidAmount = 0
repaid = N
repaymentAmount = 0





Create a new tab and choose the function PUT and enter the localhost:3000/invoice. Create the parameters and create your own invoices and click Send;


Goods Received
	Parameters
invoiceNumber
gr




Create a new tab and choose the function PUT and enter the localhost:3000/invoice. Create the parameters and create your own invoices and click Send;


Bank Payment to Supplier
	Parameters
invoiceNumber
paidAmount

Note: Paid Amount must be less than Invoice Amount


Create a new tab and choose the function PUT and enter the localhost:3000/invoice. Create the parameters and create your own invoices and click Send;

OEM repays to Bank
	Parameters
invoiceNumber
repaymentAmount

Note: Repayment Amount must be greater than the value of Paid Amount.





------------------------------------------------------------------------------------------------------------

Creating Invoice using Hyperledger Fabric | Optional 


Step 1 | Raise Invoice (only supplier can create Invoice)


Open a new terminal and open the folder fabric-samples/Fabcar/ 
Enroll a new user node enrollAdmin.js 
Run node 1stparticipantUser.js
Run node app1stparticipant.js

Open the Insomnia REST Client 

Choose the function GET and enter the localhost:3001/invoice 


Choose the POST function and create the parameters:

invoiceNumber
billedTo
invoiceDate
invoiceAmount
itemDescription
gr
isPaid
paidAmount
repaid
repaymentAmount


Step 2 | Goods received (only OEM can do GR) 

Open a new terminal and open the folder fabric-samples/Fabcar/  
Enroll a new user node enrollAdmin.js 
Run node OEM.js
Run node appOEM.js

Open the Insomnia REST Client 

Choose the function GET and enter the localhost:3003/invoice 



2. Choose the PUT function and create the parameters:
invoiceNumber
gr







Step 3  | Goods received (only bank can pay to supplier) 

Open a new terminal and open the folder fabric-samples/Fabcar/  
Enroll a new user node enrollAdmin.js 
Run node bankuser.js
Run node appBank.js


Open the Insomnia REST Client 

Choose the function GET and enter the localhost:3007/invoice 

	2. Choose the PUT function and create the parameters:
invoiceNumber
paidAmount



Step 4 | Transaction Log
Open the Insomnia Rest Client. Choose the function GET and enter the localhost:3000

Click the query tab and type invoice as the name and INV0 as the value to get the transaction Id and timestamp.


Step 5 | Display Invoices
Open the Insomnia Rest Client, choose the function GET and enter the localhost:3000

Display invoices per Supplier

Type the user1 in supplier to get the invoices per supplier



Display invoices per OEM

Type the Lenovo in oem to get the invoices per oem


