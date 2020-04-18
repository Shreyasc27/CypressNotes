# Section 8: Understand limitations of Frames & Child windows in Cypress

### 35. Handling Child Windows Using Cypress

1. Cypress cannot handle child tab and child window
2. cy,visit() does not support any change of domain.
3. Cannot open www.espncricinfo.com from www.facebook.com
4. prop() is a jquery function and not a Cypress function. Hence below will not work
```
cy.get("#opentab").prop("href")
```
5. We will therefore have to call .then() for prop() to work
```
it('First Test', () => {

    cy.visit("https://rahulshettyacademy.com/AutomationPractice/");
    cy.get("#opentab").then(function(el){
        const url = el.prop("href")
        cy.log(url)
        cy.visit(url)
    })
    

})
```

### 36. Handling Frames With Cypress Using Real Time Example

1. `Frame` - Html document on top of another Html document
2. Installing support for iframe - `npm install -D cypress-iframe` - For Cypress to handle iframes
3. `import 'cypress-iframe'`
```
/// <reference types="Cypress" />
/// <reference types="cypress-iframe" />
import 'cypress-iframe'

describe('First Test Suite', () => {
    
    it('First Test', () => {

        cy.visit("https://rahulshettyacademy.com/AutomationPractice/");
        cy.frameLoaded("#courses-iframe")
        cy.iframe().find("a[href*='mentorship']").eq(0).click()
        cy.iframe().find("h1[class*='pricing-title']").should("have.length", 2)

    })
  
})
```
