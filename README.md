
# Riverty Home Task

The task is to do a code review of the attached code. Imagine that it was written as a single large initial commit by a more junior colleague. It's meant to run in production as soon as the code review and any necesary corrections are done. 

There is no need to fix the project beforehand. Please point out all concerns you have about the code, no matter how microscopic or how major they are.

## Table of Contents

- [Context](#context)
- [Technology Stack](#technology-stack)
- [Comments](#comments)

## Context

1. The application does two things:
    - Customers being created.
    - Exisiting customers getting invoices.
2. It exposes an API which shows customer information contained in consumed events.

## Technology Stack

The technologies used for the codebase:

- .NET 5.0
- MongoDB
- RabbitMQ

## Comments

In this section, you can find out my comments about the project. I have distributed the analysis across files with detailed explanations.

- [Generic Comments](GenericComments.md)
- [Start Up](StartUp.md)
- [Customer Domain](CustomerDomain.md)
- [Invoice Domain](InvoiceDomain.md)
- [Tests](Tests.md)
