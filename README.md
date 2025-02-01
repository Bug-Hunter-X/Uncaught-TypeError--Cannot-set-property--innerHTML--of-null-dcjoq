# Uncommon HTML Bug: DOM Element Access Before Parsing

This repository demonstrates an uncommon bug in HTML that occurs when JavaScript attempts to access and modify a DOM element before the browser has fully parsed and rendered that element in the HTML.  This typically happens when the script executing the DOM manipulation is placed before the element definition in the HTML structure.

## The Bug

The `bug.html` file contains a script that attempts to change the `innerHTML` of a `div` element with the id "myDiv" before the div is defined in the HTML. This results in a `TypeError: Cannot set properties of null (setting 'innerHTML')` because `document.getElementById("myDiv")` returns null as the element doesn't yet exist.

## The Solution

The `bugSolution.html` file demonstrates the correct approach. The script to manipulate the DOM element is placed either:

1. **After** the `div` element definition to ensure the element is ready in the DOM.
2. **Within an event listener** that is triggered after the DOM is fully loaded (e.g. `DOMContentLoaded`). This makes the approach more robust and handles dynamic page content more gracefully.

This example highlights the importance of understanding the order of operations in HTML and JavaScript and how it affects DOM manipulation.