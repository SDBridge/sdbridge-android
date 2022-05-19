# sdbridge-android

TypeScript or javascript mount WebViewJavascriptBridge to window by self.

--------
> `npm install sdbridge-android`

Usage: 
```js
import { addBridgeForAndroidWebView } from 'sdbridge-android';
//@ts-ignore
let bridge = window.WebViewJavascriptBridge;
if (!bridge) {
    console.log("window.WebViewJavascriptBridge 没有挂载成功！！,TS正在尝试挂载");
    console.log("TypeScript正在尝试挂载");
    addBridgeForAndroidWebView();
    //@ts-ignore
    bridge = window.WebViewJavascriptBridge;
    if (bridge){
        console.log("window.WebViewJavascriptBridge, 已经被TypeScript挂载成功！！");
    }
} else {
    console.log("window.WebViewJavascriptBridge 挂载成功！！");
}
```
Why android webView sometimes need TypeScript or javascript mount WebViewJavascriptBridge to window by self ?

Because when you use ```window.WebViewJavascriptBridge``` in android webView,but ```window.WebViewJavascriptBridge``` did not finish loaded!!!

On the other hand iOS WKWebView have ```webView?.configuration.userContentController.addUserScript(...)```
And ```WKUserScriptInjectionTimeAtDocumentStart```
this mean: 
```
WKWebView can inject the script after the document element has been created, but before any other content has been loaded.
```

## License

MIT License (c) 2020

See LICENSE file.
