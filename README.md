# SassProject

## Using CSS Prepocessor 

- SASS Synatactically awesome style sheets
- CSS Preprocessors
- Files gets compiled into css directly to css 
-  gulp can be used or a vs code extension for live compiling 

## Two types of syntax

### .scss
  Same like css with added features 

### .sass 
  Without brackets with indentation synatax 

<br>

# Major Features/Advantages

### Variable 
  We can use $varname to store variabe
  
      color:$varname;
<br>

### Nesting 

#### Wihout Sass

    nav{
      display:flex;
      color:red
    }

    nav ul {
      padding:10px
    }

    nav .logo{
      height:100px
    }



#### With Sass
   
    nav{
      display:flex;
      color:red;
      ul{
        padding:10px
      }
      .logo{
        height:100px
      }
    }

<br>

### Modules 

#### We can Reuse SASS Components and MOdules in our filess by importing

    use "sass:color";
    .button {
      $primary-color: #6b717f;
      color: $primary-color;
      border: 1px solid color.scale($primary-color, $lightness: 20%);
    }

**POST COMPILATION**

    .button {
      color: #6b717f;
      border: 1px solid #878d9a;
    }


### Mixins and Functions 
Gives us all the functional features like any other programming languages

**Mixins** 

    @mixin reset-list {
      margin: 0;
      padding: 0;
      list-style: none;
    }

    @mixin horizontal-list {
      @include reset-list;

      li {
        display: inline-block;
        margin: {
          left: -2px;
          right: 2em;
        }
      }
    }

    nav ul {
      @include horizontal-list;
    }

*OUTPUT*

    nav ul {
      margin: 0;
      padding: 0;
      list-style: none;
    }
    nav ul li {
      display: inline-block;
      margin-left: -2px;
      margin-right: 2em;
    }


**FUNCTIONS**

    @function pow($base, $exponent) {
      $result: 1;
      @for $_ from 1 through $exponent {
        $result: $result * $base;
      }
      @return $result;
    }

    .sidebar {
      float: left;
      margin-left: pow(4, 3) * 1px;
    }

*OUTPUT*

    .sidebar {
      float: left;
      margin-left: 64px;
    }


### Inheritance using extends

    .error {
      border: 1px #f00;
      background-color: #fdd;

      &--serious {
        @extend .error;
        border-width: 3px;
      }
    }

*OUTPUT*

    .error, .error--serious {
      border: 1px #f00;
      background-color: #fdd;
    }
    .error--serious {
      border-width: 3px;
    }


### Operators 

**Sass has a pretty standard order of operations, from tightest to loosest:**

- The unary operators not, +, -, and /.
- The *, /, and % operators.
- The + and - operators.
- The >, >=, < and <= operators.
- The == and != operators.
- The and operator.
- The or operator.
- The = operator, when it’s available.



### FLOW CONTROL

- @if controls whether or not a block is evaluated.

- @each evaluates a block for each element in a list or each pair in a map.

- @for evaluates a block a certain number of times.

- @while evaluates a block until a certain condition is met.


**if**

    @mixin triangle($size, $color, $direction) {
      height: 0;
      width: 0;

      border-color: transparent;
      border-style: solid;
      border-width: $size / 2;

      @if $direction == up {
        border-bottom-color: $color;
      } @else if $direction == right {
        border-left-color: $color;
      } @else if $direction == down {
        border-top-color: $color;
      } @else if $direction == left {
        border-right-color: $color;
      } @else {
        @error "Unknown direction #{$direction}.";
      }
    }

    .next {
      @include triangle(5px, black, right);
    }

*OUTPUT*

    .next {
      height: 0;
      width: 0;
      border-color: transparent;
      border-style: solid;
      border-width: 2.5px;
      border-left-color: black;
    }


**each**

    $sizes: 40px, 50px, 80px;

    @each $size in $sizes {
      .icon-#{$size} {
        font-size: $size;
        height: $size;
        width: $size;
      }
    }

*OUTPUT*

    .icon-40px {
      font-size: 40px;
      height: 40px;
      width: 40px;
    }

    .icon-50px {
      font-size: 50px;
      height: 50px;
      width: 50px;
    }

    .icon-80px {
      font-size: 80px;
      height: 80px;
      width: 80px;
    }


### for 

    @for $i from 1 through 3 {
      ul:nth-child(3n + #{$i}) {
        background-color: lighten($base-color, $i * 5%);
      }
    }

*OUTPUT*

    ul:nth-child(3n + 1) {
      background-color: #004080;
    }

    ul:nth-child(3n + 2) {
      background-color: #004d99;
    }

    ul:nth-child(3n + 3) {
      background-color: #0059b3;
    }


### while 

    /// Divides `$value` by `$ratio` until it's below `$base`.
    @function scale-below($value, $base, $ratio: 1.618) {
      @while $value > $base {
        $value: $value / $ratio;
      }
      @return $value;
    }

    $normal-font-size: 16px;
    sup {
      font-size: scale-below(20px, 16px);
    }

*OUTPUT*

    sup {
      font-size: 12.36094px;
    }
