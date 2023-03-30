# HVBox

**22 lines of CSS == awesome rapid prototyping**

hvbox.css makes it easy to use flexbox directly in HTML.

**tl;dr example**

An input like:

```html
<div id=app hbox=stretch>
  <div id=sidebar flex=0>...</div>
  <div id=content vbox=stretch>
    <div id=toolbar flex=0>...</div>
    <div id=editor>...</div>
    <div id=status flex=0>...</div>
  </div>
</div>
```

…produces an output like:

```
┌───────┬────────────────────────────┐
│       │                            │
│       ├────────────────────────────┤
│       │                            │
│       │                            │
│       │                            │
│       │                            │
│       │                            │
│       │                            │
│       │                            │
│       ├────────────────────────────┤
│       │                            │
└───────┴────────────────────────────┘

```


## More Details

### Containers

Simply give an element an `hbox` attribute for horizontal, or `vbox` for vertical.

The presence of the attribute is enough to trigger flexbox on the element and its children.
You can control `justify-content` and `align-items` by giving the attribute a value, which is
either one or two words, separated by a hyphen. *(and since unquoted hyphens are valid in HTML, you don't even have to put the value in quotes 🥳)*

If there is only one word, the property applies to both `justify-content` and `align-items`. If two words, the first goes to `justify-content` and the last to `align-items`.

The properties are:

- `start` → `start`
- `end` → `end`
- `center` → `center`
- `stretch` → `stretch`
- `around` → `space-around`
- `evenly` → `space-evenly`
- `between` → `space-between`
- `baseline` → `baseline` *(only applies to `align-items`)*


### Children

To control children behavior, include a `flex` attribute on the child, with a value between 0-5. This simply sets the `flex` CSS property on the child. For instance, `<div flex=0></div>` applies `flex: 0` to the div.


## Summary

With these few things, you can create very complex layouts with very little typing. Great for prototyping.

Simply copy-paste the contents of `hbox.css` into the top of your css file. Since it's such a small amount of code, here it is for convenience:

```css
[vbox], [hbox] {display: flex;}
[vbox] {flex-direction: column;}
[hbox] {flex-direction: row;}
[vbox^="start"    i], [hbox^="start"    i] { justify-content: start; }
[vbox^="end"      i], [hbox^="end"      i] { justify-content: end; }
[vbox^="center"   i], [hbox^="center"   i] { justify-content: center; }
[vbox^="around"   i], [hbox^="around"   i] { justify-content: space-around; }
[vbox^="even"     i], [hbox^="even"     i] { justify-content: space-evenly; }
[vbox^="between"  i], [hbox^="between"  i] { justify-content: space-between; }
[vbox^="stretch"  i], [hbox^="stretch"  i] { justify-content: stretch; }
[vbox$="start"    i], [hbox$="start"    i] { align-items: start; }
[vbox$="end"      i], [hbox$="end"      i] { align-items: end; }
[vbox$="center"   i], [hbox$="center"   i] { align-items: center; }
[vbox$="around"   i], [hbox$="around"   i] { align-items: space-around; }
[vbox$="even"     i], [hbox$="even"     i] { align-items: space-evenly; }
[vbox$="between"  i], [hbox$="between"  i] { align-items: space-between; }
[vbox$="stretch"  i], [hbox$="stretch"  i] { align-items: stretch; }
[vbox$="baseline" i], [hbox$="baseline" i] { align-items: baseline; }
[vbox] > *, [hbox] > * { flex: initial; }
[vbox^="stretch"] > *, [hbox^="stretch"] > * { flex: auto; }
[flex="0"]{flex:0;} [flex="1"]{flex:1;} [flex="2"]{flex:2;}
[flex="3"]{flex:3;} [flex="2"]{flex:4;} [flex="5"]{flex:5;}
```

You may also be interested in the additional contents of `hbox-reset.css` which adds a few things that make layout easier. Again for convenience:

```css
*, *:before, *:after {margin:0; padding:0; box-sizing:border-box; position:relative;}
html, body {width:100%; height:100%;}
```

I've been using these in all my recent prototypes and quick-and-dirty utilities.

Enjoy! 🥂
