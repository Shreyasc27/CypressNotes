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

### 21. Handling ASync Promise With Cypress

