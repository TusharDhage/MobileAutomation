# Double Click Gesture

This gesture performs double click action on the given element/coordinates

- elementId: The id of the element to be clicked. If the element is missing then both click offset coordinates must be provided. If both the element id and offset are provided then the coordinates are parsed as relative offsets from the top left corner of the element.
- x: The x-offset coordinate
- y: The y-offset coordinate

## Different type of usages

```
// Java
((JavascriptExecutor) driver).executeScript("mobile: doubleClickGesture", ImmutableMap.of(
    "elementId", ((RemoteWebElement) element).getId()
));
```
```
Actions action = new Actions(driver);
action.moveTo(element);
action.doubleClick();
action.perform();
```
```
new TouchAction(driver).press(PointOption.point(328, 185)).release().perform().press(PointOption.point(338, 185)).release().perform();
```

