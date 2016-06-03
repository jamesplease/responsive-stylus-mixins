# responsive-stylus-mixins

Responsive mixins for Stylus

### Installation

```
npm install responsive-stylus-mixins
```

Then, wherever you define mixins for your Stylus:

```styl
@import 'path/to/responsive-stylus-mixins'
```

From that point on, you can use these mixins in your Stylus.

### Motivation

I find the media query API to be a bit clunky. The query needs to wrap the thing
being styled, when I'd rather it be the other way around.

Responsive states, to me, are similar to any other states of an element, like
a hover state. And I'd like to define them similarly, too. Wouldn't it be
nice if you could do:

```styl
.my-thing
  width 200px

  +and-on-small-screens()
    width 100%
```

These mixins provide you with a similar API to the above.

### Mixins

#### `+respond-below( $width )`

Specify styling below `$width`. Useful if you want to, say, hide something
just on a mobile device.

```styl
.my-thing
  width 200px

  +respond-below(600px)
    width 100%
```

#### `+respond-above( $width )`

Specify styling above `$width`. Useful for targeting larger screens only.

```styl
.my-thing
  width 100%

  +respond-above(600px)
    width 500px
```

#### `+respond-between( $minWidth, $maxWidth )`

Specifies styling that takes affect between the two provided widths.

```styl
.my-thing
  width 200px

  +respond-between(600px, 1000px)
    display none
```

### Recommended Usage

I often set breakpoints the for my app as variables. For instance, I might have:

```styl
$md-screen = 768px
$lg-screen = 1080px
```

Then, I make it a habit to only use these specified breakpoints in the mixins.
This keeps the app's responsive aspects consistent and simple.
