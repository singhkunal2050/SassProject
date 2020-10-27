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






