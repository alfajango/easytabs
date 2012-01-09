---
layout: default
title: jQuery EasyTabs Plugin
links:
  - title: Download from JSPkg.com
    href: http://jspkg.com/packages/easytabs
  - title: View Source or Fork on Github
    href: https://github.com/JangoSteve/jQuery-EasyTabs
  - title: View Live Demos
    href: http://jspkg.com/packages/easytabs/demos
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
  - title: Advanced demo
    href: '#advanced-demo'
  - title: Public methods
    href: '#public-methods'
  - title: Event hooks
    href: '#event-hooks'
  - title: More demos
    href: '#more-demos'
articles:
  - title: "More flexible layout, bookmarking, back- and forward-button support for browsers, and tab cycling"
    href: http://www.alfajango.com/blog/jquery-easytabs-plugin-now-more-flexible-and-usable
  - title: "Version 2.0: More versatile, event-hooks, and public methods"
    href: http://www.alfajango.com/blog/jquery-easytabs-plugin-v2/
  - title: "Version 2.1.2: uiTabs, collapsible, cancel, and callback parameters"
    href: http://www.alfajango.com/blog/jquery-easytabs-plugin-v2-1-2/
  - title: "Version 2.2: panel height transitions, and animation options"
    href: http://www.alfajango.com/blog/jquery-easytabs-plugin-v2-2/
  - title: "Version 2.3: ajax, nested tab-sets, and custom panel markup"
    href: http://www.alfajango.com/blog/jquery-easytabs-v2-3-released-ajax-tabs-and-more/
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

   <p>Optionally include the jquery [hashchange plugin](http://benalman.com/projects/jquery-hashchange-plugin/) (recommended) or [address plugin](http://www.asual.com/jquery/address/docs/) to enable forward-
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

<span id="advanced-demo"></span>

## Advanced Demo

Here's an example that uses some of the non-default configuration options:

<div id="full-container">
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

You can bind custom handlers to any of these events. You can even cancel the tab change by returning false in an `easytabs:before` binding.

Here are the events being fired from the cycling tabs in the Advanced
Demo above. <button id='stop-logging'>Click to stop</button>

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

<span id="more-demos"></span>

## More demos

Here are some more demos showcasing what you can do with EasyTabs. Check
out the source and the linked [tabs.css](css/tabs.css) to see how they're done.

### Nested tabs

<div class="tab-container" id="outer-container">
 <ul class='tabs'>
  <li class='tab'><a href="#nested-tab-1">Tab 1</a></li>
  <li class='tab'><a href="#nested-tab-2">Tab 2</a></li>
  <li class='tab'><a href="#nested-tab-3">Tab 3</a></li>
 </ul>
 <div class="panel-container">
  <div id="nested-tab-1">
   <h2>Heading 1</h2>
   <p>This is the content of the first tab.</p>
  </div>
  <div id="nested-tab-2">
   <h2>Heading 2</h2>
   <p>Stuff from the second tab.</p>
  </div>
  <div id="nested-tab-3">
   <h2>Heading 3</h2>
   <p>More stuff from the last tab.</p>

   <div class="tab-container" id="inner-container">
   <ul class='tabs'>
   <li class='tab'><a href="#tab-a">Subtab A</a></li>
   <li class='tab'><a href="#tab-b">Subtab B</a></li>
   <li class='tab'><a href="#tab-c">Subtab C</a></li>
   </ul>
   <div class="panel-container">
   <div id="tab-a">
   <h3>Heading A</h3>
   <p>This is a nested first tab</p>
   </div>
   <div id="tab-b">
   <h3>Heading B</h3>
   <p>This is a nested second tab</p>
   </div>
   <div id="tab-c">
   <h3>Heading C</h3>
   <p>This is a nested third tab</p>
   </div>
   </div>
   <br />
   </div>
  </div>
 </div>
</div>

<script type="text/javascript">
  $('#outer-container, #inner-container').easytabs();
</script>

### Tabs on side

<div id="tab-side-container">
 <ul>
  <li><a href="#side-tab1">Tab 1</a></li>
  <li><a href="#side-tab2">The Second Tab</a></li>
  <li><a href="#side-tab3">Tab C</a></li>
 </ul>
 <div class="panel-container">
  <div id="side-tab1">
   <h2>Configurations</h2>
   <p>This example has the animation disabled, so tab-switching is instantaneous. It also sets the active class names to custom names for more control over CSS stylization.</p>
  </div>
  <div id="side-tab2">
   <h2>Heading 2</h2>
   <p>Stuff from the second tab.</p>
  </div>
  <div id="side-tab3">
   <h2>Heading 3</h2>
   <p>More stuff from the last tab.</p>
  </div>
 </div>
</div>

<script type="text/javascript">
$('#tab-side-container').easytabs({
  animate: false,
  tabActiveClass: "selected-tab",
  panelActiveClass: "displayed"
});
</script>

### Tabs on bottom

<div id="tab-bottom-container">
 <div class="panel-container">
  <div id="bottom-tab1">
   <h2>Heading 1</h2>
   <p>This is the content of the first tab.</p>
  </div>
  <div id="bottom-tab2">
   <h2>Configuration</h2>
   <p>This example displays the second tab by default. Also, the tab-switching animation is slowed down to 4 seconds (2sec fade-out and 2sec fade-in).</p>
  </div>
  <div id="bottom-tab3">
   <h2>Heading 3</h2>
   <p>More stuff from the last tab.</p>
  </div>
 </div>
 <ul>
  <li><a href="#bottom-tab1">Tab 1</a></li>
  <li id="the-second-tab"><a href="#bottom-tab2">The Second Tab</a></li>
  <li><a href="#bottom-tab3">Tab C</a></li>
 </ul>
</div>
<br class='clear' />

<script type="text/javascript">
$('#tab-bottom-container').easytabs({
  animationSpeed: 2000,
  defaultTab: "li#the-second-tab"
});
</script>

### Collapsible and cancelable

<div id="tab-collapsible-container">
 <ul>
  <li><a href="#collapsible-tab1">Tab 1</a></li>
  <li><a href="#collapsible-tab2">The Second Tab</a></li>
  <li><a href="#collapsible-tab3">Tab C</a></li>
 </ul>
 <div class="panel-container">
  <div id="collapsible-tab1">
   <h2>Heading 1</h2>
   <p>This is the content of the first tab.</p>
  </div>
  <div id="collapsible-tab2">
   <h2>Heading 2</h2>
   <p>Stuff from the second tab.</p>
  </div>
  <div id="collapsible-tab3">
   <h2>Heading 3</h2>
   <p>More stuff from the last tab.</p>
  </div>
 </div>
</div>

<script type="text/javascript">
$('#tab-collapsible-container')
  .easytabs({
    collapsible: true
  })
  .bind('easytabs:before', function(e, tab){
    if ( ! tab.hasClass('active') && ! tab.hasClass('collapsed') ) {
      return confirm("Are you sure you want to switch tabs?");
    }
  });
</script>

### Disconnected tabs and panels

<div id="tab-disconnected-container">
 <ul>
  <li><a href="#disconnected-tab1">Tab 1</a></li>
  <li><a href="#disconnected-tab2">The Second Tab</a></li>
  <li><a href="#disconnected-tab3">Tab C</a></li>
 </ul>
 <br class='clear' />
 <p>Here is some random information that is not contained in the tabbed content and situated between the tabs and content divs.</p>
 <div class="panel-container">
  <div id="disconnected-tab1">
   <h2>Heading 1</h2>
   <p>This is the content of the first tab.</p>
  </div>
  <div id="disconnected-tab2">
   <h2>Heading 2</h2>
   <p>Stuff from the second tab.</p>
  </div>
  <div id="disconnected-tab3">
   <h2>Heading 3</h2>
   <p>More stuff from the last tab.</p>
  </div>
 </div>
</div>

<script type="text/javascript">
$('#tab-disconnected-container').easytabs();
</script>

### Transition Options

<div id="tab-transition-container" class="tab-container">
 <ul class="tabs">
  <li class="tab"><a href="#transition-tab1">Tab 1</a></li>
  <li class="tab"><a href="#transition-tab2">Tab 2</a></li>
  <li class="tab"><a href="#transition-tab3">Tab 3</a></li>
 </ul>
 <div class="panel-container">
  <div id="transition-tab1">
   <h2>Heading 1</h2>
   <p>Using slideUp and slideDown to transition between tab changes, <br />and fadeOut and fadeIn for collapsing transitions</p>
  </div>
  <div id="transition-tab2">
   <h2>Heading 2</h2>
   <p>Stuff from the second tab.</p>
  </div>
  <div id="transition-tab3">
   <h2>Heading 3</h2>
   <p>More stuff from the last tab.</p>
  </div>
 </div>
</div>

<script type="text/javascript">
$('#tab-transition-container').easytabs({
  collapsible: true,
  transitionIn: 'slideDown',
  transitionOut: 'slideUp',
  transitionCollapse: 'fadeOut',
  transitionUncollapse: 'fadeIn'
});
</script>

### As Form Sections

<form id="tab-nondiv-container" class='tab-container'>
 <legend>
  Form parts:
  <ul class='tabs'>
   <li class='tab'><a href="#nondiv-tab1">Tab 1</a></li>
   <li class='tab'><a href="#nondiv-tab2">Tab 2</a></li>
  </ul>
 </legend>
 <div class="field-container">
  <fieldset id="nondiv-tab1">
   <label>Tab 1 input</label>
   <input type="text" />
  </fieldset>
  <fieldset id="nondiv-tab2">
   <label>Tab 2 input</label>
   <input type="text" />
  </fieldset>
 </div>
</form>

<script type="text/javascript">
$('#tab-nondiv-container').easytabs({tabs: "legend ul li"});
</script>

### Previous and Next buttons

<div id="tab-buttons-container" class='tab-container'>
 <ul class='tabs'>
  <li class='tab'><a href="#buttons-tab1">Tab 1</a></li>
  <li class='tab'><a href="#buttons-tab2">Tab 2</a></li>
  <li class='tab'><a href="#buttons-tab3">Tab 3</a></li>
 </ul>
 <div class="panel-container">
  <div id="buttons-tab1" class="ui-tabs-panel">
   <br class='clear' />
   <h2>Heading 1</h2>
   <p>This is the content of the first tab.</p>
  </div>
  <div id="buttons-tab2" class="ui-tabs-panel">
   <br class='clear' />
   <h2>Heading 2</h2>
   <p>Stuff from the second tab.</p>
  </div>
  <div id="buttons-tab3" class="ui-tabs-panel">
   <br class='clear' />
   <h2>Heading 3</h2>
   <p>More stuff from the last tab.</p>
  </div>
 </div>
</div>

<script type="text/javascript">
$('#tab-buttons-container').easytabs();

var $tabContainer = $('#tab-buttons-container'),
    $tabs = $tabContainer.data('easytabs').tabs,
    $tabPanels = $(".ui-tabs-panel")
    totalSize = $tabPanels.length;

$tabPanels.each(function(i){
  if (i != 0) {
    prev = i - 1;
    $(this).prepend("<a href='#' class='prev-tab mover' rel='" + prev + "'>&laquo; Prev Page</a>");
  } else {
    $(this).prepend("<span class='prev-tab'>&laquo; Prev Page</span>");
  }
  if (i+1 != totalSize) {
    next = i + 1;
    $(this).prepend("<a href='#' class='next-tab mover' rel='" + next + "'>Next Page &raquo</a>");
  } else {
    $(this).prepend("<span class='next-tab'>Next Page &raquo</span>");
  }
});

$('.next-tab, .prev-tab').click(function() {
  var i = parseInt($(this).attr('rel'));
  var tabSelector = $tabs.children('a:eq(' + i + ')').attr('href');
  $tabContainer.easytabs('select', tabSelector);
  return false;
});
</script>

</div>
