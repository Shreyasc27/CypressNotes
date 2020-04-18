# Section 6 : Handling Web Control UI Using Cypress

### 23. How To Verify And Automate Checkboxes Using Cypress

1. `Behavioral` - `be.`
2. `Comparisons` - `have.`
```
describe('First Test Suite', () => {
    
    it('First Test', () => {

        cy.visit("https://rahulshettyacademy.com/AutomationPractice/");
        cy.get("#checkBoxOption1").check().should("be.checked").and("have.value", "option1")
        cy.get("#checkBoxOption1").uncheck().should("not.be.checked")

    })
  
})
```

3. Selecting multiple checkboxes
```
 cy.get("input[type='checkbox']").check(["option2", "option3"])
```

### 24. Handling Static Dropdowns Using Select Command With Cypress

`Static Dropdwons`
```
cy.get("select#dropdown-class-example").select("option3").should("have.value", "option3")
```


### 25. Handling Dynamic Dropdowns With Each Command Iteration

`Dynamic Dropdown`
```
cy.get("#autocomplete").type("ind")
cy.get(".ui-menu-item div").each(($el, index, $list) => {
    
    if ($el.text() === "India"){
        
        $el.click()
    
    } 

    })
cy.get("#autocomplete").should("have.value", "India")
```
### 26. Handling Visible And Invisible Elements Using Assertions In Cypress
```
cy.get("#displayed-text").should("be.visible")
cy.get('#hide-textbox').click()
cy.get("#displayed-text").should("not.be.visible")
cy.get('#show-textbox').click()
cy.get("#displayed-text").should("be.visible")
```

`Radiobutton`
```
cy.get("[value='radio2']").check().should("be.checked")
```