Angular Screenfull
==================

Angular screenfull is a wrapper around the [Screenfull library](https://github.com/sindresorhus/screenfull.js/), it allows you to use the HTML5 fullscreen API in an Angular way.

You can see the API documentation with some demo examples [here](http://hrajchert.github.io/angular-screenfull/#/api).

## Install

#### Download via bower or look for the files in the dist folder

    $ bower install --save angular-screenfull

#### Import it to your page

    <script src="bower_components/screenfull/dist/screenfull.js"></script>
    <script src="bower_components/angular-screenfull/dist/angular-screenfull.min.js"></script>

Note that [screenfull](https://github.com/sindresorhus/screenfull.js) is added as a bower dependency
so if you use [main bower files](https://github.com/ck86/main-bower-files) the dependency will be added for you

#### Enable it on your app

    angular.module('myModule', ['angularScreenfull']);

## Use it

In its simplest form, you can do something like this

```html
<div ngsf-fullscreen>
    <p>This is a fullscreen element</p>
    <button ngsf-toggle-fullscreen>Toggle fullscreen</button>
</div>
```

The `ngsf-fullscreen` indicates which element is going to be the fullscreen element and the `ngsf-toggle-fullscreen`
will toggle the fullscren when clicked.

Note that you can have multiple `ngsf-fullscreen` elements living side by side, the other directives require that a
parent controller exists.

# A word in CSS

When the element that uses directive `ngsf-fullscreen` becomes fullscreen a class is added using the `$animation` service, so you can add animations to the transition.

Note that this library doesn't come with any CSS, so if you would like your element to occupy the whole screen (and I imagine that you want to), you should add something like this to your CSS.

```css
.fullscreen {
    width: 100%;
    height: 100%;
}
```

# Export its functionality

You can also expose the element controller trough its directive name. So for example you can achieve the same result
using this

```html
<div ngsf-fullscreen="fullscreenCtrl">
    <p>This is another fullscreen element</p>
    <button ng-click="fullscreenCtrl.toggleFullscreen()">Toggle fullscreen</button>
</div>
```

We also provide directives to show the elements based on the fullscreen status, so for example you can have this

```html
<div ngsf-fullscreen>
    <p>This is yet another fullscreen element</p>
    <a ngsf-toggle-fullscreen show-if-fullscreen-enabled>
        <i show-if-fullscreen=false>Icon for enter fullscreen</i>
        <i show-if-fullscreen=true>Icon for exit fullscreen</i>
    </a>
</div>
```


# The problem with F11

As stated in [this bug](https://github.com/hrajchert/angular-screenfull/issues/1), it appears that browser vendors don't allow a user script to tap into the `F11` hotkey for security reasons. That means that we can only detect that the page is in fullscreen mode when the `HTML5 fullscreen API` is used.

If you can find a way to overcome this problem please let me know!
