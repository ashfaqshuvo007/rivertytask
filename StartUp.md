# StartUp Files

The project start up files like `Startup.cs` and `Program.cs`, are working but I would recommend some changes.

1. `Startup.cs`

    - First, there should be healthchecks in place for `RabbitMQ` and `Mongo` services to check they are available.

    - May be introduce global exception handling for production and logging.

    - Handling `CORS`, as it also exposes an API.

    - Removing code for DB, RabbitMQ configuration block to other files.

    - `RabbitMQ` block specific

        - Credentials exposed in config files. May suggest use of Environment variables in production.

        - Error Handling & Retry mechanisms using `cfg.UseMessageRetry()`

    - Although, this is not wrong per se, but calling `BuilderServiceProvider()` is not necessary to explicitly call as .NET itself manages it. It might create unmanaged instances of providers.

2. `Program.cs`

    - This file is OK.