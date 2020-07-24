OverAppBrowser
==================

Render a webview over your cordova webview (ios and android).

# Important Notice for iOS app developers

This plugin uses `UIWebView` and Apple is not accepting the apps using `UIWebView`. So if you are using this plugin to build an Cordova iOS app, there are two important points to note-

1. If you are developing a new iOS app which is not yet live on AppStore, because of this limitation, your app will never get approved and your build will be rejected as soon you upload it.
2. If you are using this plugin in an exisitng iOS app which was live on AppStore before April 2020, you can use this plugin but Apple will start rejecting your app releases after December 2020.

We had a discussion with the author of the original fork [etabard/Cordova-OverAppBrowser#12](https://github.com/etabard/Cordova-OverAppBrowser/issues/12). He is also no longer maintaining the repository. If you are interested to maintain the fork, you are welcome: 😊

To provide the solution, we have raised a feature request in Cordova's official plugin [apache/cordova-plugin-inappbrowser#668](https://github.com/apache/cordova-plugin-inappbrowser/issues/668). Please upvote and follow that issue so that the Cordova team can implement that feature.

Difference with the original repository
------------

There are few difference/changes as compared to the original version

1. Clearing & closing the WebView after exiting the OverAppBrowser to prevent memory link in Android
2. A method to toggle the hardware back button `toggleHardwareBack`
3. Changed id of the plugin

Installation
------------

To install from **command line**:

    cordova plugin add com.lesfrancschatons.cordova.plugins.overappbrowser


Documentation
-------------

    //function(strUrl, originx, originy, width, height, isAutoFadeIn)
    oab = new OverAppBrowser('http://www.google.fr', 0, 100, 320, 320, true);

    //Events : loadstop, loadstart, exit, loaderror
    oab.addEventListener('loadstop', function(){
        //insert inline style
        oab.insertCSS({code:'#hplogoo {-webkit-transform: rotate(180deg);}'});

        //insert css file
        oab.insertCSS({file:'http://domain.com/style.css'});

        //execute javascript code
        oab.executeScript({code:'window.alert("test");'});

        //insert javascript file
        oab.executeScript({file:'http://domain.com/script.js'});
    });

    //Fade the webview
    oab.fade(toAlpha, duration);

    //Resize the webview
    oab.resize(originx, originy, width, height);

    //Close the webview
    oab.close();


This loads `http://google.fr` over your html app at x=0, y=100, width=320, height=320 and rotates the homepage logo
