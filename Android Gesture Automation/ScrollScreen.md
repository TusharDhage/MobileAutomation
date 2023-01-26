# Scroll Gesture

This gesture performs scroll gesture on the given element/area.

- elementId: The id of the element to be scrolled. If the element id is missing then scroll bounding area must be provided. If both the element id and the scroll bounding area are provided then this area is effectively ignored.
- left: The left coordinate of the scroll bounding area
- top: The top coordinate of the scroll bounding area
- width: The width of the scroll bounding area
- height: The height of the scroll bounding area
- direction: Scrolling direction. Mandatory value. Acceptable values are: up, down, left and right (case insensitive)
- percent: The size of the scroll as a percentage of the scrolling area size. Valid values must be float numbers greater than zero, where 1.0 is 100%. Mandatory value.
- speed: The speed at which to perform this gesture in pixels per second. The value must not be negative. The default value is 5000 * displayDensity
## Returned value
The returned value is a boolean one and equals to true if the object can still scroll in the given direction

## Different types of examples
```
// Java
boolean canScrollMore = (Boolean) ((JavascriptExecutor) driver).executeScript("mobile: scrollGesture", ImmutableMap.of(
    "left", 100, "top", 100, "width", 200, "height", 200,
    "direction", "down",
    "percent", 3.0
));
```
```
TouchActions action = new TouchActions(driver);
action.scroll(element, 10, 100);
action.perform();
```
```
public void scrollAndClick(String visibleText) {
     androidDriver.findElementByAndroidUIAutomator("new UiScrollable(new UiSelector().scrollable(true).instance(0)).scrollIntoView(new UiSelector().textContains(\""+visibleText+"\").instance(0))").click();
        }
    }
```
