# AlpineJS Notes
## Useful AlpineJS links
[Add dynamic form fields using AlpineJS](https://codepen.io/sanjayojha/pen/qBONdVm)

[Dynamic input fields with Alpine.js](https://gist.github.com/awebartisan/3e0fb5eb47e86ce2b144b18064ec625b)

[Drag and Drop using alpine.js](https://codepen.io/trovster/full/oNjGGMq)

[How to check and uncheck all checkboxes by clicking one checkbox using alpine js](https://stackoverflow.com/questions/61470556/how-to-check-and-uncheck-all-checkboxes-by-clicking-one-checkbox-using-alpine-js)

[alpine-sortable](https://codepen.io/ranjan-purbey/pen/xoEMOM)

[Alpine.js Drag and Drop](https://www.trovster.com/blog/2020/05/alpinejs-drag-and-drop)


### Dynamic field snippets (e.g. adding/removing duplicate item type fields to form)

```django

# Push FAQ new entry to end of faqs array
<button @click="faqs.push({question: '', answer: '', index: faqs.length})" type="button"
    class="mt-2 rounded-full p-1.5 text-white shadow-sm focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600"
>
    <svg xmlns="http://www.w3.org/2000/svg" height="16" width="16" viewBox="0 0 512 512">
        <path fill="#00c800" d="M256 512A256 256 0 1 0 256 0a256 256 0 1 0 0 512zM232 344V280H168c-13.3 0-24-10.7-24-24s10.7-24 24-24h64V168c0-13.3 10.7-24 24-24s24 10.7 24 24v64h64c13.3 0 24 10.7 24 24s-10.7 24-24 24H280v64c0 13.3-10.7 24-24 24s-24-10.7-24-24z" />
    </svg>
</button>

# Use splice to insert after current index
<button @click="faqs.splice(faq.index + 1, 0, {question: '', answer: '', index: faq.index + 1})"

# Use following to only show after first entry of the array
<template x-if="faq.index > 0">

# Use following to only show at the end of the array
<template x-if="faq.index == faqs.index - 1">

```