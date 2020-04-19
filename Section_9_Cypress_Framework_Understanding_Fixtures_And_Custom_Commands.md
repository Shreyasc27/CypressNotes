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