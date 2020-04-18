# Section 3 : Introduction To Cypress Test Runner And Command Line Features

### 8. What is Cypress Test Runner
1. Open the Cypress Test Runner `npx cypress open`
2. Project structure is already created by Cypress
3. Just clicking on the test in the Test Runner starts the execution of the test
4. Cypress comes packed / bundled with `Mocha`

`Mocha`
1. `describe` - Test suite
2. `it` - Test case

### 9. Build Basic Cypress Test And Run From Test Runner

`First Program`
```
describe('First Test Suite', () => {
    
    it('First Test', () => {

        cy.visit("https://rahulshettyacademy.com/seleniumPractise/#/");

    })
  
})
```
### 10. Running Cypress Tests in Supported Browser

1. Cypress by default bundles `Electron` browser
2. Which browser to run the test in can be determined by selecting the Browser from the dropdown in the top right of the the Test Runner
3. `npx cypress run` runs all the tests in the `integration` folder
4. By default, Cypress runs tests in `Headless` mode - `npx cypress run --spec "cypress/integration/Shreyas/Test1.js"`
5. If Cypress has to be run in `Headed` mode - `npx cypress run --spec "cypress/integration/Shreyas/Test1.js" --headed`
6. If the tests are to be executed on a specific `Browser` - `npx cypress run --spec "cypress/integration/Shreyas/Test1.js" --browser chrome`

### 11. Exploring the Cypress Project Framework Structure

1. `fixtures` - Test data should be stored in `fixtures` and Cypress picks it on its own
2. `integration` - Tests are to be written under this folder
3. `plugins` - Used to handle Cypress events which are nothing but `Listeners` 
4. `support` - Reusable or Customized methods. Methods used across multiple test cases
5. `videos` - Videos of execution can be found here
6. `cypress.json` - Default values from `Test Runner` > `Settings` can be overridden in `cypress.json` 
