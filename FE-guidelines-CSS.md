# CSS Guidelines

##Contents
 * [TL;DR](#tldr)
 * [Directory structure](#directory-structure)
 * [Name-spacing](#name-spacing)
	 * [Common name-spaces](#common-name-spaces)
 * [BEM](#bem)
 * [Sass](#sass)
	 * [Nesting](#nesting)
	 * [Elements](#elements)
	 * [Sibling and child selectors](#sibling-and-child-selectors)
	 * [Extend](#extend)
* [Normalize](#normalize)
* [Auto-prefixing](#auto-prefixing)
* [Pixel-based units](#pixel-based-units)

##TL;DR

* [Sass](http://sass-lang.com/)
* [BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) ([name-spaced](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/))
* [ITCSS](http://www.creativebloq.com/web-design/manage-large-scale-web-projects-new-css-architecture-itcss-41514731?page=1)
* [Auto-prefixing](https://css-tricks.com/autoprefixer/)
* Pixel based units

##Directory structure

We follow the [ITCSS](http://www.creativebloq.com/web-design/manage-large-scale-web-projects-new-css-architecture-itcss-41514731?page=1) architecture, and keep files named and organised according to content.
```
styles
├─ _settings
│   ├ _settings.colours.scss
│   └ _settings.dimensions.scss
├─ _tools
│   ├ _tools.functions.scss
│   └ _tools.mixins.scss
├─ _generic
│   ├ _generic.box-model.scss
│   └ _generic.normalize.scss
├─ _elements
│   ├ _elements.buttons.scss
│   ├ _elements.headings.scss
│   └ _elements.links.scss
├─ _objects
│   ├ _objects.lists.scss
│   └ _objects.media.scss
├─ _components
│   ├ _components.buttons.scss
│   ├ _components.header.scss
│   └ _components.logo.scss
└─ _trumps
     └ _trumps.widths.scss
```

##Name-spacing

To help devs from the future find code more easily, classes should be name-spaced so as to identify their type.  E.g. a class of  `.o-block`  will be found in `_objects.block.scss`.

### Common name-spaces

**`o-`**: Signify that something is an Object, and that it may be used in any number of unrelated contexts to the one you can currently see it in. Making modifications to these types of class could potentially have knock-on effects in a lot of other unrelated places. Tread carefully.

**`c-`**: Signify that something is a Component. This is a concrete, implementation-specific piece of UI. All of the changes you make to its styles should be detectable in the context you’re currently looking at. Modifying these styles should be safe and have no side effects.

**`u-`**: Signify that this class is a Utility class. It has a very specific role (often providing only one declaration) and should not be bound onto or changed. It can be reused and is not tied to any specific piece of UI.

Learn more:

> http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/


##BEM

We follow the [BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax/) methodology, using hyphenated class names rather than camel case. Single hyphens can be used in blocks, elements or modifiers to make names more readable.

```
.o-block__element--modifier {}
.o-block__element--modifier-name{}
```

##Sass

###Nesting

**DON'T**. One class should not depend on another. Classes should be portable without needing specific parents or grandparents. Specificity is also kept as low as possible this way.

Wrong:

```
.o-block {
    .o-block__element {}
}
```
Right:
```
.o-block {}
    .o-block__element {}
```
Use indenting to help give structure to related classes.

Only use nesting for pseudo elements and states such as `:before` and `:hover`, where you need to override a class based upon a dependancy or if you are using a BEM modifier to apply modified styles.

Acceptable:

```
.o-block {
    &:hover {}
    .no-js & {}
}

.o-block__title {
	.o-block--modifier & {}
}
```

###Elements

Elements are like children, they deserve names. Unless an element is truly generic and uses a global style, give it a name.

> "Your selectors should be as explicit as your reason for wanting to select something."
> — *[Harry Roberts](http://csswizardry.com/2012/10/a-classless-class-on-using-more-classes-in-your-html/)*

Wrong:
```
.o-block {
    h1 {}
}
```

Right:

```
.o-block {}
    .o-block__title {}
```

###Sibling and child selectors

It's OK to select an element using `:first-child` or `+` etc if it's necessary and appropriate. Think about the use case. Will the target always be the first child? What if it moves?

###Extend

**DON'T**. Extending creates relationships between rules based on shared traits that are purely coincidental. It makes it difficult to inspect an element and can disguise how bloated your rules are. Extend also produces larger files (after gzipping). **USE A MIXIN INSTEAD**.

Learn more:

> * [When to use @extend; when to use a mixin](http://csswizardry.com/2014/11/when-to-use-extend-when-to-use-a-mixin/) [Harry Roberts]
> * [Sass: Mixin or Placeholder?](http://www.sitepoint.com/sass-mixin-placeholder/) [Hugo Giraudel]
> * [Mixins are better for performance](csswizardry.com/2016/02/mixins-better-for-performance/) [Harry Roberts]

##Normalize
We use [Normalize.css](http://necolas.github.io/normalize.css/) to ensure consistency across browsers. **Do not directly modify these classes**, as the normalize.css file may be upgraded in future.

##Linting

We use [scss-lint](https://github.com/brigade/scss-lint). In addition to scss-lint's default settings, we use the file below.

```
linters:

  Indentation:
    allow_non_nested_indentation: true
    enabled: true
    character: tab
    width: 1

  LeadingZero:
    enabled: false

  NameFormat:
    enabled: false

  SelectorFormat:
    convention: ^(_)?[a-z]+-[a-z0-9-]+((_{2}|-{2})?[a-z0-9-]+)?(-{2}[a-z0-9-]+)?[a-z0-9]$
    convention_explanation: 'should be written in namespaced, hyphenated BEM format'
    ignored_types: [element]

  Shorthand:
    enabled: false

  SpaceAfterPropertyColon:
    enabled: true
    style: at_least_one_space

```

##Auto-prefixing

We use [autoprefixer](https://css-tricks.com/autoprefixer/) to manage vendor prefixes.

##Pixel-based units

Units should be written in pixels, rather than rems. Instead of a mixin, use something like [pxtorem](https://www.npmjs.com/package/pxtorem) to handle conversion.
