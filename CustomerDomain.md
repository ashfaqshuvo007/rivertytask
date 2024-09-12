# Customer Domain

In this file, I have illustrated the things I would suggest to change in files related to the Customer creation and customer information exposing API endpoint.

## Models

1. `CustomerAdded.cs` and `CustomerDocument.cs` has some inconsistencies.

    - `Id` in `CustomerAdded.cs` has type String but in `CustomerDocument.cs` it is `ObjectId`.
    - Also, `CustomerId` field is missing.
    - I think the change should be `public string CustomerId`
    - Also, we can change the `CustomerDocument` to allow some `nullable` trait or `default` values if necessary.

## Controllers

`CustomerController` -  I can see a lot of discrepancies. Although it will work but there are lot of violations of best practices and security issues.

- HTTP verb missing i.e. `GET`, `POST` etc.
- Usage of `[FromBody]` in a `GET` endpoint. `GET` requests should not have parameters passed through `RequestBody`.
- Lack of validations i.e. `CustomerId` is not checked for null
- `Customer` is non-existent.
- Proper error handling and messages to the client in response.
- May be use `IActionResult` instead of `JsonResult`.
- Authentication should be put in place.

## Message Consumer

- In the `Consume()` method, we can do the message consumption and `Customer` creation within a transaction to retain Atomicity.
- `CustomerRepository` dependency injection should be `readonly`.
- We may change the `CustomerRepository` to interface `ICustomerRepository` for better testing.

## Repository & Response

- `GetCustomerAsync` should be changed slightly to maintain asyncronicity. The changed method is shown below:

```csharp
public async Task<CustomerDocument> GetCustomerAsync(string customerId)
{
    var results = await _customers.FindAsync(c => c.CustomerId == customerId);
    return await results.FirstOrDefaultAsync();
}
```

- `CustomerResponse` - should add more detailed responses for `OK()`, `NotFound()` and so on.
