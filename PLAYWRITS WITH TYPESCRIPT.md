##### PLAYWRITS WITH TYPESCRIPT







###### Day 1 

\--------



Installation:- npm init playwright@latest



* It will install the latest playwright latest version.
* By default Typescript select for playwright
* if needed GitHub can link here it self
* To install browsers :- npx playwright install





Inside that directory, you can run several commands:



* &#x20;npx playwright test

&#x20;   Runs the end-to-end tests.



* npx playwright test --ui

&#x20;   Starts the interactive UI mode.



* npx playwright test --project=chromium

&#x20;   Runs the tests only on Desktop Chrome.



* npx playwright test example

&#x20;   Runs the tests in a specific file.



* npx playwright test --debug

&#x20;   Runs the tests in debug mode.



* npx playwright codegen

&#x20;   Auto generate tests with Codegen.



* npx playwright test

&#x09;To Run the test Scripts



###### 

###### **Folder Structure** 

**----------------------**



**Test folder** :- here we will store the test case file



Note:- whenever we create new file test case file , file extension should be **spec.ts -> typescript , spec.js -> javascript**



**example :- example.spec.ts**





**playwright Config:-**

Its is configuration File if we cant configure the browser or works



workers means : - Browsers like chrominu,firefox,WebKit



* If we don't want execute other browsers we can comment out 





testDir :- './fil name '





##### **Package.json**

**-------------------**

* Its is like POM file , its shows the dependencies in file.





**Version :-** npx playwright --version



npx :- node package executer

npm:- node package manager







**Note** :- Whenever the we write the code need to write inside **tests** folder if we want change u need to config testDir file 





##### 

##### **Practical** 

**----------------**



&#x20;

Create file in tests folder 



* test, expect is built-in functions in playwright, its is package.



**import {test,expect } from '@playwright/test';** -> whenever we create fist line should be there 



**test()** -> test will take two parameter first will be 'Tittle', second is 'Function (arrow or named or anonymous)'



syntax:- 

test('tittle',()=>{

//step1

//step2

//step3



})





### Verify the page Title



test("Verify the page Tittle",async ({page})=>{

&#x20;	await page.goto("http://www.automationpractice.pl/index.php");

&#x09;let title:string= await page.title();

&#x09;console.log("Title:",title);

&#x09;await expect(page).toHaveTittle("My Shop");

&#x09;

})

* When ever we have promise we need to use Await and Async 



**()=>** inside we pass parameters or fixtures 

**fixture :**- global variable :- page, Browser 

**page:**- whatever we see in the browser we call it as page fixture, 

if we want launch url or validation use page fixture

page.goto -> open this url on particular page 

//page.method

to verify the page we have **assertion** with the help of **expect** we can validate it pass or fail.





#### Sync And Async 

\-------------------------



**Synchronous :-** step 1 complete step2 will execute one after another step will executes 

step1 complete > step2 complete >step3 complete





**Async :-** if one task is process also another task will do parallel

execute all the task prallely



step1 inprogress -> step2 will also we inprogess -> step 3 will also we inprogess



if we dealing with any background task without it complete we cant process means there we will perform Sync process.



Promise:-

* Pending
* Resolved
* Fulfilled



**await:-** we wait for previous step to complete before going to next step



* if any of step is performing **promises** we will use **await**

&#x20;





In every statement in Automation Its involved in the Promises

WE need to add await

* if we want we **await**  we need to use **async**
* without **Aysnc** , **await** will not wok





**npx playwright test :**- It By default tests folder all files wll execute 



Note :- By Default Playwrite will excecute **headless mode** means it will work in background/backend it self.





Running 3 tests using 3 workers



1 worker means 1 single browser instance.



1worker \* No. of test -> 3 workers \* 1 test = 3 tests

&#x20;

\--> Headed Mode :- **npx playwright test --headed**





##### Verify the URL of the Page

\----------------------------------------





import { test, expect } from "@playwright/test";



test("Verify the page Title", async ({ page }) => {

&#x20;   await page.goto("https://testautomationpractice.blogspot.com/");



&#x20;   const url: string = await **page.url();**

&#x20;   console.log("URL:", url);



&#x20;   await expect(page).toHaveURL("https://testautomationpractice.blogspot.com/"); --> FULL URL

&#x20;   await expect(page).toHaveURL("/testautomationpractice/"); --> PARTICIAL URL 



});



