# Frontend Guidelines

## CSS

### CSS Principles
> Follow these rules unless there is a technical reason why you can’t, eg: CMS produced code

### Sass
Using Sass allows us to do many things.

#### Modularity - files do one thing
One of these things is to split our files into modular components, for example:
````
_source/
|- styles/
|  |- _tools/
|    |- _tools.typography.scss
|  |- _settings/
|    |- _settings.global.scss
|  |- _objects/
|    |- _objects.layout.scss
|  |- _generic/
|    |- _generic.box-sizing.scss
|  |- _elements/
|    |- _elements.links.scss
````
Think about where your CSS should be written. If a style you write isn’t related to anything in an existing file, create a new one.

#### Generate contents
@todo: a bit about [sass-generate-contents](https://github.com/andrewbrandwood/gulp-sass-generate-contents).

#### Source maps
We use an automatically built source map to see where styles are in `.scss` file when we inspect in the browser.

#### Variables
@todo: a bit about variables:
- why we use them
- naming conventions

### No excessive nesting of classes
```scss
.header {
	&__navigation {
		&--small {}
	}
}
```
Is unnecessary…
```scss
.header {}
.header__navigation {}
.header__navigation--small {}
```
The above is more readable and makes it easier to <kbd>cmd</kbd> + <kbd>f</kbd> in a project to find a selector that you’ve found in the browser.

### Nesting is acceptable for:
#### States, eg:
```scss
.link {
	&:hover {}
}
```

#### Pseudo elements, eg:

```scss
.list__item {
	&::before,
	&::after {}
}
```

#### Dependencies, eg
```scss
// @todo: example
```

### Comments
Sensibly use comment blocks detailing the start of component styles:
```scss
// todo: example
```

Comment when something you’ve written is out of the ordinary so other developers know why you had to do it:
```scss
// todo: example
```

#### CSS Methodology
- [BEM](http://csswizardry.com/2013/01/mindbemding-getting-your-head-round-bem-syntax)
- [ITCSS](https://speakerdeck.com/dafed/managing-css-projects-with-itcss)

#### Selectors
Namespaces: refer to [More Transparent UI Code with Namespaces](http://csswizardry.com/2015/03/more-transparent-ui-code-with-namespaces/#the-namespaces) by Harry Roberts.

#### Properties
- Don’t prefix new CSS properties eg `-webkit-transform-` - Autoprefixer does this (it also removes un-needed prefixes that have been left in)
- Don’t use a mixin to convert to `rem` units - [postcss-pxtorem](https://github.com/cuth/postcss-pxtorem) does this. Writing in pixels is easier to take values from PSDs etc

#### Folder structure (including ITCSS)
eg:
`sass/settings/_settings.breakpoints.scss`
- @todo more

#### Normalize
We use [Normalize](https://necolas.github.io/normalize.css) as a CSS base.

**Don’t touch this file!**

#### Linting
- [scss-lint](https://github.com/brigade/scss-lint)
- config file - we need to standardise this and create a repository for config files
- `@todo: that ^`

#### CSS Style
- Grouping - Alphabetised properties (controversial!)
- Comment at top of file as per [sass-generate-contents](https://github.com/andrewbrandwood/gulp-sass-generate-contents)
