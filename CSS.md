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
### Pseudo-elements selectors :
### Attribute selectors :
