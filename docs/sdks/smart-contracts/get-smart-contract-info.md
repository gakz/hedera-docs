# Get smart contract info

A query that returns the current state of a smart contract instance, including its balance. Queries do not change the state of the smart contract or require network consensus. The information is returned from a single node processing the query.

**Smart Contract Info Response**

| **Field**               | The byte code file ID                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| ----------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Contract ID**         | ID of the contract instance, in the format used in transactions.                                                                                                                                                                                                                                                                                                                                                                                                |
| **Account ID**          | ID of the cryptocurrency account owned by the contract instance.                                                                                                                                                                                                                                                                                                                                                                                                |
| **Contract Account ID** | ID of both the contract instance and the cryptocurrency account owned by the contract ID of both the contract instance and the cryptocurrency account owned by the contract.                                                                                                                                                                                                                                                                                    |
| **Admin Key**           | The state of the instance and its fields can be modified arbitrarily if this key signs a transaction to modify it. If this is null, then such modifications are not possible, and there is no administrator that can override the normal operation of this smart contract instance. Note that if it is created with no admin keys, then there is no administrator to authorize changing the admin keys, so there can never be any admin keys for that instance. |
| **Expiration Time**     | The current time at which this contract instance (and its account) is set to expire.                                                                                                                                                                                                                                                                                                                                                                            |
| **Auto Renew Period**   | The expiration time will extend every this many seconds. If there are insufficient funds, then it extends as long as possible. If the account is empty when it expires,  then it is deleted.                                                                                                                                                                                                                                                                    |
| **Storage**             | Number of bytes of storage being used by this instance (which affects the cost to  extend the expiration time).                                                                                                                                                                                                                                                                                                                                                 |
| **Contract Memo**       | The memo associated with the contract (max 100 bytes).                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Balance**             | The current balance of the contract.                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **Deleted**             | Whether the contract has been deleted.                                                                                                                                                                                                                                                                                                                                                                                                                          |
| **Ledger ID**           | The ID of the network the response came from. See [HIP-198](https://hips.hedera.com/hip/hip-198).                                                                                                                                                                                                                                                                                                                                                               |
| **TokenRelationships**  | The tokens associated to the contract.                                                                                                                                                                                                                                                                                                                                                                                                                          |

**Query Signing Requirements**

* The client operator account's private key (fee payer) is required to sign this query

| Constructor               | Description                            |
| ------------------------- | -------------------------------------- |
| `new ContractInfoQuery()` | Initializes a ContractInfoQuery object |

```java
new ContractInfoQuery()
```

### Methods

{% tabs %}
{% tab title="V2" %}
| Method                        | Type       | Description                                          |
| ----------------------------- | ---------- | ---------------------------------------------------- |
| `setContractId(<contractId>)` | ContractId | The ID of the smart contract to return the token for |

{% code title="Java" %}
```java
//Create the query
ContractInfoQuery query = new ContractInfoQuery()
    .setContractId(contractId);

//Sign the query with the client operator private key and submit to a Hedera network
ContractInfo info = query.execute(client);

System.out.print(info);
```
{% endcode %}

{% code title="Javascript" %}
```javascript
//Create the query
const query = new ContractInfoQuery()
    .setContractId(contactId);

//Sign the query with the client operator private key and submit to a Hedera network
const info = await query.execute(client);

console.log(info);
```
{% endcode %}

{% code title="Go" %}
```java
//Create the query
query := hedera.NewContractInfoQuery().
    SetContractID(contractId)

//Sign with the client operator private key to pay for the query and submit the query to a Hedera network
info, err := query.Execute(client)

if err != nil {
		panic(err)
}

//Print the account key to the console
println(info)
```
{% endcode %}

**Sample Output**

```
ContractInfo{
     contractId=0.0.104966, 
     accountId=0.0.104966, 
     contractAccountId=0000000000000000000000000000000000019a06,    
     adminKey=302a300506032b6570032100fcd7cce3eef78f76a538c5573ce8f00258 
          386741e03adc17c66075bf659b865d, 
     expirationTime=2021-02-10T22:27:15Z,    
     autoRenewPeriod=PT2160H, 
     storage=523, 
     contractMemo=, 
     balance=0 tℏ
}
```
{% endtab %}

{% tab title="V1" %}
| Method                        | Type       | Description                                          |
| ----------------------------- | ---------- | ---------------------------------------------------- |
| `setContractId(<contractId>)` | ContractId | The ID of the smart contract to return the token for |

{% code title="Java" %}
```java
//Create the query
ContractInfoQuery query = new ContractInfoQuery()
     .setContractId(newContractId);

//Sign with the client operator private key and submit to a Hedera network
ContractInfo info = query.execute(client);

System.out.println(info);
```
{% endcode %}

{% code title="JavaScript" %}
```javascript
//Create the query
const query = new ContractInfoQuery()
     .setContractId(newContractId);

//Sign with the client operator private key and submit to a Hedera network
const info = await query.execute(client);

console.log(info);
```
{% endcode %}
{% endtab %}
{% endtabs %}

