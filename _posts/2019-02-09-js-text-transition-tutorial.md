---
layout: post
title:  "Text transition using Vanilla JS and CSS tutorial"
date:   2019-02-09 20:10:00 +0530
categories: learn coding
author: "Jay Mistry"
comments: true
---

<img src="/blog/assets/images/js-text-tut/cover.png" />

Ever since I used a text effect on my portfolio website, many peers have asked me of what module did I use to acheive the effect of text transition there? But the truth is, I didn't. There was no need, as the implementation is easy itself. You can check out [my portfolio](https:rossoskull.github.io){:target="blank"} website to know what effect I am talking about.

Well, in this post, we are going to learn how to create a text transition effect using vanilla JS and CSS for yourself. To get an idea about what we will be creating take a look at this

<img class='post-image' src="/blog/assets/images/js-text-tut/jstexttut.gif" />

You can visit the online deployment of this code [here](http://rossoskull.github.io/js-changingtext-tutorial/){:target="blank"}. It is hosted on GitHub Pages. If you want to know how to host your static sites using GitHub Pages, you can visit my tutorial on [hosting your site with GitHub Pages](https://rossoskull.me/blog/learn/coding/2019/02/03/gh-pages-tutorial.html){:target="blank"}. Also, the code for this tutorial is available [here](http://github.com/rossoskull/js-changingtext-tutorial/){:target="blank"}.

For this tutorial, we will use three files - `index.html`, `style.css` & `script.js`.

### Contents of the `index.html` file

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <link rel="stylesheet" href="style.css">
    <title>JS Text Transition</title>
</head>
<body>
    <!-- Element where we will display the text -->
    <p id='heading' class=''></p>
    <script src="script.js"></script>
</body>
</html>
```
A minimal HTML file, with links to `style.css` and `script.js`. Also, we created a paragraph element with id 'heading', which we will be targeting for text insertion and updation using JavaScript.


### Contents of the `style.css` file
```css
p {
    /* Style it as you want */
    position: fixed;
    top: 50%;
    left: 50%;
    margin: 0px;
    transform: translate(-50%, -50%);
    font-family: 'Montserrat';
    font-weight: 400;
    font-size: 5em;
    color: rgb(60, 60, 60);

    /* Necessary styles */
    opacity: 1;
    transition: 0.2s linear;
}

.invisible {
    opacity: 0;
}
```

The style rules for the paragraph elements. Not all rules are necessary, only the opacity and transition rules are needed for this method to work. Also, the `invisible` class changes the element's opacity to 0. Initially the opacity is 1, which means that it is completely visible. When the opacity is set to 0, the element becomes completely transparent.

**Note:** I have installed Montserrat font on my system, so there was no need to import it, but if you want to use Montserrat, and don't have it installed, you can visit [here](https://fonts.google.com/specimen/Montserrat){:target="blank"} to get it.

### Contents of the `script.js` file
```javascript
// Values we want to display
let text = ['Apple', 'Mango', 'Orange', 'Watermelon']

// index of the next element we want to display
let currentIndex = 1

window.onload = function () {
    let paragraph = document.getElementById('heading')
    // Set the innerHTML to first value
    paragraph.innerHTML = text[0]

    setInterval(function() {
        //  Fade out our element
        paragraph.className = 'invisible'

        setTimeout(function() {
            paragraph.innerHTML = text[currentIndex]

            // Circular incrementation of currentIndex variable
            currentIndex = ( currentIndex + 1 ) % text.length

            setTimeout(function() {
                // Fade in our element
                paragraph.className = ''
            }, 50)
        }, 200)
    }, 3000)
}
```
#### **Explaination**
The `text` variable contains an array of all the strings we wish to display in the target element. Also we set the `currentIndex` variable to 1, as we will be inserting the first element ( indexed 0 ) of `text` variable manually.

Then we use the `onload` property of `window` object, to trigger our transition function as soon as the document has finished loading. We target the element where we want to display our strings as `paragraph`, and set it's `innerHTML` property to `text[0]` i.e. the first element of the `text` array.

Then we create an interval which calls a function every 3000 milliseconds i.e. 3 seconds. This is the time for which the text will be shown to the user. At the start of the interval, we add an `invisible` class to our element. As per the transition CSS rule of the element, it will take our element 200 milliseconds to completely fade out, so we set a timeout of 200 milliseconds to wait for our element to completely fade out, and then we change the `innerHTML` to next value of `text`.

We also set the `currentIndex` to the next element in a circular manner. We want it to iterate circularly, so we add a modulus operator after the increment. Our `text` array has a length of 4, so the `currentIndex` can take values 0, 1, 2, 3. When the `currentIndex` value is 3, after the next increment, it becomes 4, which is out of bounds for our array, so we use '%' operator, which returns the remainder. So 4%4 becomes 0, and we start from there again.

For this operation, we give it a timeout of 50 milliseconds ( more than needed ). Then we set the `className` property to an empty string i.e. we remove the `invisible` class. Now, `paragraph` element's opacity becomes 1, and due to transition time being 200 milliseconds, it slowly fades in in 200 milliseconds.

As we used `setInterval` function, the function will be called infinitely, but if you intend to stop the animation, you can using the following method.
```javascript
// Create our interval, and store it in a variable
let interval = setInterval(...)

// Remove the interval using clearInterval()
clearInterval(interval)
```

That's it, now you've created your own text transition effect using Vanilla JS and CSS. If you face any difficulties, or have any improvements to share, you can comment down below. Thank you for your time!

Adios folks!