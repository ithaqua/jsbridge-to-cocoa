This project consists in a lightweight api for iPhone to call Objective-C code from Javascript in a UIWebView. A Javascript code is provided, which is able to communicate to an extension of Cocoa's UIWebview. The JSBridge does not use any private api, and has a dependency on [json framework](http://code.google.com/p/json-framework/) for Objective-C.

Download and add to your XCode project the files `JSBridgeWebView.h`, `JSBridgeWebView.m` and `JSBridge.js`. You will also need to add the JSON framework.

# Step-By-Step #
After embedding the code in your project, you need to hook up things. Here, I will try to give a quick step-by-step.

  * Instanciate a new `JSBridgeWebView` and place it in whatever view you want.
  * Implement the `JSBridgeWebViewDelegate`, and the method `- (void)webView:(UIWebView*) webview didReceiveJSNotificationWithDictionary:(NSDictionary*) dictionary`

Now, in your HTML code.

  * Import the `JSBridge.js` file.
  * Create a `JSBridgeObj` instance, like `var obj = new JSBridgeObj();`.
  * Add data to you `JSBridgeObj`, like `obj.addObject("objId", theObject);`. You may add numbers, strings, images and array of objects.
  * Call `obj.sendBridgeObject();`, and the `JSBridgeWebViewDelegate` method will be called with a `NSDictionary` containing `NSString` keys to `NSNumber`, `NSString`, `UIImage` and `NSArray` objects.

For more info, download [this example of XCode project](http://jsbridge-to-cocoa.googlecode.com/files/JSBridge_2010_09_09_v0.01.zip) that uses the JSBridge.