# Section 10 : Page Object Design And Test Parameterization

### 45. Parameterizing the test data from Json files using each command
`fixture > testuser.json`
```
{
    "name": "Shreyas",
    "gender": "Male",
    "mobiles": ["Nokia Edge", "Blackberry"]
}
```
`Spec.js`
```
it.only('Third Test', function() {
    cy.visit("https://rahulshettyacademy.com/angularpractice/shop")
    cy.wait(2000)

    for (const specificMobile of this.data.mobiles) {
        console.log("Adding to cart - " + specificMobile);
        cy.selectProduct(specificMobile)
        }
    
})
```
`support > commands.js`
```
Cypress.Commands.add("selectProduct", (productName) => { 
    cy.get('h4.card-title').each(($el, index, $list) => {
            
        const phoneName = $el.text()
        //cy.log(phoneName)

        if (phoneName.match(productName)) {
          
            cy.log("Inside Custom Command")
            cy.get('button.btn.btn-info').eq(index).click()
        
        }

      })
})
```
### 46. Test Debugging And Pause With Cypress

1. `cy.pause()` - Pause the test during execution. Can be used for analysis
2. `Time Travel` - View screenshots
3. `Browser Console Log` - Since Cypress runs on browser, logs are generated in the console
4. `.debug()` - For debugging a specific test

### 47.48. Implementing Page Object Design Pattern

1. `export default HomePage;` - To be used to expose the class 'HomePage' to all the other classes in the project
2. `import HomePage from '../pageObject/HomePage'` - Import the 'HomePage' in the js where you want to use it

`Test.js`
```
import HomePage from '../PageObjects/HomePage'

it.only('First Test', function() {

    const homePage = new HomePage()
    cy.visit("https://rahulshettyacademy.com/angularpractice/")
    cy.wait(2000)
    homePage.getNameTextField().type(this.data.name)
    homePage.getSelectGenderDropdown().select(this.data.gender)

})
```
`HomePage.js`
```
class HomePage{

    getNameTextField(){
        return cy.get(':nth-child(1) > .form-control')
    }

    getSelectGenderDropdown(){
        return cy.get("select#exampleFormControlSelect1")
    }

}

export default HomePage;

```