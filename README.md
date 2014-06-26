# The 'brand-color' meta extension

## Overview 

The 'brand-color' meta extension defines a suggested color that 
browsers and OSes displaying this page SHOULD use if they customize 
the display of individual pages in their UIs with varying colors. 

For example, a browser might color a web app's title bar with the 
specified 'brand-color' value, or use it as a color highlight in a 
task switcher. 

This feature has been developed in the past under multiple proprietary 
names, such as "mapplication-navbutton-color" for Internet Explorer 
and "apple-mobile-web-app-status-bar-style" for Mobile Safari. 

Authors MUST NOT use the proprietary variants of this meta extension. 
User agents that support proprietary variants of this meta extension 
must, if "brand-color" is specified, use "brand-color" for these 
purposes, and ignore any proprietary variants. 

## Syntax 

Example:

```HTML
 <meta name="brand-color" content="#0000ff"> 
```

The content attribute for the "brand-color" meta extension can take 
any valid CSS color. 

## Finding the brand color

To <dfn>find a page's brand color</dfn>: 

1. Let <var>candidate elements</var> be a list of all the 
"brand-color" meta elements on the page, in document order. 
1. For each <var>element</var> in <var>candidate elements</var>: 
  1. Parse a component value from <var>element</var>'s content attribute value. [[css-syntax]] 
  1. Attempt to parse the result as a CSS color. If it succeeds, return the parsed color. 


> Note: This implies that the first successfully parsed "brand-color" 
meta element defines the page's "brand color". Any further 
"brand-color" meta elements have no effect. 

If "brand-color" meta elements are added or removed from the page, or 
have their content attribute changed, user agents MUST find the page's 
brand color again. 

When using the page's "brand color", user agents MAY adjust the color 
in UA-defined ways to make it more suitable for particular uses. For 
example, if a UA intends to use the "brand color" as a background and 
display white text over it, it may use a darker variant of the "brand 
color" for that purpose, to ensure adequate contrast. 

