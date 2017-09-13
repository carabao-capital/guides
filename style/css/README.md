# Introduction

A styleguide is a picture of a code's ideal state. It is a key document for teams to work together, sharing the same techniques and reasoning on how we structure our code. Doing this provides the following benefits: 

* Maintainable and Scalable code structure
* Faster identification of style bugs, making it easier to fix something that is broken
* Provides fast and smooth onboarding for future newcomers which will maintain the existing styles in the system

That being said, these set of rules are opinionated which make this a living document. This makes it open for any changes and improvements.

---

# File Format

* File names should be in `dash-case`
* File names should be the same name with the component name.
```
  // Bad
  // requirements_submission.scss
  // .requirements-box { ... }

  // Good
<nav class="nav">
  <ul class="list-group">
    <li class="item"><a href="/home"> Home </a></li>
    <li class="item"><a href="/profile"> Profile </a></li>
    <li class="item"><a href="/logout"> Logout </a></li>
  </ul>
</nav>
```

* For layout classes, avoid altering its contents visual properties to ensure consistency
```
  .main-container {
    display: flex;
    align-items: center;
    justify-content: center;

    > .content {
      // This button will be inconsistent with the others
      > .btn {
        padding: 15px;
        color: blue;
      }
    }

    > .sidebar { ... }
  }

```

* Class declarations should have the css compositions first then the utility classes.

```
  // Bad
  class="marginBottom-s marginTop-s new-form-container"

  // Good
  class="new-form-container marginBottom-s marginTop-s"
```

* Refer to RSCSS when creating components
# RSCSS

Reference: [rscss.io](http://rscss.io/)

Reasonable System for CSS Stylesheet Structure is a set of simple ideas to guide your process of building maintainable CSS. 

According to the site:

> rscss is an attempt to make sense of all these. It is not a framework. It's simply a set of ideas to guide your process of building maintainable CSS for any modern website or application.

We will be following some of their guidelines and tweak them a little bit according to our preferences. Feel free to state your opinions if there is something that requires swaying a little bit from the guide to fit our current workflow.

---

# Components

When developing UI, it is important that to think in components. Consider each piece of the UI as an individual "component".

![](https://static.notion-static.com/1427fbd5b07242e49fc79042d0d1b5f1/component-example.png)

Components will be named with **at least two (2) words** , with a dash between each word. Examples of components:

  * A like button (.like-button)
  * A search form (.search-form)
  * A news article card (.article-card)
* A namespaced component (.sample-custom-header)

  ---

# Elements

  Elements are all of the things inside the component.

  ![](https://static.notion-static.com/2729fea3f0b847e4a9a3c628cf93429e/component-elements.png)

## Element Selectors

  Prefer to use the > child selector whenever possible. This prevents bleeding through nested components, and performs better than descendant selectors.

  .article-card {
    .title { /* okay */ }
    > .author { /* ✓ better */ }
  }

## On multiple words

For those that need two or more words, concatenate them without dashes or underscores.

.profile-box {
  > .firstname { /* ... */ }
  > .lastname { /* ... */ }
  > .avatar { /* ... */ }
}

## Avoid Tag Selectors

Use classnames whenever possible. Tag selectors are fine, but they may come at a small performance penalty and may not be as descriptive.

.article-card {
  > h3 { /* ✗ avoid */ }
  > .title { /* ✓ better */ }
}

---

# Variants

A variant is a different representation of styling. Both components and elements may have their own specific variants.

![](https://static.notion-static.com/9493ef57370541da817ddd1a1fa4db53/component-modifiers.png)

## Naming Variants

Classnames for variants will be prefixed by a dash (-).

.like-button {
  &.-wide { /* ... */ }
  &.-short { /* ... */ }
  &.-disabled { /* ... */ }
}

## Element Variants

.shopping-card {
  > .title { /* ... */ }
  > .title.-small { /* ... */ }
}

## Dash prefixes

Dashes are the preferred prefix for variants.

- It prevents ambiguity with elements.
- A CSS class can only start with a letter, _ or -.
- Dashes are easier to type than underscores.
- It kind of resembles switches in UNIX commands (gcc -O2 -Wall -emit-last).

---

# Nested Components

![](https://static.notion-static.com/a44f2f76090844868663b407ee57fa44/component-nesting.png)

```
<div class='article-link'>
  <div class='vote-box'>
  ...
  </div>
  <h3 class='title'>...</h3>
  <p class='meta'>...</p>
</div>
```

## Nested Component Variants

A component may need to appear a certain way when nested in another component. Avoid modifying the nested component by reaching into it from the containing component.
