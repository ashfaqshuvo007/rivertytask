# Invoice Domain

In this file, I have illustrated the things I would suggest to change in files related to the Invoice generation of existing customers.

## Models

- `InvoiceAdded` & `InvoiceDocument` has not a lot to change. But might change for allowing some `nullable` trait or `default` values if necessary.

## Message Consumer

- In the `Consume()` method:
  - Adding validation checks for required fields coming in the message.
  - Invoking `AddInvoiceAsync` & `UpdateConsumerAsync` should be with `await`.
  - Adding new `Invoice` & updating `Customer` should be wrapped in a transaction to ensure 
  atomicity.

## Repository

- `GetCustomerInvoicesAsync()` method should be changed to maintain asynchronicity. Changes shown below:

```csharp
public async Task<List<InvoiceDocument>> GetCustomerInvoicesAsync(string customerId)
{
    var results = await _invoices.FindAsync(c => c.CustomerId == customerId);
    return await results.ToListAsync();
}
```

- Make the calls to DB more fault tolerant with proper Error handling.
