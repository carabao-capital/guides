CSS Stynax Guidelines
---------------------

* Prefer using the longhand properties over shorthand properties for more clarity and readability.

```
// Wrong

.sample-component {
padding: 10px 20px 10px 20px;
}

// Correct

.sample-component {
  padding-top: 10px;
  padding-right: 20px;
  padding-bottom: 10px;
  padding-le: 20px;
}
```

* Avoid hooking styles to IDs at all costs.
```
// Wrong

#sample-id {
  background: #000000;
}

// Correct

.sample-class {
  background: #000000;
}
```

* Avoid using `!important` at all costs.

```
// Never do this

.sample-component {
  padding-top: 10px !important;
  padding-right: 10px !important;
  padding-bottom: 10px !important;
  padding-left: 10px !important;
}
```

* Use variables for single property which accepts a custom value. Avoid using magic numbers as much as possible.
```
// Avoid
.sample-component {
  padding-top: 109px;
  width: 73px;
}

// use map-get to select the value
// all the values are available in variables.scss
.sample-component {
  padding-top: map-get($spacing, "l");
  width: map-get($spacing, "m");
}
```

* Write detailed comments for code that isn't self-documenting:
  * Uses of z-index
    ```
    // Enter a detailed comment here about the z-index usage

    .sample-component {
      position: relative;
      z-index: 9999;
    }
    ```

  * Compatibility or browser-specific hacks
  ```
  // Enter a detailed explanation of the reason behind using such hack
  // webkit hack
  .selector:not(*:root) { padding: 20px; }
  ```


* Do not nest selectors more than three levels deep!
```
.main-layout {
  > .sidebar {
    > nav {
      // This is not inception, no need to get deeper
    }
  }
}
```

* Prefer `dash-case` over `camelCase` when naming css classes, only utility classes that has `styleProperty-value` is written in `camelCase` 
```
// bad
.pageContainer { ... }
// better
.page-container { ... }
// utility class
.paddingTop-xs { ... }
```

* Don't use `div` for everything.
```
// Bad
<div class="nav">
  <div class="list-group">
    <div class="item"><a href="/home"> Home </a></div>
    <div class="item"><a href="/profile"> Profile </a></div>
    <div class="item"><a href="/logout"> Logout </a></div>
  </div>
</div>

// Good
<nav class="nav">
  <ul class="list-group">
    <li class="item"><a href="/home"> Home </a></li>
    <li class="item"><a href="/profile"> Profile </a></li>
    <li class="item"><a href="/logout"> Logout </a></li>
  </ul>
</nav>
```

9.Refer to [rscss.io](http://rscss.io/) when creating components

References:
-----------

*  [https://csswizardry.com/2016/12/css-shorthand-syntax-considered-an-anti-pattern/](https://csswizardry.com/2016/12/css-shorthand-syntax-considered-an-anti-pattern/)
