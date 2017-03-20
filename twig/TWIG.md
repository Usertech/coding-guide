# Twig

Twig is a modern template engine for PHP.

**We use it on most projects** (specially with SEED).

## Doc
- [Go to Twig Doc](http://twig.sensiolabs.org/doc/2.x/)

## Best Practice 
- [Global Variables](#global-variables)
- [Dump variable](#dump-variable)
- [The ternary operator](#the-ternary-operator)
- [String Interpolation](#string-interpolation)
- [Control Structure](#control-structure)
- [Use the loop variable](#use-the-loop-variable)
- [Use EMBED](#use-embed)
- [Use Import and Macros](#use-import-and-macros)
- [Add new extensions](#add-new-extensions)

### Global Variables

* **_self**: references the current template name;
* **_context**: references the current context;
* **_charset**: references the current charset.

###  Dump variable
```php
{{ dump(_context) }}
```

### The ternary operator
```php
{{ foo ? 'yes' : 'no' }}
{{ foo ?: 'no' }} is the same as {{ foo ? foo : 'no' }}
{{ foo ? 'yes' }} is the same as {{ foo ? 'yes' : '' }}

{# returns the value of foo if it is defined and not null, 'no' otherwise #}
{{ foo ?? 'no' }}
```

### String Interpolation
```php
{{ "foo #{bar} baz" }}
{{ "foo #{1 + 2} baz" }}
```

### Control Structure
```php
{% if users|length > 0 %}
    <ul>
        {% for user in users %}
            <li>{{ user.username|e }}</li>
        {% endfor %}
    </ul>
{% endif %}

{# or #}

<ul>
    {% for user in users %}
        <li>{{ user.username|e }}</li>
    {% else %}
        <li>no user found</li>
    {% endfor %}
</ul>
```

```php
{% if title %}
    <h1>{{ title }</h1>}
{% endif %}
```

### Use the loop variable
| Variable | Description |
| - | - |
| loop.index | The current iteration of the loop. (1 indexed) |
| loop.index0 | The current iteration of the loop. (0 indexed) |
| loop.revindex | The number of iterations from the end of the loop (1 indexed) |
| loop.revindex0 | The number of iterations from the end of the loop (0 indexed) |
| loop.first | True if first iteration |
| loop.last | True if last iteration |
| loop.length | The number of items in the sequence |
| loop.parent | The parent context |


### Use EMBED
The embed tag combines the behaviour of include and extends. It allows you to include another template's contents, just like include does. But it also allows you to override any block defined inside the included template, like when extending a template.

Think of an embedded template as a "micro layout skeleton".

#### Example

Create module: `modal.html.twig`
```php
<div class="Modal" id="{{ "Modal-#{id}" }}">
    <div class="Modal-content">
        <div class="Modal-header">
            {% block header %}
                Modal header default content
            {% endblock %}
        </div>
        <div class="Modal-body">
            {% block body %}
                Modal body default content
            {% endblock %}
        </div>
    </div>
</div>
```

Usage: `template.html.twig`
```php
{% embed "modal.html.twig" with { 'id' : 1} %}
    {% block header %}
        Some content for the modal heade
    {% endblock %}

    {% block body %}
        Some content for the modal body
    {% endblock %}
{% endembed %}
```

[More informations](http://twig.sensiolabs.org/doc/2.x/tags/embed.html)

### Use Import and Macros

`form.html.twig`
```php
{% macro input(name, value, type, size) %}
    <input type="{{ type|default('text') }}" name="{{ name }}" value="{{ value|e }}" size="{{ size|default(20) }}" />
{% endmacro %}

{% macro textarea(name, value, rows, cols) %}
    <textarea name="{{ name }}" rows="{{ rows|default(10) }}" cols="{{ cols|default(40) }}">{{ value|e }}</textarea>
{% endmacro %}
```

Usage: `template.html.twig`
```php
{% import 'forms.html.twig' as forms %}

<dl>
    <dt>Username</dt>
    <dd>{{ forms.input('username') }}</dd>
    <dt>Password</dt>
    <dd>{{ forms.input('password', null, 'password') }}</dd>
</dl>
<p>{{ forms.textarea('comment') }}</p>

{# or #}

{% from 'forms.html' import input as input_field, textarea %}

<dl>
    <dt>Username</dt>
    <dd>{{ input_field('username') }}</dd>
    <dt>Password</dt>
    <dd>{{ input_field('password', '', 'password') }}</dd>
</dl>
<p>{{ textarea('comment') }}</p>
```

More informations [import](http://twig.sensiolabs.org/doc/2.x/tags/import.html) and [macro](http://twig.sensiolabs.org/doc/2.x/tags/macro.html)

### Add new extensions

#### Create
`src/AppBundle/Twig/AppExtension.php`

```php

// CREATE FUNCTION

/**
* @param $string
*
* @return boolean
*/
public function isYoutubeLink($url) {
    if (false !== strpos($url, 'youtube')) {
        return true;
    }
    return false;
}


// RETURN IT IN:
// public function getFilters()

return [
    ...
    new \Twig_SimpleFilter('isYoutubeLink', [$this, 'isYoutubeLink']),
    ...
]
```

#### Usage
```php
{% if youtubeLink | isYoutubeLink %}
    some action
{% endif %}
```

[More informations](http://twig.sensiolabs.org/doc/2.x/advanced.html#creating-an-extension)