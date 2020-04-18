# Section 4 : Getting Started With Cypress Test Automation

### 12. Cypress Locator Strategies And How to Construct Them?

1. Cypress `only supports CSS selectors`
2. CSS Cheat Sheet - 
* https://appletree.or.kr/quick_reference_cards/CSS/CSS%20selectors%20cheatsheet.pdf
* https://guide.freecodecamp.org/css/tutorials/css-selectors-cheat-sheet/

### 13. Cypress In-Built Plugin in Test Run To Generate Locators

1. `/// <reference types="Cypress" />` - Header to add Cypress Intellisense
2. `;` at the end of each statement is `optional`. Cypress understands both
3. `" or '` is `optional`. Cypress understands both

### 14. Basic Assertion in writing the Tests with Cypress

```
describe('First Test Suite', () => {
    
    it('First Test', () => {

        cy.visit("https://rahulshettyacademy.com/seleniumPractise/#/");
        cy.get(".search-keyword").type("ca")
        cy.wait
        cy.get(".product").should("have.length", 5)

    })
  
})
```

### 15. Handling Invisible Elements with Cypress by Analyzing the Logs

1. Cypress allows `Time Travel` by clicking on each of the executed steps in `Test Runner`
2. User can go to history and check what was the execution status at that point in time
3. `cy.get(".product:visible").should("have.length", 4)` - ':visible' maes sure that only visible elements are considered   