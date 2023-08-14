# Accounts

## Get account balance

Use the `getBalance(...)` to get balances from a specific account, supplying the `accountId`

The method will return detailed information regarding the balances for the given account:

| Field                 | Type   | Description                                  |
|-----------------------|--------|----------------------------------------------|
| `id`                  | Number | Account identifier                           |
| `name`                | String | Account name                                 |
| `totalBalance`        | Number | Total balance included pending and available |
| `pendingBalance`      | Number | Balance pending to be confirmed              |
| `availableBalance`    | Number | Balance ready to operate                     |
| `consolidatedBalance` | Number | Summary of all balances                      |



