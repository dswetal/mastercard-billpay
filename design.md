
# Bill Pay Application for XYZ corporation


## Problem statement

XYZ Corporation would like to create a new bill payment application to act as hub between customers and billers. XYZ Corporation will maintain customer account with balances in it, will maintain biller list along with bill data and will store all transaction data.

## Functional requirements
#### 1.Registration :
 Provide a feature to “register” customer for paying bills. As part of registration capture email id only. Successful registration should create a “stored value account’ (wallet) associated with the registered customer. Option for customer to move funds to the wallet as part of registration.

#### 2.Pay Biller :
 Pay your utility bills
a) Fetch billers and bill from 3rd party external applications.
b) Select a biller, fetch the bill and pay that using the wallet.
c) Move funds from customer wallet to biller account.
#### 3.Bulk/File based Bill Payment
Process bill payments for N number of records received in a fi le.Multiple fi les can be received in a day. Design should supportfollowing use cases

UC 1
Design assuming XYZ provides a standard specification for Inbound bill payment file and customers (corporates, banks, service providers)adheres to this format when sending the bill pay file.

UC2
Design should also support non standard format / adhoc format in
future. The design should require minimal code changes to support
new file formats introduced in future.

## Solution
#### High level design

There will be 2 micro-services

For API definition please refer to swagger file [here](https://github.com/dswetal/mastercard-billpay/blob/main/API_definition_swagger.yaml)

 1. Wallet Service

		Wallet service will expose api's for following functions 
			a. Register new customer to create new wallet 
			b. Check balance for a customer
			c. Add money to wallet
			d. Pay money from wallet

		Tech stack :
			a. Spring boot microservice deployed on Kubernetes 
			b. Database : Postgress 
			c. Deployed on AWS cloud

		

 2. Bill pay service

		Bill pay service will expose api's for following functions 
			a. Pay bill
			b. Fetch billers
			c. Fetch billing history
			d. Bulk bill pay

		Tech stack :
			a. Spring boot microservice deployed on Kubernetes 
			b. Database : Postgress 
			c. Deployed on AWS cloud


 

#### Block diagram


![design](https://github.com/dswetal/mastercard-billpay/blob/main/high_level.png)

#### Sequence diagram

![sequence diagram](https://github.com/dswetal/mastercard-billpay/blob/main/SequenceDiagram.png)




#### NFR (Non function al requirements)

##### Security
##### Logging & Monitoring
##### Auto scaling
##### CI CD processes and tech stack
##### Automation of test suites
##### Support PI/PCI Data. Application should be PCI complaint.


