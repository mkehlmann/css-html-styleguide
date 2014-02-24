SALT CSS/HTML Syntax + Style Guide {
==================

SALT is a "mobile-first" site.  The user experience on a mobile device should feel as seamless as on a desktop.  We also want to load only the static resources needed.
Our ability to create changable layouts is based on "The Grid".  Please see the following for an explanation.

http://foundation.zurb.com/docs/components/grid.html

## <a name='TOC'>Table of Contents</a>

  1. [HTML5 Support](#html5)
  2. [General Rules](#general)
  3. [Whitespace](#whitespace)
  4. [!important](#important)
  5. [Selector Naming](#naming)
  6. [File Size and Structure](#structure)
  7. [Available Modules](#modules)
  8. [Creating Buttons](#buttons)
  9. [Understanding SASS](#sass)
  10. [Automated Testing](#testing)

## <a name='html5'>HTML5 Support</a>

In order to provide a consistent experience, we use a plugin "Webshims lib" to provide fallback support for browsers that don't support certain features of HTML5. This allows you to use HTML5 standard markup and validation patterns that will work in these non-compliant browsers (IE9, Safari, etc) out of the box.

For a full list of the features and more info please refer to:

http://afarkas.github.io/webshim/demos/

## <a name='general'>General Rules</a>

No inline styles -- all styles should belong in an external stylesheet

If you are unfamiliar with the box model, do not pass GO, read this: https://developer.mozilla.org/en-US/docs/Web/CSS/box_model

Rule Precedence -- Should be alphabetical

```css
.foo {
  border: 1px solid black;
  color: black;
}
```

## <a name='whitespace'>Whitespace</a>

* _Never_ mix spaces and tabs for indentation.
* Use tabs (set to a size of 4 spaces)
* One space after selector before opening curly bracket
* After colon, one space before rule
* No one liners

```css
//GOOD
.foo {
  border: 1px solid black;
}

//BAD
.foo{border :1px solid black; color: black;}
```

Tip: configure your editor to "show invisibles" or to automatically remove
end-of-line whitespace.

Tip: use an [EditorConfig](http://editorconfig.org/) file (or equivalent) to
help maintain the basic whitespace conventions that have been agreed for your
code-base.

## <a name='important'>!important</a>
Avoid the use of !important.  If you feel you must use it, document the heck out of why you did.

## <a name='naming'>Selector Naming</a>

Selectors should use dashes in favor of underscores
All words in a selector should be lower case

```css
//GOOD
.foo-bar {
  border: 1px solid black;
}

//BAD
.FOO_bar {
  border: 1px solid black;
}
```

## <a name='structure'>File Size and Structure</a>
Files should be no more than 500 lines, logic permitting
Modules should be organized into files based on their function.
For example, the buttons module can be seen at: http://foolink.com

"If two modules are very similar with only barely noticable changes to stuff like the shadow, padding and colours combine them into one."


## <a name='modules'>SALT CSS Module Structure</a>

  SALT's CSS is currently under renovation with the goal of using a defined modular structure. As this is a Work-In-Progress, this document will be updated with the most current modular structure. This is subject to change with SWD-4881, Refactoring of CSS Modules. 
  
  As of 2/24/2014 and SWD-4880, a team of developers has broken the existing CSS into this modular structure currently in place in Predev5 Accurev Stream:

  1. Components -- contains modules that should be global to the SALT Site.
      a.  utilityClasses.css -- helpful classes to ease CSS positioning, alignment, Foundation's hide-for-x classes
      b.  icons.css -- site-wide CSS code for creating icons
      c.  typography.css -- web fonts
      d.  forms.css -- site-wide styling for form elements
      e.  panels.css -- site-wide CSS for panel styling
      f.  tiles.css
      g.  deprecated.css -- legacy code that most likely isn't being used in any HTML, or was being overwritten by other styles. Keeping for now to be safe.
      h.  toRefactor.css -- Old CSS that should really be refactored along with its HTML and Dust. Most of what's in this file can be re-created with proper use of column nesting, panels, and other Foundation classes.
      i.  docs.css -- should be refactored into more semantic global modules
      j.  tooltips.css
      k.  overlays.css
      l.  buttons.css
      m.  orbit.css

  3. Navigation -- CSS for navigation elements
      a.  header.css
      b.  navigation.css
      c.  breadcrumbs.css
  
  5. Themes -- CSS for different sections of the site that have distinct "look and feel", and individual/one-off styling
      a.  basicPage.css -- Default page styling
      b.  KWYO.css
      c.  theRed.css
      d.  moneyCoachProgress.css -- Money Coach/bunchball progress styling
      e.  badges.css -- Money Coach badges
      f.  liveChat.css
      g.  quizWidget.css -- homepage quiz/survey
      h.  feed-module.css -- Twitter and Blog feed modules
      i.  glossary.css
      j.  lessonsPage.css
      k.  pressPage.css
      l.  tools.css
      m.  vlc.css

  Modules yet to be sorted:
    1. colorbox.css -- CSS still used by remaining colorbox modals. Please don't change this unless absolutely necessary
    2. featuredHeadline.css -- Module for creating the FEATURED section header on the homepage, the Content Type Sort pages, etc.

  

## <a name='buttons'>How To Create Buttons</a>

All basic buttons need to have this basic HTML and CSS structure:

```html
<a class="button base-btn pink-btn">See My Loans</a>
```

In this example:
  * .button includes some needed Foundation CSS and provides some overriding of ugly Foundation styles. 
  * .base-btn provides the basic structure and size, border radius, font styling
  * .pink-btn provides the background gradient and text shadow to make a standard SALT pink button.

You can include different classes to create variations:
```html
<a class="button base-btn larger-btn black-btn">See My Loans</a>
```

In this example:
  * .button still provides necessary overrides
  * .base-btn still provides the basic structure and size, border radius, font styling
  * .larger-btn creates a... well, a larger button with padding, font-size and border-radius changes
  * .black-btn provides the background gradient and text shadow to make a black button.

NOTE: All of the arrows/chevrons in SALT buttons are added through CSS :before and :after pseudo-classes. This means you never have to type the '&lt;' or '&gt;' character in your HTML for your buttons.

## <a name='sass'>SASS</a>
  * Pragmatic Sass: http://insideasa.amsa.com/sites/FnctAreas/InfoSvcs/SaltyDawgz/Site%20Documents/pragmatic-guide-to-sass_p1_0.pdf

## <a name='testing'>Integration with Automated Testing</a>
  * In order to make automated testing easier:
    All Buttons, Links, Input Fields, and Dropdowns should have an ID or Class. (TODO add link to naming conventions for classes and ID's)

*Based on the excellent work done by Richard Powell [here](https://github.com/byrichardpowell/CSS-Style)*

}
=
