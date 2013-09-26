chrome-tabs
===

[Browserify](http://browserify.org/) compatible [chrome-tabs](https://github.com/adamschwartz/chrome-tabs) by Adam Schwartz.

[Demo](http://adamschwartz.co/chrome-tabs/)

![](http://adamschwartz.co/chrome-tabs/chrome-tabs.gif)

Requirements
---

1. jQuery
2. [brfs](https://github.com/substack/brfs) transform to inline HTML and CSS resources when browserified:

```sh
$ browserify -t brfs chrome-tabs.js > bundle.js
```

Usage
---

```javascript
var chromeTabs = require("chrome-tabs")

// Add chrome tabs CSS to page head
chromeTabs.insertCss()

// Init chrome tabs in the container .chrome-tabs-shell
var $chromeTabsExampleShell = $(".chrome-tabs-shell")

chromeTabs.init({
  $shell: $chromeTabsExampleShell,
  minWidth: 45,
  maxWidth: 180
})

// Add a new tab
chromeTabs.addNewTab($chromeTabsExampleShell, {
  favicon: "http://g.etfv.co/https://www.hubspot.com",
  title: "HubSpot",
  data: {
    timeAdded: +new Date()
  }
})

// Log tab change data to console
$chromeTabsExampleShell.bind("chromeTabRender", function (){
  var $currentTab = $chromeTabsExampleShell.find(".chrome-tab-current")
  if ($currentTab.length && window["console"] && console.log) {
    console.log("Current tab index", $currentTab.index(), "title", $.trim($currentTab.text()), "data", $currentTab.data("tabData").data)
  }
})
```
