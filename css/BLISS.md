# CSS Bliss

A CSS style guide for small to enormous projects, without all that pomp and cruft.

**We use BLISS on all projects.**

## To be studied in following order

- [Walkthrough](http://gilbox.github.io/css-bliss/walkthrough/release/)
- [Chapters in README](https://github.com/gilbox/css-bliss)
- [How css-bliss tackles problems with complex CSS identified by Facebook](https://github.com/gilbox/css-bliss/blob/master/solving-complexity.md)
- [Common mistakes](https://github.com/gilbox/css-bliss/blob/master/common-mistakes.md)

## Naming

### Modul
- **.TitleCase**

### Module Modifier
- **--camelCase**

### Element
- ***-camelCase**

### Element Modifier
- **--camelCase**

### State
- **.isCamelCase (formerly .is-camelCase)**

### Utility Classes (aka Simple Rules)
- **.u-camelCase**

### Modul example

`example.scss`
```scss
.MyModule {
  ...
  &-myElement {
    ...
  }

  &-myOtherElement {
    ...
  }

  &-myOtherElement--myModifier {
    ...
  }

  &-myOtherElement--anotherModifier {
    ...
  }
}

.MyModule--myModifier {
    ...
    .MyModule-myOtherElement {
        ...
    }

    .MyModule-myOtherElement--anotherModifier {
        ...
    }
}

.MyModule--anotherModifier {
    ...
}

@media (max-width: $screen-xs-max) {
    .MyModule {
        ...
        &-myElement {
            ...
        }
        ...
    }
}
```

`example.html`
```html
<div class="MyModule">
    <div class="MyModule-item">
        <h2 class="Headline Headline--medium">
            Title 1
        </h2>
        <a class="Link" href="/odkaz-1">
            Link 1
        </a>
    </div>
    <div class="MyModule-item">
        <h2 class="Headline Headline--medium">
            Title 2
        </h2>
        <a class="Lin" href="/odkaz-2">
            Link 2
        </a>
    </div>
</div>
```




