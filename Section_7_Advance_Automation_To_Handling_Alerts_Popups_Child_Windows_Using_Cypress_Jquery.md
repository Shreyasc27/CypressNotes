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


### 34. Handling Mouse Over PopUps Using Cypress