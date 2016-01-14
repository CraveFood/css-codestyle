# CSS Code Style Guide

_This is the Code Style guide for CSS, feel free to bring new ideas. Forked from [ThinkUpLLC](https://github.com/ThinkUpLLC/ThinkUp/wiki/Code-Style-Guide:-CSS)._

### Indentation

Use an indent of two spaces, with no tabs.

### Names & Capitalization

ID names should be in lowerCamelCase.

<pre>#pageContainer {</pre>

Class names should be in lowercase, with words separated by dashes.

<pre>.my-class-name {</pre>

HTML elements should be in lowercase.

<pre>body, div {</pre>

### Selectors

Selectors should be on a single line, with a space after the last selector, followed by an opening brace. A selector block should end with a closing curly brace that is unindented and on a separate line. A blank line should be placed between each selector block. Selectors should never be indented.

<pre>selector {
}

selector {
}</pre>

Multiple selectors should each be on a single line, with no space after each comma.

<pre>selector1,
selector2,
selector3,
selector4 {
}</pre>

When selecting HTML elements, write the selector in lowercase.

<pre>div { /* Okay */
DIV { /* Not okay */</pre>

### Nesting
Avoid more than two levels of nesting, instead, try to break it into small classes.

<pre>
/* Okay */
.selector {
    .selector2 {
    }
}

/* Okay */
.selector .selector2 {
}

/* Not okay */
.selector {
    .selector2 {
        .selector3 {
        
        }
    }
}

/* Not okay */
.selector .selector2 .selector3 {

}

</pre>

### Property-Value Pairs

Property-value pairs should be listed starting on the line after the opening curly brace. Each pair should:
* be on its own line;
* be indented one level;
* have a single space after the colon that separates the property name from the property value; and
* end in a semicolon.

<pre>selector {
  name: value;
  name: value;
}</pre>

Start with the box model properties followed by its positions and finally the context properties grouped.

<pre>
/* Not okay */
.selector {
  font-weight: normal;
  width: 500px;
  background: #000;
}

/* Okay */
.selector {
  width: 500px;
  height: 500px;
  padding: 20px 30px;
  margin: 30px 20px;
  
  position: absolute;
  top: 20px;
  left: 20px;
  
  border: 1px solid red;
  
  font-family: Helvetica, sans-serif;
  font-size: 12px;
  color: red;
  
  text-decoration: underline;
  text-style: italic;
}
</pre>

For properties with multiple values, separate each value with a single space following the comma(s).

<pre>  font-family: Helvetica, sans-serif;</pre>

If a single value contains any spaces, that value must be enclosed within double quotation marks.

<pre>  font-family: "Lucida Grande", Helvetica, sans-serif;</pre>

### Position

Following the Atomic design principles, modify the selector position on his parent instead on its own.
 
<pre>
/* Okay */
.selector {
  width: 500px;
  height: 500px;
  padding: 20px 30px;
}    

/* Better */
//parent.less
.parent {
    .selector {
        margin: 30px 20px;
    }
}

//selector.less
.selector {
  width: 500px;
  height: 500px;
  padding: 20px 30px;
}    
</pre>

### Pre-compile
Split your code into small files, this make code easy to read and maintain.
<pre>
/* Okay */
//parent.less
.parent {
    .selector {
        margin: 30px 20px;
    }
}

/* Better */
//parent.less
.parent {
    ...
}

//selector.less
.selector {
  ...
}    
</pre>

### Colors

When denoting color using hexadecimal notation, use all capital letters. Both three-digit and six-digit hexadecimal notation are acceptable; if it's possible to specify the desired color using three-digit hexadecimal notation, do so as you'll save the end-user a few bytes of download time.

<pre>
  color: #FFF;    /* Okay */
  color: #FE9848; /* Okay */
  color: #fff;    /* Not okay */
</pre>

### Dimensions

When denoting the dimensions -- that is, the width or height -- of an element or its margins, borders, or padding, specify the units in either <code>em</code>, <code>px</code>, or <code>%</code>. If the value of the width or height is 0, do not specify units.

<pre>
  width: 12px;  /* Okay */
  width: 12%;   /* Okay */
  width: 12em;  /* Okay */
  width: 12rem; /* Okay */
  width: 0;     /* Okay */
  width: 12;    /* Not okay */
  width: 0px;   /* Not okay */
</pre>