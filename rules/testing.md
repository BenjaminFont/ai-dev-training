# Testing Rules

## Core Rules

- New code needs tests. No exceptions.
- Every test is isolated -- no dependencies between tests
- No real API calls, no real DB calls in unit tests

## Naming

Test name describes the expected behavior, not the method:
- `shouldReturnUser_whenIdExists` instead of `testGetUser`
- `renders error message when login fails` instead of `test login component`

## Structure

- Arrange-Act-Assert (backend) / Given-When-Then
- Setup and teardown via framework mechanisms, not manually
- One logical assert per test

## Test Data

- Use factories or builders, don't hardcode inline
- No magic values without explanation
- Shared fixtures only when multiple tests genuinely need identical data

## What NOT to Do

- No business logic in tests (no if/else, no loops)
- No test-order dependencies
- No `Thread.sleep()` or fixed timeouts -- use async utilities
- No tests that are always green (assert must be able to fail)
