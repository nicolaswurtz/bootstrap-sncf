---
layout: docs
title: Buttons
description: Use Bootstrap's custom button styles for actions in forms, dialogs, and more with support for multiple sizes, states, and more.
group: components
redirect_from: "/docs/4.0/components/"
toc: true
---

## Examples

Bootstrap includes several predefined button styles, each serving its own semantic purpose, with a few extras thrown in for more control.

{% example html %}
{% for color in site.data.btn-colors %}
<button type="button" class="btn btn-{{ color.name }}">{{ color.name | capitalize }}</button>{% endfor %}
{% endexample %}

{% capture callout-include %}{% include callout-warning-color-assistive-technologies.md %}{% endcapture %}
{{ callout-include | markdownify }}

## Button tags

The `.btn` classes are designed to be used with the `<button>` element. However, you can also use these classes on `<a>` or `<input>` elements (though some browsers may apply a slightly different rendering).

When using button classes on `<a>` elements that are used to trigger in-page functionality (like collapsing content), rather than linking to new pages or sections within the current page, these links should be given a `role="button"` to appropriately convey their purpose to assistive technologies such as screen readers.

{% example html %}
<a class="btn btn-primary" href="#" role="button">Link</a>
<button class="btn btn-primary" type="submit">Button</button>
<input class="btn btn-primary" type="button" value="Input">
<input class="btn btn-primary" type="submit" value="Submit">
<input class="btn btn-primary" type="reset" value="Reset">
{% endexample %}

## Button link

TODO : description

{% example html %}
<a href="#" class="btn btn-link"><span>Link</span> <i class="icons-share icon-size-x75 ml-2"></i></a>
<a href="#" class="btn btn-link disabled"><span>Disabled link</span> <i class="icons-share icon-size-x75 ml-2"></i></a>
{% endexample %}

## Button icon

TODO : description

{% example html %}
<button type="button" class="btn btn-only-icon btn-primary"><i class="icons-search"></i></button>
<button type="button" class="btn btn-only-icon btn-white" disabled><i class="icons-search"></i></button>
<button type="button" class="btn btn-only-icon btn-white"><i class="icons-search"></i></button>
{% endexample %}

TODO : description

{% example html %}
<button type="button" class="btn-rounded btn-rounded-white box-shadow"><i class="icons-arrow-prev"></i></button>
<button type="button" class="btn-rounded btn-rounded-white box-shadow"><i class="icons-arrow-next"></i></button>
<button type="button" class="btn-rounded btn-rounded-primary"><i class="icons-share"></i></button>
<button type="button" class="btn-rounded btn-rounded-facebook"><i class="icons-close"></i></button>
<button type="button" class="btn-rounded btn-rounded-twitter"><i class="icons-close"></i></button>
<button type="button" class="btn-rounded btn-rounded-linkedin"><i class="icons-close"></i></button>
<button type="button" class="btn-rounded btn-rounded-youtube"><i class="icons-close"></i></button>
{% endexample %}

## Sizes

Fancy smaller buttons? Add `.btn-sm` for additional sizes.

{% example html %}
<button type="button" class="btn btn-primary btn-sm">Small button</button>
<button type="button" class="btn btn-secondary btn-sm">Small button</button>
{% endexample %}

Create block level buttons—those that span the full width of a parent—by adding `.btn-block`.

{% example html %}
<button type="button" class="btn btn-primary btn-block">Block level button</button>
<button type="button" class="btn btn-secondary btn-block">Block level button</button>
{% endexample %}

## Active state

Buttons will appear pressed (with a darker background, darker border, and inset shadow) when active. **There's no need to add a class to `<button>`s as they use a pseudo-class**. However, you can still force the same active appearance with `.active` (and include the <code>aria-pressed="true"</code> attribute) should you need to replicate the state programmatically.

{% example html %}
<a href="#" class="btn btn-primary active" role="button" aria-pressed="true">Primary link</a>
<a href="#" class="btn btn-secondary active" role="button" aria-pressed="true">Link</a>
{% endexample %}

## Disabled state

