# Section 5 : Deep Diving Into Cypress And Its Asynchronous Nature

### 17. Understanding Get and Find Commands with Cypress

1. For `Parent-Child Chaining`, make use of `find`
```
cy.get(".products").find(".product").should("have.length", 4)
```
2. `eq` - Find element based on index 
```
cy.get(".products").find(".product").eq(2).contains("ADD TO CART").click()
```

### 18. Grabbing the Text for Validations using Cypress Text Command

1. Iterate over list of items using `each`, find element by text and then perform action 
2. Traversing / Iterating over the item of array elements
```
cy.get(".products").find(".product").each(($el, index, $list) => {
            
            const vegetable = $el.find("h4.product-name").text()

            if (vegetable.includes("Capsicum")) {
              
                $el.find('button').click()
            
            } 

          })
```

### 19. Cypress Asynchronous Nature And Its Promise Handling

1. Javascript is asynchronous. Cypress has its engine written such that steps execution will be synchronous
2. Cypress provides `synchronous execution`. But it is `Asynchronous`
3. Cypress will `Queue all the commands` and make sure to execute them in order
4. `Asynchronous` - Every step asynchronous returns a `Promise`
5. `Promise` has 3 stages -
    * `Resolved` - Step is completed
    * `Rejected` - Step errored out
    * `Pending`  - Step is yet to be executed
6. `.then()` makes sure that the step is Resolved before moving to the next step
7. Cypress has done the job of concatenating `.then()` for every step

### 20. Understanding the Difference Between JQuery Method And Cypress Commands

1. This will not work. Because as per the logic of `Promise`, we are voilating the implementation provided by Cypress
```
const logo = cy.get(".brand")
cy.log(logo.text())
```
2. To make the above code snippet work, we will have to explicitly resolve promise
```
cy.get(".brand").then(function(logo)
{
    cy.log(logo.text())
})
```
3. `cy.log` is used for printing logs
4. `cy.get(".search-keyword").type("ca")` - In case of Cypress Commands, when we call 2 Cypress commands back to back; `Cypress will resolve 1st commands promise, wait for it and then resolve 2nd`.
5. Cypress supports `JQuery`. `.text()` is a JQuery method.
6. `cy.get(".brand").text()` - `.text()` method returns the content of the selected element.
7. `Non Cypress commands do not resolve Promise by themselves. We have to manually resolve them using then()`

### 21. Handling ASync Promise With Cypress

