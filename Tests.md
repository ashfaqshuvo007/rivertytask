# Tests

In this file, I have illustrated the things I would suggest to change in files related to overall Tests in the application.

- `CustomerAddedConsumerTests`
  - Violation of naming convention. `Consume_ValidCustomerAddedMessage_PersistsCustomer` should be the name of the test.
  - I would mock the `IMongoCollection<CustomerDocument>` instead of live connection to ensure test isolation
  - More assertions `CreationDate`, `IsCreationThroughPromo`
  - Negatice  case tests are missing.
  - Test case for invalid `CustomerId`.

- Missing Tests:
  - Invoice Related Tests.
  - Missing Negative cases.

Overall, testing allows services to go through intensive checks before code goes into production.
