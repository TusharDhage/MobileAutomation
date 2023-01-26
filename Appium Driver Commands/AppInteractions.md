## Terminate app
- Terminates an existing app
```
driver.terminateApp("App Package Name");
```

## Install Application
- Test app upgrades Note: Use terminate before installing
```
driver.installApp("/Users/johndoe/path/to/app.apk");
```

## Remove app
- Uninstalls app
```
driver.removeApp("com.example.AppName");
```

## Is app installed?
- Checks if an app is already installed
```
driver.isAppInstalled("com.example.AppName");
```

## Launch app
- Launches existing app. If app is already running, it will be brought to foreground
```
driver.launchApp();
```

## Close app
- Close the app and end driver session
```
driver.closeApp();
```

## Run app is background

- Sends app to background for specified time and then brings back to foreground
```
driver.runAppInBackground(Duration.ofSeconds(10));
```
## Activate app
- Activates an app and moves it to foreground (the app should be already running)
```
driver.activateApp('io.appium.android.apis');
```

## Query app state
- Get app state
- Returns current app state (for e.g. RUNNING IN FOREGROUND)
```
driver.queryAppState('io.appium.android.apis');
```

## Reset app
- Reset the app data
```
driver.resetApp();
```
