# Section 2: Cypress Installation And Project Setup

### Generate package.json and Get Cypress Dependencies

1. For `node` projects there is `package.json`
2. `npm install` reads `package.json` and performs downloads
3. `npm install cypress --save-dev` - will look for cypress in the npm repository. `--save-dev` will add the entry to `package.json` for future reference.
4. Two ways to run tests -
    a. Command line
    b. Test runner
5. `npm install cypress --save-dev` adds below to the `package.json`
```
"devDependencies": {
    "cypress": "^4.4.0"
  }
```
