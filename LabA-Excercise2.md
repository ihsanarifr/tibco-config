# Design Perform Credit Check

## Configurasi JDBC Query
* JDBC Query Name : `Get Account Info`
* JDBC Query Design : `SELECT CUSTOMER_ACCOUNT.AMOUNT_OWED,
CUSTOMER_ACCOUNT.AVAILABLE_CREDIT
FROM CUSTOMER_ACCOUNT
WHERE ((CUSTOMER_ACCOUNT.ACCOUNT_ID=?))`

## Mapper activity Customer's Credit status
```{r, tidy=FALSE, eval=FALSE, highlight=FALSE }
If (count($Get-Account-Info/resultSet/Record) > 0)
and (($Start/pfx:CreditCheckRequest/pfx:Amount + $Get-Account-Info/resultSet/Record[1]/AMOUNT_OWED)
<=
$Get-Account-Info/resultSet/Record[1]/AVAILABLE_CREDIT)
    Print "Accepted"
Else
    "Reject"
End If
```