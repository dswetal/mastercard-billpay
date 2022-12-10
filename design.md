
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

	DataModel :
	
	![design](https://github.com/dswetal/mastercard-billpay/blob/main/WalletServiceDM.png)
		
	



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
			
	
	DataModel :
	
	![design](https://github.com/dswetal/mastercard-billpay/blob/main/BillServiceDM.png)
	

 	Bounded Context :
	
	![design](https://github.com/dswetal/mastercard-billpay/blob/main/BoundedContext.PNG)	


 

#### Block diagram


![design](https://github.com/dswetal/mastercard-billpay/blob/main/high_level.png)

#### Sequence diagram

![sequence diagram](https://github.com/dswetal/mastercard-billpay/blob/main/SequenceDiagram.png)




#### NFR (Non function al requirements)

##### Security

 1. Authentication / authorization
		a. OATH 2 authentication nd authorization mechanism will be used
		b. Before hitting load balancer for any operation client must get token from Auth server
		c. Each API will check authentication and authorization for the token and if valid then serve the request.
		
2. Data security
		a. Each data base will persist PII(personally identifiable information) data in encrypted form only, lookup columns like emailId will be hashed for easy lookup. 

	 
##### Logging & Monitoring

 1. Logging 
	 a. Each service will log information in  standard format where each log line will have follwing attributes 
		 - Service ID
		 - Correlation ID
		 - TimeStamp
		 - Additional information

 2. Monitoring
	 Logs will be published to DataDog for easy monitoring.

 
##### Auto scaling

Auto scaling will be managed by Kubernetes 

##### CI CD processes and tech stack
##### Automation of test suites
##### Support PI/PCI Data. Application should be PCI complaint.


