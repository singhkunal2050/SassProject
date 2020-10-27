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
