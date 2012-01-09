---
layout: default
title: jQuery EasyTabs Plugin
links:
  - title: Download from JSPkg.com
    href: http://jspkg.com/packages/easytabs
  - title: View Source or Fork on Github
    href: https://github.com/JangoSteve/jQuery-EasyTabs
  - title: View Live Demos
    href: https://jspkg.com/packages/easytabs/demos
  - title: View Changelog
    href: https://github.com/JangoSteve/jQuery-EasyTabs/wiki/CHANGELOG
  - title: Report bug or request feature
    href: https://github.com/JangoSteve/jQuery-EasyTabs/issues
anchors:
  - title: Demo
    href: '#demo'
  - title: Installation
    href: '#installation'
  - title: Stylization
    href: '#stylization'
  - title: AJAX tabs
    href: '#ajax-tabs'
  - title: Configuration options
    href: '#configuration'
  - title: Public methods
    href: '#public-methods'
  - title: Event hooks
    href: '#event-hooks'
---

# JQuery EasyTabs Plugin

> Tabs with(out) style.

The jQuery EasyTabs plugin handles all of the functionality of tabs and none of the styling.

So, why use this instead of jQuery UI tabs?

As great as jQuery UI tabs are, UI tabs become a liability when it comes time to shed the out-of-box UI styling for something more custom.

After struggling to create custom-designed tabs, messing with numerous CSS classes, overriding all the default styling, and feeling constrained by the required markup, we finally decided to create our own lightweight, flexible jQuery tab plugin. Unlike jQuery UI tabs, which style and arrange your tabs and panels for you, this plugin handles only the functionality of the tabs. By leaving the styling and layout up to you, it is much easier to style and arrange your tabs the way you want.

Why you should use EasyTabs:

* Provides smooth transitions between panels when tab is selected
* Allows complete customization of appearance, layout, and style via CSS
* Supports back-button and forward-button in browsers
* Tabs are bookmarkable and SEO-friendly
* Loads AJAX content, or anything not already on the page
* Tabs can automatically cycle at a specified interval
* Adds NO global JS variables
* Can have multiple EasyTabs instances on one page
* Written in jQuery plugin format, chain-able with other jQuery commands
* Completely valid HTML markup
* Lightweight: the minified version is only 5KB
* Open-source and dual licensed under the MIT and GPL licenses
* Styles your tabs in any way (either through javascript or CSS)

<span id="demo"></span>

## Demo

<div id="tab-container" class='tab-container'>
 <ul class='tabs'>
   <li class='tab'><a href="#tabs1-html">HTML Markup</a></li>
   <li class='tab'><a href="#tabs1-js">Required JS</a></li>
   <li class='tab'><a href="#tabs1-css">Example CSS</a></li>
 </ul>
 <div class='panel-container'>
  <div id="tabs1-html">
   <h2>HTML Markup for these tabs</h2>

{% highlight html %}
<div id="tab-container" class="tab-container">
  <ul class='tabs'>
    <li class='tab'><a href="#tabs1-html">HTML Markup</a></li>
    <li class='tab'><a href="#tabs1-js">Required JS</a></li>
    <li class='tab'><a href="#tabs1-css">Example CSS</a></li>
  </ul>
  <div id="tabs1-html">
    <h2>HTML Markup for these tabs</h2>
    <!-- content -->
  </div>
    <div id="tabs1-js">
    <h2>JS for these tabs</h2>
    <!-- content -->
  </div>
  <div id="tabs1-css">
    <h2>CSS Styles for these tabs</h2>
    <!-- content -->
  </div>
</div>
{% endhighlight %}

   <p>The HTML markup for your tabs and content can be arranged however you want. At the minimum, you need a container, a collection of links for your tabs (an unordered list by default), and matching divs for your tabbed content. Make sure the tab `href` attributes match the
`id` of the target panel. This is standard semantic markup for in-page anchors.</p>
   <p>The class names above are just to make it easy to style. You can make them whatever you want, there's no magic here.</p>
  </div>
   <div id="tabs1-js">
   <h2>JS for these tabs</h2>

