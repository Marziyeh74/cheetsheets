## Introdunction (Cascading Style Sheets)
زبانی برای استایل دهی به HTML و تغییر نمایش element های آن.

## CSS Selectors:

### Simple selectors:
- select elements based on name, id, class

- grouping selectors. univeral selector (*)


example :
```

p.center {
  text-align: center;
  color: red;
}
 h1, h2, p {
  text-align: center;
  color: red;
}
``` 

### Combinator selectors :

- Descendant combinator (space) :  (div p )
  تگ های p که یکی از اجداشان div باشد
- Child combinator (>) : (div>p):
  تگ p که اولین والدش div باشد
- Next sibling combinator (+) : (div + p):
  تگ p که بلافاصله بعد از div قرار گرفته اند و والدشان یکی هست.
- Subsequent-sibling combinator (~): ( div ~ p) :
  تمام تگ های p که بعد از div قرار گرفته اند و والدشان یکی هست.


### Pseudo-class selectors :
- syntax :
```
selector:pseudo-class {
  property: value;
}
```
مثال :
```
a:link {
}

a:visited {
}

/* mouse over link */
div:hover {
}

/* Hover over me to show the <p> element. */
div:hover p {
  display: block;
}

```
### Pseudo-elements selectors :
- syntax :
```
selector::pseudo-element {
  property: value;
}
  ```
- pseudo-element are :
  - first-line , first-letter,
  - before , after, marker,selection
```
p::first-line {
  color: #ff0000;
  font-variant: small-caps;
}
h1::before {
  content: url(smiley.gif);
}

::selection {
  color: red;
  background: yellow;
}
```

### Attribute selectors :
- selector is used to select elements with a specified attribute.
  ```
  a[target] {
  background-color: yellow;
  }
  a[target="_blank"] {
  background-color: yellow; }

  ```

  ## how styling :
  - External : have another css file and link in out html file
  - Internal : style in tag <style> in html file
  - Inline style

 ## Important properites :
 ### background
-  background-color
- background-image: use url ("mypic.gif")
- background-repeat : repeat an image vretically or horzentally (repeat-x , repeat-y)
- background-attachment: scroll|fixed|local|initial|inherit
- background-position:
  left top
left center
left bottom
right top
right center
right bottom
center top
center center
center bottom

x% y%
xpos ypos : 50px, 150px
  ```

  body {
  background-image: url("img_tree.png");
  background-repeat: no-repeat;
  background-position: right top;
  background-attachment: scroll;
}
```
- backgroun-size : Specify the size of a background-image with "auto" and in pixels
  - auto|length|cover|contain|initial|inherit
- background (shorthand property)
  ```
  div {
  background: rgba (0,128,0 , 0.3) ; /*  Green background with 30% opacity */
  }
  ```
 ### box model
 - contain
 - padding
 - border
 - outline
 - margin
  ### border :
  - border-style : solid, dotted,dashed,none,hidden,
  - border-width
  - border-color
  - border sides : define different style for each side
    - border : (border-width, border-style, border-color
  - border-radius
  ```
  /* define different style for each side */
    p {
  border-top-style: dotted;
  border-right-style: solid;
  border-bottom-style: dotted;
  border-left-style: solid;}
  
    div {
  border : 5px dotted blue ;
   border-radius: 5px;
    }
  ``` 
 ### margin , padding
 - atributs : (top-right-bottom-left)
 - margin collapse :
   when the top margin of one element and the bottom margin of another overlap , The larger margin value is used
   - values :
     -- auto - the browser calculates the margin
     
     -- length - specifies a margin in px, pt, cm, etc.
     -- % - specifies a margin in % of the width of the containing element
     -- inherit - specifies that the margin should be inherited from the parent element
     ```
     p {
      margin: 25px 50px 75px 100px;
      }
      p {
     margin : 25px, 30px , 70px; /* top  , right and left,bottom
     }
     p {
     margin : 25px, 30px; /* top and bottom , right and left
     }
     ```
  ### postion:
  - static : Static positioned elements are not affected by the top, bottom, left, and right properties
  - relative : is positioned relative to its normal position (top , right,left,bottom ) properties
  - fixed:it always stays in the same place even if the page is scrolled. The top, right, bottom, and left properties are used to position the element
  - absolute:
   توی اولین والدی که دارای postition:relative هست توسط صفت های top-left-bottom-right مکانش تعیین می شود.
  - sticky :
    بین relative, fixed قرار می گیرد .. و مثلا می تونیم تعیین کنیم که وقتی به top رسید مکانش fixed می شود.
    It is positioned relative until a given offset position is met in the viewport - then it "sticks" in place (like position:fixed).
    ```
    div.sticky {
    position: sticky;
    top: 0;
    background-color: green;
    border: 2px solid #4CAF50;
    }
    ```
  ### display
  
  - inline : span,a , are inline elemements
  - block : like div,p,h1,h2 are block elements
  - inherit
  - none

### Media query
- @media : use for define different style for diffrent media types.
- media types: all | print | screen
- media features: orientation | max-(width or height) | width | height

  ```
  @media not|only mediatype and (media feature) and (media feature) {
  CSS-Code;
  }
  @media screen and (min-width: 480px) {
  body {
    background-color: lightgreen;
  }
  }
  ```
## CSS variables
### definition
- can be defined globally or locally
- global variables defined in root of html:
  ```
  :root {
  --blue: #1e90ff;
  --white: #ffffff;
  }
  ```
  - can access to varable using var() function:
    ```
    body {
    background-color : var(--blue);
    }
    ```
 - local variables : can be used only inside the selector where it is declared,
   if we have local varaiable just like the root variable, it will override it`s gloabal value;
   ```
   button {
    --blue: #0000ff; /* local variable will override global */
    background-color: var(--white);
    color: var(--blue);
   
   }
   ```
   - CSS variables have access to the DOM, which means that you can change them with JavaScript. using  document.querySelector(':root')
     

## CSS units
Many CSS properties take "length" values, such as width, margin, padding, font-size  , 
For some CSS properties, negative lengths are allowed
### Absolue
- px
- pt
- mm
- cm
- in  (inch)
### Relative
- rem : Relative to font-size of the root element. if html font-size is 16 px , 1 rem means 16px.
- em : 	Relative to the font-size of the element or near parent (2em means 2 times the size of the current font)
- vh : Relative to 1% of the height of the viewport(browser window size)
- vw : Relative to 1% of the width of the viewport(browser window size)
- % :Relative to the parent element
### CSS functions
- calc : like width: (calc(100% - 100px) )
- var
- max or min :   width: max(50%, 300px);
- acos , asin : Returns the inverse cosine or sin of a number between -1 and 1

## type of design in css,html
- table
- flex


![Screenshot 2025-05-06 131548](https://github.com/user-attachments/assets/2863c305-4606-431b-9d6f-a536b82b5f79)

![Screenshot 2025-05-06 131559](https://github.com/user-attachments/assets/e63f9af0-b508-4e25-904e-b014e0ee8729)
-grid
![Screenshot 2025-05-06 132802](https://github.com/user-attachments/assets/e57a922b-8e00-469f-8ce8-6915ac7aa50e)

## SCSS,SASS, less
  
  

