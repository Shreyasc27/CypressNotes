# Section 7: Advance Automation to handling Alerts,popups, Child Windows using Cypress-Jquery

### 28. How Cypress Auto Handles Alerts In Webapps?

1. Cypress auto accepts alerts / popups
2. Cypress has the capabilities to handle Browser Events
3. `window:alert` event will be triggered on alert opening
```
cy.on("window:alert", (str) =>{
    expect(str).to.equal("Hello , share this practice page and share your knowledge")
})
```
4. `window:confirm`
```
cy.on("window:confirm", (str) =>{
    expect(str).to.equal("Hello , Are you sure you want to confirm?")
})
```

### 29. Handling Child Tabs With A Combination Of Cypress & JQuery Commands

1. Cypress does not provide the capability to work on Child Tabs
2. Since Cypress cannot open another tab, it will manipulate the DOM to remove 'target="_blank"' and thereby open the new page in the same browser window
3. This will be acheived using .removeAttr() of jquery
```
cy.get("#opentab").invoke("removeAttr", "target").click()
```

### 30. Naviagting Browser Controls Using Cypress
1. `cy.go("back")` - To go back to the prevvious page
2. `cy.go("forward")` - To go to the next page
3. Validate the `current url` - To get the current url
```
cy.get("#opentab").invoke("removeAttr", "target").click()
cy.wait(2000)
cy.url().should("include", "index")
cy.go("back")
cy.wait(2000)
cy.go("forward")
```

### 32. Handling Web Tables With Cypress Using Each Command

1. `tr td:nth-child(2)` - To get the contents of the 2nd column
```
describe('First Test Suite', () => {
    
    it('First Test', () => {

        cy.visit("https://rahulshettyacademy.com/AutomationPractice");
        
        cy.get("tr td:nth-child(2)").each(($el, index, $list) => {
            
            const courseName = $el.text()
        
            if (courseName === "Master Selenium Automation in simple Python Language") {
              
                const coursePrice = cy.get('tr td:nth-child(2)').eq(index).next().then(function(price){

                    expect(price.text()).to.equal("25")
                
                })
            
            }

          })

    })
  
})
```


### 34. Handling Mouse Over PopUps Using Cypress
1. `.invoke("show")` - Does `mouse hover by invoking jQuery show` and clicks on the `Top`
```
it.only('Second Test', () => {

    cy.visit("https://rahulshettyacademy.com/AutomationPractice");
    cy.get(".mouse-hover-content").invoke("show")
    cy.contains("Top").click()
    cy.url().should("includes","top")
    
})
```
2. Cypress can click on the hidden element as well. `{force:true}` make sure that hidden elements are also displayed
```
cy.contains("Top").click({force:true})
```