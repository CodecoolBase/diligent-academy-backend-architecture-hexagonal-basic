# Tasks

## The background

- We have a greeting service (`src/business/greeting-service.ts`).
- It gets a name and respond it with a nice greeting. 
- We store the greetings to keep the good memories.
- We want to invoke this greeting logic in various ways, like CLI, prompt it to the user or using a REST API.
- We also want to store it in various ways the greetings, like in JSON or TXT formatted files. 
- It is important to keep our software flexible for the new ideas, so we choose the Hexagonal Architecture.

## Task 1: Define the Ports

- This business logic has two ports.
- One is responsible for greeting (primary port). It should define a `greet` method with a name string parameter and should return nothing.
- Another is responsible for storing the message (secondary port). It should define a `store` method with a greeting string parameter and should return nothing. 

## Task 2: Add the ports to the business logic

- The main business logic (`greeting-service.ts`) should **implement** the primary port(s).
- The main business logic should **use** the secondary ports. 
- Always use types/interfaces in the business logic, not concrete implementations.

## Task 3: Implement args input primary adapter

- Implement the adapter in the `args-input-primary-adapter.ts`. 
- It should read the first CLI argument after the file name, and treat it as a name.
- The primary adapters are **using** the primary ports.

## Task 4: Implement the fake store secondary adapter

- Implement the adapter in the `fake-store-secondary-adapter.ts`.
- Fake store is not really store anything just logs out what it would store: `STORE: <something>`.
- The secondary adapters are implementing the Secondary Port Interfaces.

## Task 5: Wire up the things

- Use the `args.ts` to wire up everything.
- This file should initiate the service, the business logic with the proper secondary adapters.
- It also pass the service to the primary adapter to use it.
- Run your code with the `npm run ts -- args.ts Alice` command.