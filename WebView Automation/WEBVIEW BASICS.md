# Automating Hybrid apps and Mobile Browser: Basics

## Native view:

- Developed using native SDKs i.e. Java for Android and Swift for iOS. Native to the OS. Platform specific.

## WebView:

- Developed using HTML, CSS and JavaScript.
- WebView container that uses browser functionality i.e. Chrome for Android and Safari for Android

#### Mobile Browser:

- Safari for iOS, Chrome for Android
- Developed using HTML, CSS and JavaScript

## Inspecting Hybrid App/Mobile Browser elements:

- Appium inspector shows elements natively. In that case, need to define different selectors for Android and IOS
- WebView elements can be inspected using Chrome remote debugger or Safari Web Inspector
- WebView elements are common for both Android and iOS 
- For Android, in order to inspect WebView elements, developer need to set setWebContents DebuggingEnabled to true within the app
- For Android, the default ChromeDriver version in Appium should be compatible with the Chrome browser version on the device
- For iOS, Appium can automate WKWebView and UIWebView elements, but not SafariViewController elements.

## Code Example
```
    Set<String> contextHandles = ((AndroidDriver) driver).getContextHandles();
        for(String contextHandle : contextHandles){
            System.out.println(contextHandle);
        }

        ((AndroidDriver) driver).context("WEBVIEW");
//        ((AndroidDriver) driver).context(contextHandles.toArray()[1].toString());
```
