---
title: 'Custom checkbox'
date: '2022-07-28'
tags: ['checkbox', 'snippets', 'css']
draft: false
summary: 'Creates a styled checkbox with animation on state change. '
layout: SnippetSimple
---

![custom-checkbox](/static/images/snippets/checkbox.jpg)

Creates a styled checkbox with animation on state change.

- Use an `<svg>` element to create the check `<symbol>` and insert it via the `<use>` element to create a reusable SVG icon.
- Create a .checkbox-container and use flexbox to create the appropriate layout for the checkboxes.
- Hide the `<input>` element and use the label associated with it to display a checkbox and the provided text.
- Use `stroke-dashoffset` to animate the check symbol on state change.
- Use `transform: scale(0.9)` via a CSS animation to create a zoom animation effect.

```html
<svg class="checkbox-symbol">
  <symbol id="check" viewbox="0 0 12 10">
    <polyline
      points="1.5 6 4.5 9 10.5 1"
      stroke-linecap="round"
      stroke-linejoin="round"
      stroke-width="2"
    ></polyline>
  </symbol>
</svg>

<div class="checkbox-container">
  <input class="checkbox-input" id="samsung" type="checkbox" />
  <label class="checkbox" for="samsung">
    <span>
      <svg width="12px" height="10px">
        <use xlink:href="#check"></use>
      </svg>
    </span>
    <span>Samsung</span>
  </label>
  <input class="checkbox-input" id="apple" type="checkbox" />
  <label class="checkbox" for="apple">
    <span>
      <svg width="12px" height="10px">
        <use xlink:href="#check"></use>
      </svg>
    </span>
    <span>Apple</span>
  </label>
</div>
```

```css
.checkbox-symbol {
  position: absolute;
  width: 0;
  height: 0;
  pointer-events: none;
  user-select: none;
}

.checkbox-container {
  box-sizing: border-box;
  background: #ffffff;
  color: #222;
  height: 64px;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-flow: row wrap;
}

.checkbox-container * {
  box-sizing: border-box;
}

.checkbox-input {
  position: absolute;
  visibility: hidden;
}

.checkbox {
  user-select: none;
  cursor: pointer;
  padding: 6px 8px;
  border-radius: 6px;
  overflow: hidden;
  transition: all 0.3s ease;
  display: flex;
}

.checkbox:not(:last-child) {
  margin-right: 6px;
}

.checkbox:hover {
  background: rgba(0, 119, 255, 0.06);
}

.checkbox span {
  vertical-align: middle;
  transform: translate3d(0, 0, 0);
}

.checkbox span:first-child {
  position: relative;
  flex: 0 0 18px;
  width: 18px;
  height: 18px;
  border-radius: 4px;
  transform: scale(1);
  border: 1px solid #cccfdb;
  transition: all 0.3s ease;
}

.checkbox span:first-child svg {
  position: absolute;
  top: 3px;
  left: 2px;
  fill: none;
  stroke: #fff;
  stroke-dasharray: 16px;
  stroke-dashoffset: 16px;
  transition: all 0.3s ease;
  transform: translate3d(0, 0, 0);
}

.checkbox span:last-child {
  padding-left: 8px;
  line-height: 18px;
}

.checkbox:hover span:first-child {
  border-color: #966f9a;
}

.checkbox-input:checked + .checkbox span:first-child {
  background: #966f9a;
  border-color: #966f9a;
  animation: zoom-in-out 0.3s ease;
}

.checkbox-input:checked + .checkbox span:first-child svg {
  stroke-dashoffset: 0;
}

@keyframes zoom-in-out {
  50% {
    transform: scale(0.9);
  }
}
```

[View Codepen](https://codepen.io/berkaymehmetsert/pen/BarmQzz)

And that's what I know about checkbox. I hope you find it useful. If you have any questions, please let me know. 👇

Happy coding!
