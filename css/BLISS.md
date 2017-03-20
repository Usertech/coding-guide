# CSS Bliss

A CSS style guide for small to enormous projects, without all that pomp and cruft. Many ideas borrowed from BEM, SMACSS, OOCSS, SUITECSS. This style guide uses SCSS. However, the only truly beneficial preprocessor-specific features we discuss are variables, mixins, and partials. Therefore, this guide will be useful for any preprocessor or no preprocessor at all as there is very little focus on features that aren't already part of vanilla CSS.

**We use BLISS on all projects.**

## Bliss rules
https://github.com/gilbox/css-bliss

## Bliss walkthrough
http://gilbox.github.io/css-bliss/walkthrough/release/

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
- **.camelCase**

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

## Mistakes
- don't use `!important`
- don't scross Modules




