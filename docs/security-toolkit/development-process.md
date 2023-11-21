# Development Process
Ensuring a secure codebase hinges significantly on a well-established development process. This document illustrates a sample development process tailored for implementation in the Papaya build and serves as a companion to our [audit readiness checklist](audit-readiness-checklist.md).

```
Feature Request
 |
 └> Specification
     |
     └> Evaluation (time + complexity + risks)
        |
        └> Implementation
           |
           └> Testing
              |
              └> Deployment
                 |
                 └> Monitoring
```

## Specification
Take note of the categories of variables that influence a feature:
1. User input?
2. Time?
3. Other protocols?
4. Existing state?

## Evaluation
Make dedicated time to evaluate:
1. How long will this realistically take?
2. Is the specification overly complex? Complexity leads to bugs and worse overall code.
3. What are the risks associated with this feature? Spend ample time evaluating this. Consider every module the feature may touch. Then go back through excluded modules and *ensure* they cannot be affected.

You may have millions of dollars at risk already, or will after launch. As such, you **have** to consider how each feature may put *all* of it at risk. The cost of a misstep will likely be in the millions of dollars.

## Implementation
1. Draft a PR.
  - Include the feature request + specification.
2. Write an initial implementation.
  - Get an initial implementation in place.
  - Document all functions' intended behavior for public functions and add inline documentation/comments where necessary.
  - While Clarinet allows for `potentially unchecked data`, avoid simply dismissing this message whenever possible. See [New Safety Checks in Clarinet](https://www.hiro.so/blog/new-safety-checks-in-clarinet) for reference.
  - **Every** line of assembly is documented/commented on.

## Testing
3. Write initial [tests](https://github.com/papaya-dao/reed)
  - Write an initial test for the implementation. Each write to storage should be checked, each revert should be checked. Line-by-line of the implementation, look for storage writes.
  - For non-state changing functions, good practice is have a test contract that inherits the contract that does the math.
  - Use coverage tools to see how well your tests cover your code.
4. Cleanup the implementation.
5. Improve tests, then move back to step 4 based on any found bugs.
6. Utilize [fast-check + clarinet implementation](https://github.com/stacks-network/sbtc/pull/152) for contract fuzzing with the added bonus of property based testing.
  - Analyze the output and return to step 4, if needed.
  - A good fuzz test should consider all valid inputs, and include as many state transition assertions as possible.
7. Move back to step 4 if any bugs are found.
8. Write integration tests.
  - Your feature now likely does exactly what you think it does. In a complex system, that is not enough. Ideally you have tested how it affects the entire system as well.
9. Move back to step 4 if any bugs are found.
10. Cleanup documentation.
11. Setup CI.
  - Continuous Integration via Github Actions help reviewers with basic things.
  - [Clarinet](https://github.com/hirosystems/clarinet#use-clarinet-in-your-ci-workflow-as-a-github-action) can be used in GitHub Actions as part of the CI workflow. 
12. PR review.
  - Minimum two reviewers per PR.
  - The implementer is just the first line of defense. If you are a reviewer, confirm that the implementer followed the above principals as applicable. (test-per-state-transition, test-per-revert, fuzz test, and integration test)
  - Review the documentation and ensure the implementation matches the documented behavior. If it does not, touch base with the implementer and confirm which needs to be updated.
  - Ensure CI passes.
  - Check common missteps. ([e.g., tx-sender usage](https://www.coinfabrik.com/blog/tx-sender-in-clarity-smart-contracts/))


## Deployment
13. Write a deployment script.
14. Write a deployment test.
  - Ensure deployment goes exactly as planned by writing a test testing *every state transition* and make sure no changes unexpectedly happen. One way to accomplish this is the `record` cheatcode. If performing an upgrade to an existing protocol, create a list of your entire protocol's addresses, call record, perform the upgrade. Then, call `accesses` for each address of your protocol. Ensure there are no slots/addresses that unexpectedly changed.
15. Have an audit performed.
  - Consider if this feature/contract needs an audit. Always lean towards being safe rather than sorry.
  - Have the complexity & code size inform if and who should audit your contracts.
16. Implement audit fixes.
17. Setup monitoring service.
  - Have an internal tool that monitors important aspects of your system.
  - 
18. Prepare/update your [Incident Response Plan](incident-response-plan-template.md).
19. Deploy the contract(s).
  - Deployment to `testnet` and `mainnet` can be done directly through [Clarinet](https://docs.hiro.so/clarinet/how-to-guides/how-to-deploy-contracts).

## Monitoring
20. Monitor next couple hours.
  - Use the monitoring service you set up to watch carefully for unexpected behaviors and be ready to take action.
21. Sit back and sip on a glass of wine.