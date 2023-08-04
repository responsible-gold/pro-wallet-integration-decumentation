# Qenta SDK

## Business case:

Qenta ProWallet PAYMENT DISBURSEMENT SYSTEM is designed to facilitate the efficient and secure distribution of funds from a single source (organization) to multiple recipients. This system is commonly used by businesses, and oganizations to disburse salaries, vendor payments, refunds, incentives, and other forms of payments to a large number of beneficiaries simultaneously.

## Key Concepts

- B2C / QENTA APP: Qenta App: Also known as a B2C App, B2C Wallet or Individual Retail Wallet. It is a secure digital marketplace that offers users the ability to see real-time prices, buy, sell, hold and receive payments in responsibly earned gold (Responsible Gold™), allows for account management, transaction history and charts to follow market trends. It is the application that Savia collaborators will use. 

- B2B / PRO WALLET: Also known as Pro Wallet or business wallet, it refers to the web platform for companies focused on the transfer, purchase and sale of G-Coins. This digital wallet will be used for the organization to carry out G-Coins transactions to the retail wallets of its collaborators. 

- B2B2C: Business do Business to Consumer. Ecosystem model companies reach customers through another company but have the ability to directly interact with their consumers through their own platforms. 

- Responsible Gold™: It is 99.99% pure gold that meets the best environmental, social and governance practices, documented in our Responsible Gold™ standards. Gold is digitally tracked from mine to refinery to vault with our Responsible Gold™ supply chain app. 

### Key Components of Qenta’s Payment Disbursement System SDK:

	- Allows the transfer of funds from the payer's account to another account.

	- User Interface (UI) / Application: The system has an user-friendly application that allows the org admin user or authorized personnel to manage and initiate payments.

	- Recipient Management, the system has a recipient management module to store and manage recipient data securely. This may include details such as wallet address and email.

	- Batch or Mass Payment Feature, the main feature of the system is its ability to perform batch or mass payments. Instead of processing individual payments one by one, the org admin user can upload a single file (CSV), each row in the file represents a payment transaction for a specific recipient.

Qenta ProWallet is looking to position itself as a GLOBALLY PAYMENT DISBURSEMENT SYSTEM, the approach is to allow organizations to integrate their platforms to Qenta ProWallet features via Qenta SDK so these organizations can perform an end to end payment disbursement using their own platform.

Qenta SDK (library) has to be deployed on the organization´s system so they can consume the Qenta's prowallet backend. All the calls to Qenta’s ProWallet will be executed through the SDK, the private key to allow the use of these services is passed as a parameter to the library but is never sent through the API.

All the signatures required to perfom a transaction take place using the SDK.

The services included in the SDK will be:

1. List organization accounts.: 

2. Provide organization account balance

3. Provide recipient details by email or ID:

4. Invite recipient (create link):

5. Perform external transfer.

6. Re transfer status

## Technical Requirements
- [Java 1.17 or later](https://www.oracle.com/java/technologies/downloads/)
- [Gradle](https://gradle.org/install/) or [Maven](https://maven.apache.org/download.cgi)

## Using the SDK

### Step 1: Generate `access token` and get the `private key`

To configure the `Qenta client` on your project, you will need an `access token` and your `Private key`.

Please, follow this steps to get them:

- Go to [ProWallet](https://prowallet.stage.gmint.co) console 
- In settings menu go to Security option 
- Generate an Access token and copy the Private Key. Save this value, you will need them for SDK configuration

### Step 2: Add the `Qenta SDK` to your project dependecies

For [Maven](https://maven.apache.org/download.cgi) based project you can use the follow code snipped

```xml
<dependencies>
  <dependency>
    <groupId>com.qenta</groupId>
    <artifactId>qenta-client</artifactId>
    <version>X.Y.Z</version>
  </dependency>
</dependencies>
```

For [Gradle](https://gradle.org/install/) based projects, use the follow code snipped

```groovy
dependencies {
  qenta 'com.qenta:qenta-client:X.Y.Z'
}
```

### Step 3: Initialize the `Qenta Client`

In order to use the Qenta SDK in your business logic, first you need to initialize the Qenta Client.

```java
class BusinessClass {
    
    void businessMethod() {
      //To initialize the client you need to provide the access token and the private key
      //Initialize the private key and callbackUrl
      PrivateKey privateKey;
      URL callbackUrl;
      Long organizationId;
      
      QentaClient qentaClient = QentaClient.builder()
                                    .withAccessToken("<use the access token here>")
                                    .withOrganizationId(organizationId)
                                    .withKey(privateKey)
                                    .callbackUrl(callbackUrl)
                                    .build();
      //Once the client is initialized you can use any of it's methods
      OrganizationInfoResponse response = OrganizationqentaClient.getOrganizationInfo();
      if (!response.isSuccessful()) {
        throw new RuntimeException(response.getError().getMessage());
      }
      //here you can handle the response object
    }
    
}
```


## Uses cases

| Use case | Description   | Reference doc |
|----------|---------------|---------------|
|Recipients | List, Get, Onboard your organization's recipients | [recipients](./use_cases/recipients) |
|Transactions | List, Get, and manage your batch transactionss | [transactions](./use_cases/transactions) |

