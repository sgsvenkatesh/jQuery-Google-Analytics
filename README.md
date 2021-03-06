jQuery Google Analytics Plugin
=========================

A jQuery plugin that helps you set up [Event Tracking With Google Analytics](https://developers.google.com/analytics/devguides/collection/gajs/eventTrackerGuide).


Features
--------

* Reading event tracking variables from HTML data attributes as default.
* Reading pageview tracking variables from HTML data attributes as default.
* Validates values for type before pushing.
* Support for dynamically created DOM objects and attributes created using `$.data()`.
* Support delay for links to ensure that the logging to Google Analytics occurs before redirect.

Dependencies
------------

* jQuery v1.7.0 (or higher). (HTML5 data attributes required)
* Google Analytics script with `_gaq` variable set.

Usage
-----
The default behaviour of the plugin is to automagically search your page for any elements containing html5 data attributes that start with `data-ga`.

This will then add tracking defaulting to the more commonly used `_trackevent` method setting the parameters to pass to that method from the corresponding data attributes.

To alter that default behaviour a data api has been provided.

e.g.

``` js
// Unbind the default behaviour
$(document).off("ready.ga").on("ready", function () {

    // Set some options the ones below are the defaults.
    var options = {
            event: "trackEvent", // The event name unprefixed. 
            handler: "click", // The eventhandler to trigger the tracking. 
                            // Using 'load' will track immediately.
            debug: false // Whether to run in debug mode.
    };

    // Bind using the custom selector.        
    $("selector").googleAnalytics(options);
       
});
``` 

 - **event**
   The type of Google event to track. Used unprefixed with '_'. Currently tracked events are.

  1. [_trackEvent(category, action, opt_label, opt_value, opt_noninteraction)](https://developers.google.com/analytics/devguides/collection/gajs/eventTrackerGuide).
  2. [_trackPageview(opt_pageURL)](https://developers.google.com/analytics/devguides/collection/gajs/methods/gaJSApiBasicConfiguration#_gat.GA_Tracker_._trackPageview).

 - **handler**
   A string containing one or more DOM event types, such as "click" or "submit," or custom event names.

 - **debug**
   Whether the plugin is in debug mode. If set to true the plugin will log the argument array to the development console.

 
Examples
-----
``` html
<a class="trackEvent" href="#" data-ga-category="category" data-ga-action="action"  data-ga-label="label" >
    Click to test trackEvent
</a>
```
``` js
$("a.trackEvent").googleAnalytics({event:"trackEvent", handler:"click"});
```

Will bind the `_trackEvent` analytics method to click event of the selected DOM object.
``` html
<a class="trackPageview" href="#" data-ga-url="/some other url">Click to test trackPageview</a>
``` 
``` js
$("a.trackPageview").googleAnalytics({event:"trackPageview", handler:"click"});    
```
	
Will bind the `_trackPageview` analytics method to click event of the selected DOM object.

Please use the [GitHub issue tracker](https://github.com/JimBobSquarePants/jQuery-Google-Analytics-Plugin/issues) for bug
reports and feature requests.

