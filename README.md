Issue using supertest with Cypress
===

Install the dependencies with:
```
npm ci
```

and run cypress:

```
npx cypress run
```

This generates an error with the stacktrace:

```
     TypeError: The following error originated from your test code, not from Cypress.

  > Object prototype may only be an Object or null: undefined

When Cypress detects uncaught errors originating from your test code it will automatically fail the current test.

Cypress could not associate this error to any specific test.

We dynamically generated a new test to display this failure.
      at Function.setPrototypeOf (<anonymous>)
      at ./node_modules/supertest/lib/agent.js (webpack://cypress-supertest-issue-minimal/./node_modules/supertest/lib/agent.js:53:0)
      at __webpack_require__ (webpack://cypress-supertest-issue-minimal/webpack/bootstrap:19:0)
      at ./node_modules/supertest/index.js (webpack://cypress-supertest-issue-minimal/./node_modules/supertest/index.js:14:14)
      at __webpack_require__ (webpack://cypress-supertest-issue-minimal/webpack/bootstrap:19:0)
      at eval (webpack://cypress-supertest-issue-minimal/./cypress/e2e/spec.cy.js:1:18)
      at eval (http://localhost:33935/__cypress/tests?p=cypress/e2e/spec.cy.js:22369:3)
      at eval (http://localhost:33935/__cypress/tests?p=cypress/e2e/spec.cy.js:22371:12)
      at eval (<anonymous>)
```

This was working fine before supertest version 6.2.4 (which upgrades superagent from 7.1.3 to 8.0.0):

```
npm i supertest@6.2.3
npx cypress run
```
