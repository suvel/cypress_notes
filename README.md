# cypress_notes

Cypress is greate tool to work and test your application, it was very user friendly and GUI helped me consume the data better while testing.

[link to the teting file](https://github.com/suvel/admin_basic/blob/master/cypress/e2e/landing_page.cy.js)

**Some function that I used:**

### describe()

Help you to describe overall test case

**Example**

```
describe("[🧪] Checking the searching functionality", () => {
....
```

### it()

Help you to describe the steps the are take by you to test the test case.

**Example**

```
it(`Go to Localhost:${portNumber}`, () => {
    ...
  });

  it(`Contains the welcome message in the applications`, () => {
    ...
  });
```

### **cy.visit()**

I have been using the function to visit the server where the application is hosted.

**Example**

```
cy.visit(`http://localhost:3000`);
```

### cy.contains()

I have been using to check if the argument is present in the application, it can also be used to narrow down a component by the text it contain.

**Example**

```
// checking if the web has "Total Rows:1" when ever a row is selected.
cy.contains("Total Rows:1");
// Selecting a specific element inorder to click the same.
cy.get(".Searchbox").contains("Search").click();
```

### cy.get()

I have been using it to select a component using the selectors.

**Example**

```
// Triggering a action on a component
cy.get("tbody > tr > td > input").first().click();
// Fetching the all the children componet
const labels = cy.get("div.LabeledInput").children();
    labels.should("contain", "Name");
// Checking the if a component contain certain number in it
cy.get("tbody tr").should("have.length", 1);
// Pulling a value in a input
cy.get("div.LabeledInput")
      .find('[placeholder="Email"]')
      .invoke("val")
      .then((emailId) => (selectedEmail = emailId));
```

### cy.intercept()

Used for creating a listener to trigger on a specific condition. I have been using it to know when an api have been resolved.

**Example**

```
cy.intercept({
      method: "GET",
      url: "https://geektrust.s3-ap-southeast-1.amazonaws.com/adminui-problem/members.json",
    }).as("recivedMemberData");
cy.visit(`http://localhost:${portNumber}`);
cy.wait("@recivedMemberData").then(async (response) => {
      const recMemLs = response.response.body.length;
     .......
    });
```