Make buttons look inactive by adding the `disabled` boolean attribute to any `<button>` element.

{% example html %}
<button type="button" class="btn btn-primary" disabled>Primary button</button>
<button type="button" class="btn btn-secondary" disabled>Button</button>
{% endexample %}

Disabled buttons using the `<a>` element behave a bit different:

- `<a>`s don't support the `disabled` attribute, so you must add the `.disabled` class to make it visually appear disabled.
- Some future-friendly styles are included to disable all `pointer-events` on anchor buttons. In browsers which support that property, you won't see the disabled cursor at all.
- Disabled buttons should include the `aria-disabled="true"` attribute to indicate the state of the element to assistive technologies.

{% example html %}
<a href="#" class="btn btn-primary disabled" role="button" aria-disabled="true">Primary link</a>
<a href="#" class="btn btn-secondary disabled" role="button" aria-disabled="true">Link</a>
{% endexample %}

{% callout warning %}
##### Link functionality caveat

The `.disabled` class uses `pointer-events: none` to try to disable the link functionality of `<a>`s, but that CSS property is not yet standardized. In addition, even in browsers that do support `pointer-events: none`, keyboard navigation remains unaffected, meaning that sighted keyboard users and users of assistive technologies will still be able to activate these links. So to be safe, add a `tabindex="-1"` attribute on these links (to prevent them from receiving keyboard focus) and use custom JavaScript to disable their functionality.
{% endcallout %}

## Button illustration

{% example html %}
<button type="button" class="btn btn-card" data-toggle="button">
  <i class="icons-earth-underline icon-size-4x50"></i>
  <span>Défaut</span>
</button>
<button type="button" class="btn btn-card active" data-toggle="button">
  <i class="icons-earth-underline icon-size-4x50"></i>
  <span>Sélectionné</span>
</button>
<button type="button" class="btn btn-card" data-toggle="button" disabled>
  <i class="icons-earth-underline icon-size-4x50"></i>
  <span>Inactif</span>
</button>
{% endexample %}

## Button plugin

Do more with buttons. Control button states or create groups of buttons for more components like toolbars.

### Toggle states

Add `data-toggle="button"` to toggle a button's `active` state. If you're pre-toggling a button, you must manually add the `.active` class **and** `aria-pressed="true"` to the `<button>`.

{% example html %}
<button type="button" class="btn btn-primary" data-toggle="button" aria-pressed="false" autocomplete="off">
  Single toggle
</button>
{% endexample %}

### Checkbox and radio buttons

Bootstrap's `.button` styles can be applied to other elements, such as `<label>`s, to provide checkbox or radio style button toggling. Add `data-toggle="buttons"` to a `.btn-group` containing those modified buttons to enable their toggling behavior via JavaScript and add `.btn-group-toggle` to style the `<input>`s within your buttons. **Note that you can create single input-powered buttons or groups of them.**

The checked state for these buttons is **only updated via `click` event** on the button. If you use another method to update the input—e.g., with `<input type="reset">` or by manually applying the input's `checked` property—you'll need to toggle `.active` on the `<label>` manually.

Note that pre-checked buttons require you to manually add the `.active` class to the input's `<label>`.

{% example html %}
<div class="btn-group-toggle" data-toggle="buttons">
  <label class="btn btn-secondary active">
    <input type="checkbox" checked autocomplete="off"> Checked
  </label>
</div>
{% endexample %}

{% example html %}
<div class="btn-group btn-group-toggle" data-toggle="buttons">
  <label class="btn btn-secondary active">
    <input type="radio" name="options" id="option1" autocomplete="off" checked> Active
  </label>
  <label class="btn btn-secondary">
    <input type="radio" name="options" id="option2" autocomplete="off"> Radio
  </label>
  <label class="btn btn-secondary">
    <input type="radio" name="options" id="option3" autocomplete="off"> Radio
  </label>
</div>
{% endexample %}

### Methods

| Method | Description |
| --- | --- |
| `$().button('toggle')` | Toggles push state. Gives the button the appearance that it has been activated. |
| `$().button('dispose')` | Destroys an element's button. |