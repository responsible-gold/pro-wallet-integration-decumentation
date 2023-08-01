# Qenta SDK

## Requirements
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

