# Tags for Bootstrap 4/5

[![NPM](https://nodei.co/npm/bootstrap5-tags.png?mini=true)](https://nodei.co/npm/bootstrap5-tags/)
[![Downloads](https://img.shields.io/npm/dt/bootstrap5-tags.svg)](https://www.npmjs.com/package/bootstrap5-tags)

## How to use

An ES6 native replacement for `select` using standards Bootstrap 5 (and 4) styles.

No additional CSS needed! Supports creation of new tags.

```js
import Tags from "./tags.js";
Tags.init();
// Tags.init(selector, opts);
// You can pass global settings in opts that will apply
// to all Tags instances
```

By default, only provided options are available. Validation error
will be displayed in case of invalid tag.

```html
<label for="tags-input" class="form-label">Tags</label>
<select class="form-select" id="tags-input" name="tags[]" multiple>
  <option disabled hidden value="">Choose a tag...</option>
  <option value="1" selected="selected">Apple</option>
  <option value="2">Banana</option>
  <option value="3">Orange</option>
</select>
<div class="invalid-feedback">Please select a valid tag.</div>
```

Use attribute `data-allow-new` to allow creation of new tags. Their
default value will be equal to the text. Since you can enter
arbitrary text, no validation will occur.

```html
<select class="form-select" id="tags-input" name="tags[]" multiple data-allow-new="true"></select>
```

Use attribute `data-show-all-suggestions` in order to show an unfiltered list of options.
Only the first matching value is selected.

```html
<select class="form-select" id="tags-input" name="tags[]" multiple data-show-all-suggestions="true"></select>
```

Use attribute `data-allow-clear` in order to add a cross to remove items.

```html
<select class="form-select" id="tags-input" name="tags[]" multiple data-allow-clear="true"></select>
```

Use attribute `data-suggestions-threshold` to determine how many characters need to be typed to show the dropdown (defaults to 1).

```html
<select class="form-select" id="tags-input" name="tags[]" multiple data-suggestions-threshold="0"></select>
```

Use attribute `data-regex` to force new tags to match a given regex.

```html
<select class="form-select" id="tags-input" name="tags[]" multiple data-regex=".*@mycompany\.com$"></select>
```

Use attribute `data-separator` to split new tags based on a given separator. You can add multiple separators with |.

```html
<select class="form-select" id="tags-input" name="tags[]" multiple data-separator=" |,">
    <option disabled hidden value="">Type a tag...</option>
</select>
```

Use attribute `data-max` to only allow a specific number of tags

```html
<select class="form-select" id="tags-input" name="tags[]" multiple data-max="2" data-allow-clear="true">
    <option disabled hidden value="">Type a tag...</option>
</select>
```

_NOTE: don't forget the [] if you need multiple values!_

## Server side support

You can also use options provided by the server. This script expects a json response that is an array or an object with the data key containing an array.

Simply set `data-server` where your endpoint is located. It should provide an array of value/label objects. The suggestions will be populated upon init
except if `data-live-server` is set, in which case, it will be populated on type. A ?query= parameter is passed along with the current value of the searchInput.

```html
<label for="validationTagsJson" class="form-label">Tags (server side)</label>
<select class="form-select" id="validationTagsJson" name="tags_json[]" multiple data-allow-new="true" data-server="demo.json" data-live-server="1">
  <option disabled hidden value="">Choose a tag...</option>
</select>
```

## Accessibility

You can set accessibility labels when passing options:

- clearLabel ("Clear" by default)
- searchLabel ("Type a value" by default)

## Tips

- Use arrow down to show dropdown (and arrow up to hide it)
- If you have a really long list of options, a scrollbar will be used
- Access Tags instance on a given element with Tags.getInstance(mySelect)

## Bootstrap 4 support

Even if it was not the initial idea to support Bootstrap 4, this component is now compatible with Bootstrap 4 because it only
requires minimal changes.

Check out demo-bs4.html

## Standalone usage

Obviously, this package works great with the full bootstrap library, but you can also use it without Bootstrap or with a trimmed down version of it

In my version, I'm using bootstrap.native to keep the bundle size under a reasonable size (15,2kb vs 9,5kb for the original version).

You can check out the .scss file to see how to reduce bootstrap 5 css to a smaller size.

Check out demo-standalone.html

## Demo

https://codepen.io/lekoalabe/pen/ExWYEqx

## How does it look ?

![screenshot](screenshot.png "screenshot")

## Browser supports

Modern browsers (edge, chrome, firefox, safari... not IE11). [Add a warning if necessary](https://github.com/lekoala/nomodule-browser-warning.js/).

## I need more

Maybe you can have a look at https://github.com/Honatas/multi-select-webcomponent
