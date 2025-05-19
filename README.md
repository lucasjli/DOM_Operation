# DOM operation

# Task Goal 
Demonstrate a basic understanding using Javascript to:
* Manipulate the DOM of a HTML document.
* Parse and generate content from data stored in XML.
* Parse and generate content from data stored in JSON. 

## Preamble
1. Fork this repository using the button at the top of the project page.
2. Make sure that the visibility of your project is private. (Settings > expand Permissions > Project visibility: Private; Save changes).  *Note: Class teachers and tutors will still have read access to your project for marking purposes.*
3. Clone the new repository to your computer using Git.  Store the repository in your COMPX575 directory.
4. Remember to commit and push regularly as you work on the project!  

## Useful Resources
Useful tutorials on Javascript DOM methods:
* https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction
* http://www.w3schools.com/js/js_htmldom_methods.asp

Example html tables:
* https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table#Examples

### Part One
1. Open *intro.html* in a text editor.  In *\<script> ... \</script>*, add the following code.
```
var pElem = document.createElement("p");
var pText = document.createTextNode("This is the first paragraph");
pElem.appendChild(pText);
document.appendChild(pElem);
```
Save the file and reload it in the browser.  Why doesn't the text appear?  Look at the error message in the error console (in Firefox: Menu -> Developer -> Web Console).

2. Change *document.appendChild(pElem);* to *document.body.appendChild(pElem);*.  Save the file and reload it in the browser.  You should see the paragraph appear.  
3. Right click the paragraph -> "Inspect Element".
4. Count the number of child and grandchild elements the *<html>* element has.
```
var children = document.documentElement.children;
var total = children.length;
for (var i = 0; i < children.length; i++) {
    var child = children[i];
    total += child.children.length;
}
alert(total);
```

### Part Two
Still in *happy-english-learning.html*.  For questions one to three, we will work on the element with ID *flaxHeader*.  Use the method *document.getElementById* to obtain a reference to this element.
1. Use the JavaScript method console.log to display the following information about the *flaxHeader* element:
    * All attributes and their values (use the *attributes* property),
    * The number of children,
    * The first elements child's tag name and
    * The parents *id*
2. Add a new attribute to *flaxheader* named *seq* with the value *"2"*.
3. Capitalize the first letter of each *\<span\>* element in *flaxHeader*.

Use *console.log* to display:

4. The value of the href attribute of the first *\<link>* element.
5. The number of *\<img>* elements that do not have a style attribute.

Use the methods *document.createElement*, *appendChild*, *insertBefore* and *removeChild* to update the HTML content:

6. Append a new activity: 
```
<li><a href="matching-text">Matching Text</a></li>
```
into the first *\<ul class="activity-list">*.

7. Insert a new activity:
```
<li><a href="split-sentences">Spit Sentences</a></li>
```
into the fifth position in the last *\<ul class="activity-list">* (so it is between "Scrambled Sentences" and "Word Guessing").

8. Remove all the children of the second *\<li class="song-li">*.

### Part Three
Open *xml.html* in a text editor and write JavaScript code to convert the XML string to a HTML table as below and append it to the end of the *\<body>* element.
You need to first parse the XML string into an XML DOM object using:
```
var parser = new DOMParser();
var xmlDoc = parser.parseFromString(xmlString, "text/xml");
```

<table border="1">
    <thead>
        <tr>
            <td> id </td>
            <td> title </td>
            <td> linkDocCount </td>
            <td> linkOccCount </td>
        </tr>
        <tr>
            <td> 17362 </td>
            <td> Kiwi </td>
            <td> 59 </td>
            <td> 60 </td>
        </tr>
        <tr>
            <td colspan="4"> <b> Kiwi </b> are <a href="">flightless bird</a>s endemic to <a href="">New Zealand</a> ... </td>
        </tr>
        <tr>
            <td> 509080 </td>
            <td> Kiwi (people) </td>
            <td> 38 </td>
            <td> 41 </td>
        </tr>
        <tr>
            <td colspan="4"> <b> Kiwi </b> is the nickname used internationally for <a href="">people from New Zealand</a> ... </td>
        </tr>
    </thead>
</table>

* There are useful resources listed above that might help.
* The *\<definition>* element contains HTML, which you must render as HTML (clickable links and so on).  Inserting the XML element into the HTML document will not work.  The simplest solution is to use the *innherHTML* property to convert the contents of the *\<definition>* element to a string and then assign the result to the *innherHTML* property of an appropriate HTML element such as *\<td>*
* The column names are provided in the array *attrs*.  You **must not** hard code these attribute names (they must not appear anywhere in the script except in the array declaration).

### Part Four
Open *json.html* in a text editor and write JavaScript code to parse the JSON string into a JavaScript object and make the HTML document look as below.

**Text:** Kiwi <br>
**LinkDocCount:** 168 <br>
**LinkOccCount:** 177 <br>
**Senses:** <br>

| id | title | linkDocCount | linkOccCount |
| ------ | ------ | ------ | ------ |
| 17362 | Kiwi | 59 | 60 |
| 509080 | Kiwi (people) | 38 | 41 |

As in the previous part, the column names are provided in the array *attrs* and you must not hard code them.

