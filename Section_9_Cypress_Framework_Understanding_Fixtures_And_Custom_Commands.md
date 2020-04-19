# Section 9: Cypress Framework Part 1- Understanding Fixtures and Custom commands

`Test Hooks`
1. Provided by `Mocha`
```
before(function(){

})

beforeEach(function(){

})

afterEach(function(){
    
})

after(function(){
    
})

```

`Fixtures`
1. Cypress can pick up the data from the fixtures folder and use the data
2. Have to resolve the promise to get the data that fixture returns
3. `this.data` - `this` refers to full class. Variable `data` is defined. Scope of the variable is the full class.

```
/// <reference types="Cypress" />

describe('Angular Practice Test Suite', () => {
    
    before(function(){

        cy.fixture('testuser').then(function(data){
            this.data = data
        })
        
    })

    it('First Test', function() {

        cy.visit("https://rahulshettyacademy.com/angularpractice/")
        cy.wait(2000)
        cy.get(':nth-child(1) > .form-control').type(this.data.name)
        cy.get("select#exampleFormControlSelect1").select(this.data.gender)

    })
  
})
```
`testuser.json`
```
{
    "name": "Shreyas",
    "gender": "Male"
}
```

> For all `Behaviours` use `be.`

> For `Retriving Property` use `should('have.value','')`

> Question yourself if it is a `Behaviour` or `Property`

```
/// <reference types="Cypress" />

describe('Angular Practice Test Suite', () => {
    
    before(function(){

        cy.fixture('testuser').then(function(data){
            this.data = data
        })
        
    })

    it('First Test', function() {

        cy.visit("https://rahulshettyacademy.com/angularpractice/")
        cy.wait(2000)
        cy.get(':nth-child(1) > .form-control').type(this.data.name)
        cy.get("select#exampleFormControlSelect1").select(this.data.gender)

    })

    it('Second Test', function() {

        cy.visit("https://rahulshettyacademy.com/angularpractice/")
        cy.wait(2000)
        cy.get(':nth-child(1) > .form-control').type("Shreyas")
        cy.get(':nth-child(4) > .ng-untouched').should("have.value", "Shreyas")
        cy.get(':nth-child(1) > .form-control').clear()
        cy.get(':nth-child(1) > .form-control').type("S")
        cy.get(':nth-child(4) > .ng-untouched').click()
        cy.get(':nth-child(1) > .form-control').should('have.attr', 'minlength', '2')
        cy.get('#inlineRadio3').should('be.disabled')

    })
  
})

```

`Custom Commands`

1. `Custom methods` should be present in `support` folder

/// <reference types="Cypress" />

describe('Angular Practice Test Suite', () => {
    
    it.only('Third Test', function() {

        cy.visit("https://rahulshettyacademy.com/angularpractice/shop")
        cy.wait(2000)
        cy.selectProduct("Nokia Edge")
        
    })
  
})
```
`Support > Command.js`
```
Cypress.Commands.add("selectProduct", (productName) => { 
    cy.get('h4.card-title').each(($el, index, $list) => {
            
        const phoneName = $el.text()
        cy.log(phoneName)

        if (phoneName.match(productName)) {
          
            cy.log("Inside Custom Command")
            cy.get('button.btn.btn-info').eq(index).click()
        
        }

      })
})
```