# Click Button Gesture

This gesture performs click action on the given element/coordinates.
Usage of this gesture is recommended as a possible workaround for cases where the "native" tap call fails, even though tap coordinates seem correct.

- elementId: The id of the element to be clicked. If the element is missing then both click offset coordinates must be provided. If both the element id and offset are provided then the coordinates are parsed as relative offsets from the top left corner of the element.
- x: The x-offset coordinate
- y: The y-offset coordinate

## Different types of usages

```
// Java
driver.executeScript("mobile: clickGesture", ImmutableMap.of(
    "elementId", ((RemoteWebElement) element).getId()
));
```
```
TouchAction().press(el0).moveTo(el1).release()
```
```
MobileElement el = driver.findElementByAccessibilityId("SomeId");
el.click();
```
