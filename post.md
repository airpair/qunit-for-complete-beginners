QUnit is a javascript framework that you can use to test software. Learning how to use QUnit so that you can test software as you build it will save you time in the long run. Testing will ensure you write the least amount of code needed to get your software to do what it needs to do. It will also save you having to constantly backtrack and fix things once your software starts growing in complexity.

##Step 1: Set Up the Boilerplate
Let's set up with some boilerplate from the [qunit website](www.qunitjs.com). Create a new directory for your testing adventures, and create a file called (for example) `tests.html` with the following content:

```
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>QUnit Example</title>
  <link rel="stylesheet" href="https://code.jquery.com/qunit/qunit-1.18.0.css">
</head>
<body>
  <div id="qunit"></div>
  <div id="qunit-fixture"></div>
  <script src="https://code.jquery.com/qunit/qunit-1.18.0.js"></script>
  <script src="tests.js"></script>
</body>
</html>
```

##Step 2: Set up the sample test
Create a new file called `tests.js` (if you call it something different you will have to change the reference to it on line 12 of the boilerplate).

Inside `test.js` copy and paste the following code:

```javascript
test("this bit should describe, to a human, what the test is for", function() {
	equal( 1, 1);
});
```

The 'equal' bit at the end (known as an assertion) checks that the two things inside the brackets are equal to each other.

## Step 3: Write a Test and Fail

We are going to write a test to check that the header shows up on the page.

1. The first line should explain what the test does for future reference
	```javascript
	 test("check that the header exists", function() {
 	```

2. The next line sets a variable that you can then refer to in line 3. We are looking for an element with the ID 'heading', and storing its text in the variable 'title'.
	```javascript
	var title = document.getElementById('heading').innerHTML;
	```

3. The third line then tests the variable created in line two against what you expect it to be. The equal assertion will only pass if the first parameter matches the second.
    ```javascript
    equal(title, "This is a header");})
    ```

When you put it all together it should look like this:
```javascript
test("check that the header exist'", function() {
    var title= document.getElementById('heading').innerHTML;
    equal(title, "This is a header");
})
```

When you load the page in the browser (the page you saved the boiler plate to, not test.js) it should look like this.

![Fail test](http://i.imgur.com/Y2R8Ow9.png)

The test will fail because we have not added the header to the page. This is exactly what is suppose to happen. This is what the test explains in the red section.

## Step 4: Pass Your Test

Add the following h1 tag with an id of 'header' that says "This is a header" to the page and rerun the test.

```html
<h1 id='heading'>This is a header</h1>
```

A passing test will have a nice green line along it like this:

![Pass test](http://i.imgur.com/je0769P.png)

Failing a test before you wrote the code needed to pass it is the whole idea behind test driven development. Working in this way ensures that
you write the least amount of code needed to get your software to do what it needs to do.

Designing clear user stories for your software will help you decide the tests you will need for the software to work and those tests will then drive the coding process.

Now that you understand the basic anatomy of a test, try putting your new found understanding into practice by developing a test-driven stopwatch with [this tutorial](https://github.com/docdis/learn-qunit).