\--> **npx playwright test** --> it will excecute all file in tests folder 

\--> **npx playwright test Day1.1.spec.ts** -> it will excute only spceifed file  

\--> **npx playwright test** --project=chromium -> to run specific broswer

\--> **npx playwright test Day1.1.spec.ts** --project=chromium -> to run specific broswer



##### Mutiple file Run 

\-------------------------



**--> npx playwright test Day1.1.spec.ts Day1.spec.ts --project=chromium** --> mutiple file names can specify here





##### **Matching with file name we will run File**

**------------------------------------------------------------**



**--> npx playwright test -g "Verify" -->** where in the tittle verify it will run that test

\--> **npx playwright test -g "URL" ->  -g means global wherever Url matches it will exceute all** 







#### **Run In UI Mode**

**-----------------------------**



\--> npx playwrigt test --ui



we can run whichever file we can by selecting there

* It will collects the lots of info , we can do time travel means back and front we can move execute





#### 

#### **Debug Mode**

**-------------------**



**-> npx playwright test Day1.spec.ts --debug**



* Open Browser which ever the file we specified we can execute line by line 
* Step Over -> F10 --> step by step we can excute
* 





WebSocket -> playwright uses

W3C Protocol -> Selenium 4 WebDriver



HTTP call works b/w the Request - response 



* In playwrights one connection open ,Closes after exceute all test cases.
* In Selenium For each and every request it will open closes for all  test cases.
* In Playwright no specific browser driver by itself it will communicate with Browsers.













# Day 2

\----------------



##### Locators

\-------------



Playwright itself its have own built-in locators -> 1st priority

Css -> 2nd priority

X-path -> 3rd priority



* Locators are able identify the Web Element -> Auto-Waiting and retry-ability.
* Locators are the central piece of Playwright's auto-waiting and retry-ability. In a nutshell, locators represent a way to find element(s) on the page at any moment.



##### 3 types of locators

\----------------------------

##### 1.Built-in locators

##### 2\. CSS locators

##### 3\. X-path



##### 1.Built-in locators

\------------------------------

* ###### **page.getByRole()** to locate by explicit and implicit accessibility attributes.
* ###### **page.getByText()** to locate by text content.(Non-interactive Elements)
* ###### **page.getByLabel()** to locate a form control by associated label's text.
* ###### **page.getByPlaceholder()** to locate an input by placeholder.
* ###### **page.getByAltText()** to locate an element, usually image, by its text alternative.
* ###### **page.getByTitle()** to locate an element by its title attribute.
* ###### **page.getByTestId()** to locate an element based on its data-testid attribute (other attributes can be configured).





###### 



##### **Locators in Playwright:** 

* Identifies the elements on the page
* Dom - Document Object Model -> Html Dom is different and playwright dom is different 
* Dom in playwright is Api interface provided by browser.







1. ###### **page.getByAltText()** to locate an element, usually image, by its text alternative.
* Its used most for finding images
* Identify images (and similar elements) based on the alt attribute.
* use this locators when your element supports alt text such as img and area elements.
* 



import {test,expect} from '@playwright/test';





test("verify the Playwright Locators",async({page})=>{

&#x09;await page.goto("https://demo.nopcommerce.com/")

&#x09;// await page.getByAltText("nopCommerce demo store")

&#x20;   const logo:Locator = await page.getByAltText("nopCommerce demo store");

&#x20;   console.log("Logo:",logo);

&#x20;   await expect(logo).toBeVisible();

&#x09;

});



\->Locators -need to import because its fixture.

\-> await -if the returning something or promise or action we will use await

\-> await will not use if its not doing any action





**toBeVisible():-** to verify the image is visible or not in page, await is required for toBeVisible() method













###### **2. page.getByText()** to locate by text content.



* <p>text</p> / <div>text</div> /<span>text</span>
* text wrapped inside the tag 
* it is used to find the non interactive text in page
* By using the text/Substring/Regular expression/Full String.
* Case Sensitive by default if we want ignore 



