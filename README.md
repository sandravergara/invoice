# Invoice

**Chaincode and rest/json based node.js application**

**Creating Invoice using Hyperledger Fabric | Mandatory**


**GO Version**: go version go1.11.5 linux/amd64

**OS**: Ubuntu 18.04 LTS

Installing the prerequisites

**Step 1**

1. Download Go Language in this link https://golang.org/doc/install  and follow the step by step installation.
2. Set your gopath by opening the terminal and run echo $GOPATH

**Step 2**

1. Clone this repository by running 
git clone https://github.com/ssvergara/invoice.git
2. Open the Fabcar folder and copy all the files except the node modules
3. Create a folder named Fabcar under fabric-samples/  and paste the files we copied earlier.


**Output**

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


**Output**

	fabric-samples/
		|- chaincode
                |-fabcar
		|--go
		|---scm.go





**Step 3.**

Open terminal and go to this directory fabric-samples/Fabcar/
Start the fabric  ./openFabric.sh

Run npm install to create the modules

Run enrollAdmin.js

Run node mainregisteruser.js

Run node appmain.js

**Output** 

![1stuser](https://user-images.githubusercontent.com/44419783/52931276-c37e9d80-3386-11e9-9127-95bd74bb7023.PNG)







**Step 4** 

Test the endpoints using Insomnia REST Client. [Download Insomnia REST Client here: https://insomnia.rest/download/ ]

1. Choose the function GET and enter the localhost:3000/queryAllinvoice. You must see a data like this:

![localhost 3000 get](https://user-images.githubusercontent.com/44419783/52931313-e7da7a00-3386-11e9-9b66-c05e2dce7cfa.PNG)






2. Create a new tab and choose the function POST and enter the localhost:3000/invoice. Create the parameters and create your own invoices and click Send;

**Raise Invoice**

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


![localhost 3000 post](https://user-images.githubusercontent.com/44419783/52931354-0476b200-3387-11e9-89ef-7c627550a0f8.PNG)




3. Create a new tab and choose the function PUT and enter the localhost:3000/invoice. Create the parameters and create your own invoices and click Send;


**Goods Received**

**Parameters**

invoiceNumber

gr

![localhost 3000 put gr](https://user-images.githubusercontent.com/44419783/52931390-1a847280-3387-11e9-9394-935530067b0c.PNG)



4. Create a new tab and choose the function PUT and enter the localhost:3000/invoice. Create the parameters and create your own invoices and click Send;


**Bank Payment to Supplier**

**Parameters**

invoiceNumber

paidAmount

**Note:** Paid Amount must be less than Invoice Amount

![localhost 3000 put paidamount](https://user-images.githubusercontent.com/44419783/52931435-4b64a780-3387-11e9-9402-cebc7c661b84.PNG)


5. Create a new tab and choose the function PUT and enter the localhost:3000/invoice. Create the parameters and create your own invoices and click Send;

**OEM repays to Bank**

**Parameters**

invoiceNumber

repaymentAmount

**Note:** Repayment Amount must be greater than the value of Paid Amount.

![localhost 3000 repayment](https://user-images.githubusercontent.com/44419783/52931484-79e28280-3387-11e9-94e9-2265817016f5.PNG)



------------------------------------------------------------------------------------------------------------

**Creating Invoice using Hyperledger Fabric | Optional** 


**Step 1 | Raise Invoice (only supplier can create Invoice)**


Open a new terminal and open the folder fabric-samples/Fabcar/ 

Enroll a new user node enrollAdmin.js 

Run node 1stparticipantUser.js

Run node app1stparticipant.js


1. Open the Insomnia REST Client 

Choose the function GET and enter the localhost:3001/invoice 

![localhost 3001 get](https://user-images.githubusercontent.com/44419783/52931516-a26a7c80-3387-11e9-9675-a0b4cf411bb2.PNG)


2. Choose the POST function and create the parameters:

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


![localhost 3001 post](https://user-images.githubusercontent.com/44419783/52931540-b615e300-3387-11e9-8947-6df65e108965.PNG)

**Step 2 | Goods received (only OEM can do GR)** 

Open a new terminal and open the folder fabric-samples/Fabcar/  

Enroll a new user node enrollAdmin.js 

Run node OEM.js

Run node appOEM.js


**Open the Insomnia REST Client** 

1. Choose the function GET and enter the localhost:3003/invoice 

![localhost 3003 get](https://user-images.githubusercontent.com/44419783/52931582-e2316400-3387-11e9-87fa-0c2df9fa9792.PNG)



2. Choose the PUT function and create the parameters:

invoiceNumber

gr

![localhost 3003 put](https://user-images.githubusercontent.com/44419783/52931622-f9705180-3387-11e9-84c2-ee08972dcd89.PNG)



**Step 3  | Goods received (only bank can pay to supplier)** 

Open a new terminal and open the folder fabric-samples/Fabcar/  

Enroll a new user node enrollAdmin.js 

Run node bankuser.js

Run node appBank.js


**Open the Insomnia REST Client** 

1. Choose the function GET and enter the localhost:3007/invoice 

![localhost 3007 get](https://user-images.githubusercontent.com/44419783/52931645-14db5c80-3388-11e9-80de-62731a71f132.PNG)


2. Choose the PUT function and create the parameters:

invoiceNumber

paidAmount

![localhost 3007 put gr](https://user-images.githubusercontent.com/44419783/52931683-30466780-3388-11e9-8e5e-528d00877630.PNG)


**Step 4 | Transaction Log**

Open the Insomnia Rest Client. Choose the function GET and enter the localhost:3000

1. Click the query tab and type invoice as the name and INV0 as the value to get the transaction Id and timestamp.

![localhost 3000 transaction log](https://user-images.githubusercontent.com/44419783/52931713-4d7b3600-3388-11e9-8bbe-ad4f5adca356.PNG)

**Step 5 | Display Invoices**

Open the Insomnia Rest Client, choose the function GET and enter the localhost:3000

**Display invoices per Supplier**

Type the user1 in supplier to get the invoices per supplier

![localhost 3000 supplierhistory](https://user-images.githubusercontent.com/44419783/52931745-77ccf380-3388-11e9-8982-b767d1706e6b.PNG)




**Display invoices per OEM**

Type the Lenovo in oem to get the invoices per oem

![localhost 3000 oemhistory](https://user-images.githubusercontent.com/44419783/52931784-97fcb280-3388-11e9-9607-9d02edc767cd.PNG)