{% highlight html %}
<script src="/javascripts/jquery.js" type="text/javascript"></script>
<script src="/javascripts/jquery.hashchange.js" type="text/javascript"></script>
<script src="/javascripts/jquery.easytabs.js" type="text/javascript"></script>
{% endhighlight %}

   <p>Optionally include the jquery hashchange plugin (recommended) or address plugin to enable forward-
and back-button functionality.</p>

{% highlight js %}
$('#tab-container').easytabs();
{% endhighlight %}
  </div>
  <div id="tabs1-css">
   <h2>CSS Styles for these tabs</h2>
{% highlight css %}
.tabs { margin: 0; padding: 0; }
.tab { display: inline-block; background: #ccc; border: solid 1px; border-bottom: none; }
.tab a { display: block; padding: 5px; outline: none; }
.tab a:hover { text-decoration: underline; }
.tab.active { background: #fff; padding-top: 6px; position: relative; top: 1px; }
.tab a.active { font-weight: bold; }
.tab-container .panel-container { border: solid #000 1px; padding: 0 10px; }
{% endhighlight %}
  </div>
 </div>
</div>

<script type="text/javascript">
  $('#tab-container').easytabs();
</script>

<span id="installation"></span>

## Required Markup

The only rules you need to follow are these:

a container `<div>`
the container contains a collection (a `<ul>` by default) of links `<a>`
the container also contains panel divs (for the tabbed content), each div has a unique id that matches the href property of a link in the tab collection
Other than that, go nuts. The order of the elements does NOT matter. Your tabs could be before or after the panels. You can put non-tabbed content between the elements. You could even put the tabs inside one of the panels! It doesn't matter.

<span id="stylization"></span>

## Styling Tabs and Content

To style your tabs, you simply use your own CSS and stylesheet. Here's some very basic styling to get you started:

EasyTabs will simply add the .active class to the currently selected tab and panel. Also, any element inside of the currently-selected tab also gets the .active class. So, for example, if your tabs look like this:

{% highlight html %}
<ul>
  <li>
    <a href="#tab-1">Tab 1</a>
  </li><li>
  </li><li>
    <a href="#tab-2">Tab 2</a>
  </li>
</ul>
{% endhighlight %}

... and then you click on the first tab link, your markup will now look like this:

{% highlight html %}
<ul>
  <li class="active">
    <a href="#tab-1" class="active">Tab 1</a>
  </li><li>
  </li><li>
    <a href="#tab-2">Tab 2</a>
  </li>
</ul>
{% endhighlight %}

<span id="ajax-tabs"></span>

## AJAX Tabs

Sometimes we want to load content into a tab from another page via AJAX. In order to do that, we'll change the markup of the tabs a little bit.


<div id="ajax-tab-container" class='tab-container'>
 <ul class='tabs'>
   <li class='tab'><a href="ajax.html #html-content" data-target="#tabs-ajax-html">HTML Markup</a></li>
   <li class='tab'><a href="ajax.html #js-content" data-target="#tabs-ajax-js">Required JS</a></li>
 </ul>
 <div class='panel-container'>
  <div id="tabs-ajax-html"></div>
  <div id="tabs-ajax-js"></div>
 </div>
</div>

<script type="text/javascript">
  $('#ajax-tab-container').easytabs();
</script>

Also see the cache configuration option, and the easytabs:ajax:beforeSend and easytabs:ajax:complete event hooks below.

<span id="configuration"></span>

## Configuration Options

You can configure EasyTabs by passing in a hash of options when you instantiate it on a container. The following is a list of all the available options, including accepted and default values.

### Available Options

<table>
 <thead>
  <th>Option</th>
  <th>Description</th>
  <th>Values (default)</th>
 </thead>
 <tbody>
  <tr>
   <td>animate</td>
   <td>Makes content panels fade out and in when a new tab is clicked.</td>
   <td>true, false <br />(<code>true</code>)</td>
  </tr>
  <tr>
   <td>animationSpeed</td>
   <td>Controls the speed of the fading effect if <code>animate: true</code>.</td>
   <td><code>"slow"</code>, <code>"normal"</code>, <code>"fast"</code>, integer in milliseconds <br />(<code>"normal"</code>)</td>
  </tr>
  <tr>
   <td>cache<br /><em>v2.3</em></td>
   <td>Caches the content retrieved for ajax tabs after the first request, such that subsequent tab clicks only hide/show the content.</td>
   <td><code>true</code>, <code>false</code> <br />(<code>true</code>)</td>
  </tr>
  <tr>
   <td>collapsedByDefault<br /><em>v2.1</em></td>
   <td>Makes tabs collapsed by default (when the page is loaded) if <code>collapsible: true</code>. Note that if <code>defaultTab</code> is specified, then <code>collapsedByDefault</code> defaults to <code>false</code>.</td>
   <td><code>true</code>, <code>false</code> <br />(<code>true</code>)</td>
  </tr>
  <tr>
   <td>collapsedClass<br /><em>v2.1</em></td>
   <td>Adds specified class to tab when panel is collapsed. Only works for <code>collapsible: true</code>.</td>
   <td>any class name string <br />(<code>"collapsed"</code>)</td>
  </tr>
  <tr>
   <td>collapsible<br /><em>v2.1</em></td>
   <td>Makes panels collapse and un-collapse if active tab is clicked repeatedly.</td>
   <td><code>true</code>, <code>false</code> <br />(<code>false</code>)</td>
  </tr>
  <tr>
   <td>cycle<br /><em>v1.1.2</em></td>
   <td>Turns on automatic cycling through tabs, with the specified cycling interval in milliseconds.</td>
   <td><code>false</code>, integer in milliseconds <br />(<code>false</code>)</td>
  </tr>
  <tr>
   <td>defaultTab</td>
   <td>Selects the <code>&lt;li&gt;</code> tab to activate when page first loads.</td>
   <td>any single jquery selector <br /><em>e.g. <code>"li:first-child"</code> or <code>"li#tab-2"</code></em> <br />(<code>"li:first-child"</code>)</td>
  </tr>
  <tr>
   <td>panelActiveClass</td>
   <td>Adds specified class to the currently-selected content <code>&lt;div&gt;</code></td>
   <td>any class name string <br /><em>e.g. <code>"active"</code> or <code>"selected"</code></em> <br />(<code>"active"</code>)</td>
  </tr>
  <tr>
   <td>tabActiveClass</td>
   <td>Adds specified class to the currently-selected tab <code>&lt;li&gt;</code> (and it's descendants).</td>
   <td>any class name string <em>e.g. <code>"active"</code> or <code>"selected"</code></em> <br />(<code>"active"</code>)</td>
  </tr>
  <tr>
   <td>tabs<br /><em>v1.1.2</em></td>
   <td>The container element for your tabs, relative to the container element that easyTabs was applied to.</td>
   <td>any jquery selector referencing your collection of tabs <br /><em>e.g. <code>"ul#tabs > li"</code> or <code>"div#tab-container > span"</code></em> <br />(<code>"> ul > li"</code>, which selects the top-level <code><ul></code> within the container element)</ul></td>
  </tr>
  <tr>
   <td>transitionIn<br /><em>v2.2</em></td>
   <td>The <a href="http://api.jquery.com/category/effects/">jQuery effect</a> used to show the target panel when a tab is selected.</td>
   <td><code>'fadeIn'</code>, <code>'slideDown'</code> <br />(<code>'fadeIn'</code>)</td>
  </tr>
  <tr>
   <td>transitionOut<br /><em>v2.2</em></td>
   <td>The <a href="http://api.jquery.com/category/effects/">jQuery effect</a> used to hide the visible panel when a tab is selected.</td>
   <td><code>'fadeOut'</code>, <code>'slideUp'</code> <br />(<code>'fadeOut'</code>)</td>
  </tr>
  <tr>
   <td>transitionCollapse<br /><em>v2.2</em></td>
   <td>The <a href="http://api.jquery.com/category/effects/">jQuery effect</a> used to collapse the panel if <code>collapsible: true</code>.</td>
   <td><code>'fadeOut'</code>, <code>'slideUp'</code>, <code>'hide'</code> <br />(<code>slideUp</code>)</td>
  </tr>
  <tr>
   <td>transitionUncollapse<br /><em>v2.2</em></td>
   <td>The <a href="http://api.jquery.com/category/effects/">jQuery effect</a> used to un-collapse the panel if <code>collapsible: true</code>.</td>
   <td><code>'fadeIn'</code>, <code>'slideDown'</code>, <code>'show'</code> <br />(<code>slideDown</code>)</td>
  </tr>
  <tr>
   <td>updateHash<br /><em>v1.1.2</em></td>
   <td>Tells easyTabs whether or not to update the browser window's URL hash, useful for SEO and bookmarking.</td>
   <td><code>true</code>, <code>false</code> <br />(<code>true</code>)</td>
  </tr>
  <tr>
   <td>uiTabs<br /><em>v2.1</em></td>
   <td>Automatically uses class names and defaults of jQuery UI tabs, making it easy to switch from jQuery-UI tabs without needing to change any HTML or CSS styles.</td>
   <td><code>true</code>, <code>false</code> <br />(<code>false</code>)</td>
  </tr>
 </tbody>
</table>

Here's an example that uses some of the non-default configuration options:

<div id="tab-full-container" class='tab-container'>
 <div class='tabs'>
  <span class='tab'><a href="#tabs2-html">HTML Markup</a></span>
  <span class='tab' id="tab-2"><a href="#tabs2-js">The JS</a></span>
 </div>
 <div class='panel-container'>
  <div id="tabs2-html">
   <h2>HTML Markup for these tabs</h2>
{% highlight html %}
<div id="tab-full-container" class='tab-container'>
 <div class='tabs'>
  <span class='tab'><a href="#tabs2-html">HTML Markup</a></span>
  <span class='tab' id="tab-2"><a href="#tabs2-js">The JS</a></span>
 </div>
 <div class='panel-container'>
  <div id="tabs2-html">
   <h2>HTML Markup for these tabs</h2>
   <!-- content -->
  </div>
   <div id="tabs2-js">
   <h2>JS for these tabs</h2>
   <!-- content -->
  </div>
 </div>
</div>
{% endhighlight %}
  </div>
   <div id="tabs2-js">
   <h2>JS for these tabs</h2>
{% highlight js %}
$("#tab-full-container").easytabs({
  animate: true,
  animationSpeed: 1000,
  defaultTab: "span#tab-2",
  panelActiveClass: "active-content-div",
  tabActiveClass: "selected-tab",
  tabs: "> div > span",
  updateHash: false,
  cycle: 2000
});
{% endhighlight %}
  </div>
 </div>
</div>

<script type="text/javascript">
  $("#tab-full-container").easytabs({
    animate: true,
    animationSpeed: 1000,
    defaultTab: "span#tab-2",
    panelActiveClass: "active-content-div",
    tabActiveClass: "selected-tab",
    tabs: "> div > span",
    updateHash: false,
    cycle: 2000
  });
</script>

<span id="public-methods"></span>

## Public methods

EasyTabs currently has one public method, called select, which allows you to select a tab via JavaScript.

<button id='select-button'>Click me to select the second tab above (and stop the cycling)</button>

<script type="text/javascript">
$('#select-button').click( function() {
  $('#tab-full-container').easytabs('select', '#tab-2');
});
</script>

{% highlight js %}
$('#select-button').click( function() {
  $('#tab-full-container').easytabs('select', '#tab-2');
});
{% endhighlight %}

The parameter passed to select (`'#tab-2'` in the example above), can be either a jQuery selector to select the tab (e.g. one of the `<li>` elements), the tab link (e.g. one of the `<a>` elements), or it can be the id of one of the panels.

<span id="event-hooks"></span>

## Event Hooks

jQuery EasyTabs fires off three events to which you can bind your own functionality.

<table>
 <thead>
  <th>Option</th>
  <th>Description</th>
 </thead>
 <tbody>
  <tr>
   <td>easytabs:before</td>
   <td>Fires before a tab is selected.</td>
  </tr>
  <tr>
   <td>easytabs:midTransition</td>
   <td>Fires after the previous panel has been hidden, but before the next is shown.</td>
  </tr>
  <tr>
   <td>easytabs:after</td>
   <td>Fires after a tab has been selected (and after the panel is completely finished transitioning in).</td>
  </tr>
  <tr>
   <th colspan=2>For ajax tabs, there are two additional event hooks that fire:</th>
  </tr>
  <tr>
   <td>easytabs:ajax:beforeSend</td>
   <td>Fires before ajax request is made.</td>
  </tr>
  <tr>
   <td>easytabs:ajax:complete</td>
   <td>Fires when ajax request is complete (before the content is loaded).</td>
  </tr>
 </tbody>
</table>

You can bind custom handlers to any of these events. You can even cancel the tab change by returning false in an `easytabs:before` binding. <button id='stop-logging'>Click to stop</button>

<div id="tab-console">
  <div class='logged-event-group'>Waiting for events...</div>
</div>

<script type="text/javascript">
var log = true;

$('#stop-logging').click( function() {
  log = false;
});

$('#tab-full-container')
  .bind('easytabs:before', function() {
    if ( log ) {
      var $tabConsole = $('#tab-console'),
          $lastGroup = $tabConsole.find('.logged-event-group').slideUp();

      $tabConsole
        .append("<div class='logged-event-group'><span class='logged-event'><code>easytabs:before</code> fired</span></div>");
      setTimeout( function() { $lastGroup.remove(); }, 500);
    }
  })
  .bind('easytabs:midTransition', function() {
    if ( log ) {
      $('#tab-console')
        .find('.logged-event-group').last()
          .append("<span class='logged-event'><code>easytabs:midTransition</code> fired</span>");
    }
  })
  .bind('easytabs:after', function() {
    if ( log ) {
      $('#tab-console')
        .find('.logged-event-group').last()
          .append("<span class='logged-event'><code>easytabs:after</code> fired</span>");
    }
  });
</script>

The above logging is being done with this JS:

{% highlight js %}
var log = true;

$('#stop-logging').click( function() {
  log = false;
});

$('#tab-full-container')
  .bind('easytabs:before', function() {
    if ( log ) {
      var $tabConsole = $('#tab-console'),
          $lastGroup = $tabConsole.find('.logged-event-group').slideUp();

      $tabConsole
        .append("<div class='logged-event-group'><span class='logged-event'>easytabs:before fired</span></div>");
      setTimeout( function() { $lastGroup.remove(); }, 500);
    }
  })
  .bind('easytabs:midTransition', function() {
    if ( log ) {
      $('#tab-console')
        .find('.logged-event-group').last()
          .append("<span class='logged-event'>easytabs:midTransition fired</span>");
    }
  })
  .bind('easytabs:after', function() {
    if ( log ) {
      $('#tab-console')
        .find('.logged-event-group').last()
          .append("<span class='logged-event'>easytabs:after fired</span>");
    }
  });
{% endhighlight %}

All callbacks also pass parameters to the handler function, as described in [this post](http://www.alfajango.com/blog/jquery-easytabs-plugin-v2-1-2/).

The ajax event hooks have their own set of data passed as well, see [this post for more detail and examples](http://www.alfajango.com/blog/jquery-easytabs-v2-3-released-ajax-tabs-and-more/#ajax-tabs).

The `easytabs:midTransition` is also when the URL gets updated if `updateHash` is true (which it is by default). The URL must be updated precisely after the previous panel has disappeared from the page, but before the next panel appears to avoid making the browser window jump to the top of the panel when the URL is updated.

<span id="demos"></span>

## Live demos

 Many tab containers on one page (with various configurations)

 Disconnected tabs and tabbed content demo

</div>