test("Verify the text in page",({page})=>{

&#x09;await page.goto("")

&#x09;const text:Locator=page.getByText("Submit Form")

&#x09;await expect(text).toBeVisible()

&#x09;//or

&#x09;await expect(page.getByText("Submit Form")).toBeVisible() -> instead of storing in one variable we use directly in expect

&#x09;await expect(page.getByText("Submit Form")).toBeVisible()  -> Full text

&#x09;await expect(page.getByText("Submit Fo")).toBeVisible() -> SUB STRING

&#x09;await expect(page.getByText(/submit\\s+form\\s/i)).toBeVisible()



})



Note :-

\\s -> space

/i -> ignores case sensitive text







###### 3\. **page.getByRole()** to locate by explicit and implicit accessibility attributes.





* Role is not attribute of an element, Sometimes may have attribute in HTML
* Role includes Buttons, Checkboxes, Heading, links, list, tables and many more and follow W3C specifications for ARIA Role
* Implicit means Role and Tag name is same eg:- Checkbox
* Explicit means role and tag name is differ eg :- Heading, Button,





Syntax:- page.getByRole("ARIA Tag",{ name:"text"}).method()



* await page.getByRole("link",{name:"Primary Action"}).click() -> PERFORM ACTION
* await expect (page.getByRole("link",{name:"Primary Action"})).toBeVisible();







###### **4. page.getByLabel()** to locate a form control by associated label's text.

* Its mainly used for form tag -> form labels like first name / dob/ address etc.
* fill() is method to insert data in that textbox /input





Example :- 

await page.getByLabel('Email Address:').fille("ss@gmail.com");

await page.getByLabel('Password:').fille("Change@123");

await page.getByLabel('Your Age:').fille(20);







###### **5. page.getByPlaceholder()** to locate an input by placeholder.



* Finds elements with a given placeholder 
* 



Example :

await page.getByPlaceholder("Enter your full name").fill("Apple");





###### **6. page.getByTitle()** to locate an element by its title attribute.

* When to use: When Your Element has a meaningful title attribute



Example :	

await page.goto("url")

const link:Locator=page.getByTitle("Home page link");

expect(link).toHaveText("Home")

###### 



**--**

await expect(page.getByTitle("Home page link")).toHaveText("Home");

await expect(page.getByTitle("HyperText Markup Language")).toHaveText("HTML"); 









###### **7. page.getByTestId()** to locate an element based on its data-testid attribute (other attributes can be configured).



* Its is rearly used, it locate based on data testid attribute id should be there.
* example : -<button data-testid="directions">Itinéraire</button>
* await page.getByTestId('directions').click();



Customisation we can do it:-

* When to use :- When text or role-based locators are unstable or not suitable



example:- verify by data-testid attribute in page and value



&#x20;await expect(page.getByTestId("profile-email")).toHaveText("john.doe@example.com");

&#x20;await expect(page.getByTestId("profile-name")).toHaveText("John Doe");



\--if the attribute name changed 



* we need to changes in configuration file, use:{ trace:'on-first-retry',testIdAttribute:'data-pw' }.
* new attribute name should pass in id attribute instead of changing the code instead of testId we can use our customise name need add.
* 

&#x20;  



#### 

#### XPath Locators

\---------------------------



* XPath stands for Xml path language.
* It is a syntax used to navigate through elements and attributes in an XML document.
* In web automation, Path is used to locate elements on a webpage by their structure and attributes.
* URL Practice :- https://demowebshop.tricentis.com/
* type of Xpath :- 1. Absolute Xpath(Full XPath)   2.Relative Xpath(Partial XPath)



1\. Absolute XPath (Full XPath)



* An Absolute XPath provides the full path from the root of the document to the target element.
* It starts with a **single /**, which represents the root node.
* Example: /html/body/header/div/div/div\[2]/div/input
* Note :- If we can structure its not works, so doesn't recommend to use 



2\. Relative XPath (Partial XPath)



* A Relative XPath is a more flexible way of finding an element. It **directly jumps** to the element using attributes, without starting from the root.



* It **starts with //**, which allows XPath to search anywhere in the document.
* Example: //\*\[@name="search"]















































































&#x20;                                                                                            







