# Best Practices

Owner: Sean Teeling
Created time: January 29, 2024 3:15 PM

This doc discusses some best practices in go, particularly around API design. That said, its principles are not limited to go, and can be applied to other programming languages. For other general Go tips, see the [Go proverbs](https://go-proverbs.github.io/)

# API Design

API Design is important, and how it is structured will affect how easy it is to add code to your system. The API of any go package, is the sum of it's exported functions, methods, struct fields, etc. Each package should expose as little as possible, and provide simple API's that **do one thing well**.

## Tests

Tests, at its essence, test the input and the output of a system, with the system itself being a black box. What the scope of a system is depends on the type of test:

- For unit tests, the black-box system is a function or method
- For integration tests, the system might be a function that spans calls to multiple packages, or even interacts with external systems like a database. In this sense the input might be the parameters to a function call, and the output may be a row being updated in a database.
- For E2E tests the black-box is your entire system. The inputs would mimic how a user interacts with the system, and the output is what the user expects as a result, like a Pod being deployed in K8s.
- For each level, avoid "peaking" into the black box.
- [Prefer table-driven tests](https://dave.cheney.net/2019/05/07/prefer-table-driven-tests)
- Prefer e2e tests, then integration tests, then finally unit tests. A codebase that can reach 100% test coverage via e2e tests is inherently more tested than a codebase that has 100% coverage via unit tests and mocking or using fakes.
    - Personally, I only write unit tests as part of my dev flow, when fixing a bug and the e2e tests take too long, or on particularly complex functions. Otherwise, I strive to test the code through e2e tests.
    - If you find your dev cycles are too long because of e2e tests, then you should write smaller unit tests to reduce your dev cycle.
    - Another good use case of unit tests is as documentation. Unit tests clearly communicate what is expected of a function, and can help future users and devs understand the intent of your code.
- Avoid testing internals -- this means you don't need unit tests on unexported funcs. Since these are likely to change more frequently, you should write your test on the exported func, which in turn should exercise any un-exported funcs. You should still be able to achieve high levels of code coverage with this method.
- Avoid mocks as much as possible. Instead, can you write an integration test that ends up testing multiple components? You can stand up http servers internally in tests. Mocks behave as you expect, whereas your code may not, and they ultimately diminish the value of your tests.
    - If you're using mocks, your interface is likely too complicated. It should be faster to write a small struct that implements the desired interface than setting up the code gen required for mocks.

# Best Practices with Interfaces

Interfaces are the glue between API's. It's a declaration of how one package uses another. As such, interfaces should be kept small, to avoid one package depending too much on the internals of another package. They should also be defined where they are consumed (see below).

Good interfaces can promote healthy code, see some tips below.

## Do

- Leverage [dependency injection](https://medium.com/avenue-tech/dependency-injection-in-go-35293ef7b6) in your main package.
- Prefer [composition over inheritance](https://stackoverflow.com/questions/49002/prefer-composition-over-inheritance)
- Keep Interfaces Small. “The larger the interface, the weaker the abstraction” - Rob Pike.
- It’s OK to copy. “A little copying is better than a little dependency” - Rob Pike.
- Interfaces should be defined where they are consumed, not by their implementation -- in fact the implementation should not need to know about the interfaces it satisfies. It only knows about the exported fields and methods.
- You can redefine interfaces as many times as you want. In fact, in many places you likely only need 1 or 2 methods from a struct. Go ahead and redefine those methods in a new interface. This allows you to be much more agile, and make things easier to mock for testing.
- Funcs should accept interfaces and return structs. Don't limit your users by requiring a struct input, or outputting an interface that waters down your struct. Empower your users.
- Don’t create abstractions too early. Prefer the WET principle over the DRY principle. It’s likely not until your third implementation that you’ll be able to see the correct lines of abstraction.
- Create Interfaces to Abstract API calls. API calls change, and aren’t great for unit testing. It’s a good general rule to create an interface for any API calls.
- Use "domain" objects throughout your code. Clients that interact with API's should accept and return domain objects, performing translations to the API calls as needed.
- Compose Interfaces together:

```
type ServiceRepository interface {
   // ...
}

type EndpointRepository interface {
   // ...
}

type Repository interface {
   ServiceGetter
   EndpointGetter
}

```

## Don’t

- Create interfaces for every struct. There’s simply no need. Interfaces are a layer of abstraction, and adding one adds a burden to the developer. It also makes clicking through functions with modern IDE’s more cumbersome. Avoid them if you can.
- Use mocks. Well, sometimes, but prefer Fake's over Mocks
- Map interfaces directly to structs. Rarely should the public methods of a struct and an interface map 1:1. An interface should be exactly the subset of the struct that is needed for the user of that interface.