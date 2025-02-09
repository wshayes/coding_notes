# HTMX Notes

## Example Code

- https://enzircle.hashnode.dev/bulk-actions-in-table-with-django-htmx-and-alpinejs
- 
### 1. Triggering

First let's take a look at a really simple example:

```html
      <button hx-get="/data" hx-trigger="click" hx-swap="outerHTML">
        Click Me
      </button>
```

The only attribute I'm going to talk about here is the `hx-trigger`. As you can see its set to trigger on a click of the button element. That said, the attribute did not need to be stated. The default event is "click" except for input elements which are set to "change" and forms that are set to "submit".

#### Example: Polling with HTMX

```html
  <div hx-get="/data" hx-trigger="every 1s" hx-swap="outerHTML">
    updated every 1 second
  </div>
```

#### Example: Triggering from Another Element

```html
  <div id="my-div" hx-get="/data" hx-trigger="click from:#button1" hx-swap="outerHTML">
    Initial content of the div.
  </div>
  <button id="button1">Click me to update div</button>
```

### Race Conditions Examples

Form validation example:
```html
<form hx-post="/store">
    <input id="title" name="title" type="text"
        hx-post="/validate"
        hx-trigger="change"
        hx-sync="closest form:drop">
    <button type="submit">Submit</button>
</form>
```

Alternative validation approach:
```html
<form hx-post="/store">
    <input id="title" name="title" type="text"
        hx-post="/validate"
        hx-trigger="change"
        hx-sync="closest form:abort">
    <button type="submit">Submit</button>
</form>
```

Search with sync replace:
```html
<input type="search" 
    hx-get="/search" 
    hx-trigger="keyup changed delay:500ms, search" 
    hx-target="#search-results"
    hx-sync="this:replace">
```

### Loading Indicators

```html
<button hx-get="/click">
    Click Me!
    <img class="htmx-indicator" src="/spinner.gif">
</button>
```

### Request Examples

Password validation with multiple fields:

```html 
<input type="text" id="password1" name="password1">
<input type="text" id="password2" name="password2" 
    hx-post="/validate/password" 
    hx-include="[name='password1']">
```

Using hx-vals for additional data:

```html
<input type="text" id="password1" name="password1">
<input type="text" id="password2" name="password2" 
    hx-post="/validate/password" 
    hx-vals="js:{csrftoken: 'dfdfdsdsf'}">
```

### Response Examples

Search with target:
```html
<input type="search" 
    hx-get="/search" 
    hx-trigger="keyup changed delay:500ms, search" 
    hx-target="#search-results">
<div id="search-results"></div>
```

Out-of-bounds swap example response:

```html     
<div id="message" hx-swap-oob="true">Swap me directly!</div>
<div hx-swap-oob="beforeend:#messages">add me!</div>
```

## Additional Features

HTMX can do much more, including:
- Triggering JavaScript functions using hx-on
- WebSocket and SSE support
- User prompts and confirmations
- Error handling
- And much more, mostly without writing any JavaScript

The power of HTMX lies in its simplicity and its ability to leverage your backend templating engine for rendering, making frontend development much more straightforward, especially when working with frameworks like Django.
