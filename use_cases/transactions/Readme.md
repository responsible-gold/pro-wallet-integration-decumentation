# Transaction Batches

## Create a transaction batch

A `transaction` is an instruction move funds from an `organizationAccount` to a specific [recipient](../recipients) or
wallet address.

`Transaction batch` allows to perform multiple transaction in once.

![create_batch.png](create_batch.png)

Before the batch is created and saved to the database, the `Transaction API` will validate the `account` balance is
enough to support the total amount of all transactions.

Once the batch and its transaction are saved in database, the `Transaction API` will return the follow batch info.

| Field    | Type          | Description                                    |
|----------|---------------|------------------------------------------------|
| `ID`     | Number (Long) | Numeric identifier of the batch                |
| `UUID`   | String        | Large string identifier                        |
| `Status` | String        | `PENDING` `APPROVED` `IN_PROGRESS` `SUCCEEDED` |

> When a `batch` is created is in `PENDING` status

After the synchronous part of the process if completed: the batch is created and returned to the `SDK Client`, the `Transaction API` will create asynchronously each transaction on the blockchain.

> At this moment the balance from the `account` will be reserved, but, the `funds`won't be transfer __until the `batch` is approved__.

Finally, when all transactions are created on the blockchain, the `Transaction API` will notify to `External System` via the `callback URL`

## Add transaction to batch

## Remove a transaction from batch

## Approve a batch

