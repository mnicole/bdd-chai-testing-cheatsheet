# Nightwatch BDD Testing based on Chai Expect Library Cheat Sheet
[API Documentation](http://nightwatchjs.org/api/#expect)

## Testing Base
Use the below as a start for each test. The text below as shown as "login working" should be a quick description of what your test is doing so when the test runs, we know what it is testing.

```
module.exports = {
  'login working': function (client) {
    client
      .url('http://localhost:3000')
      // PUT THE TESTS HERE! (SEE OPTIONS BELOW)
  }
}
```

## Options

#### Helpers
| Helper  | Options     | Code/Example         |
|---|---|---|
| Go to a URL | (url I want the test to happen on) | .url('http://localhost:3000') |
| Pause | (milliseconds) | .pause(1000) |
| Resize the window | (new window width, new window height) | .resizeWindow(1000, 800) |
| Close a window | | .closeWindow() |
| Save a screenshot | (where you want it saved) | .saveScreenshot('/path/to/filename.png') |
| Wait for an element to be or not be present before moving on | (element, milliseconds) |  .waitForElementPresent('.myDiv', 1000)<br>.waitForElementNotPresent('.myDiv', 1000) |
| Wait for an element to be or not be visible before moving on | (element, milliseconds) |    .waitForElementVisible('.myDiv', 1000)<br>.waitForElementNotVisible('.myDiv', 1000) |
| Close a window | | .closeWindow() |

#### Actions (Commands)
| Action   | Options           | Code/Example       |
|---|---|---|
| Click something | (element I want clicked) | .click(‘button’) |
| Set a value of something (usually an input) | (element I want the value to be put into, the value I want entered) | .setValue(‘input[type=text]’, ’sample input’) |
| Submit a form | (form element I want submitted) | .submitForm(‘form.login’) |
| Clear a value | (element you want cleared) | .clearValue('input[type=text]') |
| Get element size | (element) | .getElementSize('.myDiv', function (result) {<br>// tests here<br>// returns result.value.width and result.value.height`<br>} |
| Get element's location on the page | (element) | .getLocation('.myDiv', function (result) {<br>// tests here <br>// returns result.value.x, result.value.y<br>} |
| Get element's visible text | (element) | .getText('.myButton', function (result) {<br>// tests here<br>// returns result.value<br>} |
| Get element's value (input) | (element) | .getValue('form input[type=text]', function (result) {<br> // tests here<br> // returns result.value<br>} |

#### Things to Test (Expect)
| Test        | Options           | Code/Example  |
|---|---|---|
| Check to see if an element has certain text or does not have certain text | (element I want checked)<br>(text I expect to see)<br>(milliseconds) | .expect.element('.main').text.to.equal('My text exactly matched')<br>.expect.element('.main').text.to.contain('some text within my text')<br>.expect.element('.main').text.to.not.equal('This text should not be found)<br>.expect.element('.main').text.to.not.contain('This text should not be in my element')<br>.expect.element('.main').text.to.not.equal('This text should not be found).before(1000)<br>.expect.element('.main').text.to.not.equal('This text should not be found).after(1000)|
| Check for a CSS property on an element, or check that an element does not have it | (element I want checked)<br>(css property I expect)<br>(css value I expect) | .expect.element('.main').to.have.css('background-color).which.equals('black')<br>.expect.element('.main').to.have.css('background-color).which.does.not.equals('white') |
| Check to see if an element is the type you expected | (form element I want submitted) | .expect.element('.main').to.be.a.('div') |
| Check to see if an element is enabled, not enabled, enabled before a time period passes | (checkboxes)<br>(element)<br>(milliseconds) | .expect.element('.toggles').to.be.enabled<br>.expect.element('.toggles').to.not.be.enabled<br>.expect.element('.toggles').to.be.enabled.before(100) |
| Check to see if an element is present on the page, not present, or not present before a time period passes | (element)<br>(milliseconds) | .expect.element('.main').to.be.present<br>.expect.element('.main').to.not.be.present<br>.expect.element('.main').to.not.be.present.before(100) |
| Check to see if an element is selected (options or inputs), not selected, or selected before a time period passes | (element)<br>(milliseconds) | .expect.element('.input').to.be.selected<br>.expect.element('.input').to.not.be.selected<br>.expect.element('.input').to.be.selected.before(100) |
| Check to see if an element is visible, not visible, or visible before a time period passes | (element)<br>(milliseconds) | .expect.element('.main').to.be.visible<br>.expect.element('.main').to.not.be.visible<br>.expect.element('.main').to.be.visible.before(100) |
