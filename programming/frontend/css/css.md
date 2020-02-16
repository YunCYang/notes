# CSS

## CSS Notes

### Overflow: Hidden
Apply `overflow: hidden` on `body` tag or `html` tag works on browsers, but not on mobile. This is because mobile has a div acting as a content wrapper for the HTML, thus `overflow` attributes are ignored on the `html` and `body` tag on mobile.

The solution is to create a site wrapper div inside the `body` tag and apply `overflow: hidden ` to the wrapper. May also need to add `position: relative`. For React using the `#root` div works well.


[Back](../../../README.md)
