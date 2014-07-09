# The 'theme-color' meta extension

## Overview 

The 'theme-color' meta extension defines a suggested color that 
browsers and OSes displaying this page SHOULD use if they customize 
the display of individual pages in their UIs with varying colors. 

For example, a browser might color a web app's title bar with the 
specified 'theme-color' value, or use it as a color highlight in a 
task switcher. 

This feature has been developed in the past under multiple proprietary 
names, such as "msapplication-navbutton-color" for Internet Explorer 
and "apple-mobile-web-app-status-bar-style" for Mobile Safari. 

Authors MUST NOT use the proprietary variants of this meta extension. 
User agents that support proprietary variants of this meta extension 
must, if "theme-color" is specified, use "theme-color" for these 
purposes, and ignore any proprietary variants. 

## Syntax 

Example:

```HTML
 <meta name="theme-color" content="#0000ff"> 
```

The content attribute for the "theme-color" meta extension can take 
any valid CSS color. 

## Finding the theme color

To <dfn>find a page's theme color</dfn>: 

1. Let <var>candidate elements</var> be a list of all the 
"theme-color" meta elements on the page, in document order. 
1. For each <var>element</var> in <var>candidate elements</var>: 
  1. Parse a component value from <var>element</var>'s content attribute value. [[css-syntax]] 
  1. Attempt to parse the result as a CSS color:
     1. If it succeeds, return the parsed color.
     1. Otherwise, the page has no theme color and abort these steps.

> Note: This implies that the first "theme-color" meta element defines
  the page's "theme color". Any further "theme-color" meta elements
  have no effect. 

If "theme-color" meta elements are added or removed from the page, or 
have their content attribute changed, user agents MUST find the page's 
theme color again. 

When using the page's "theme color", user agents MAY adjust the color 
in UA-defined ways to make it more suitable for particular uses. For 
example, if a UA intends to use the "theme color" as a background and 
display white text over it, it may use a darker variant of the "theme 
color" for that purpose, to ensure adequate contrast. 

