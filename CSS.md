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
- background-image
- background-repeat
- background-attachment
- background-position
- background (shorthand property)
