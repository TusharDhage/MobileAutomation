# Long Click Gesture

This gesture performs long click action on the given element/co-ordinates

- singleElementId:- if user provide only element id then it will click on centre of element.
- singleCo-Ordinate:- if user provide only co-ordinate then it will click on selected corner of element.
- elementId: The id of the element to be clicked. If the element is missing then both click offset coordinates must be provided. If both the element id and offset are provided then the coordinates are parsed as relative offsets from the top left corner of the element.
- x: The x-offset coordinate
- y: The y-offset coordinate
- duration: Click duration in milliseconds. 500 by default. The value must not be negative

## Different types of usages

```
// Java
((JavascriptExecutor) driver).executeScript("mobile: longClickGesture", ImmutableMap.of(
    "elementId", ((RemoteWebElement) element).getId()
));
```
```
TouchActions action = new TouchActions(driver);
action.longPress(element);
action.perform();
```
```
WebElement recBtn = driver.findElement(MobileBy.id("img_button"));
new TouchAction((MobileDriver) driver).press(recBtn).waitAction(Duration.ofMillis(10000)).release().perform();
```

## Example

```
 WebElement element = driver.findElement(AppiumBy.id("elementId"));

        driver.executeScript("mobile: longClickGesture", ImmutableMap.of(
          //    "elementId", ((RemoteWebElement) element).getId(),
                "x", 217 ,
                "y", 659,
                "duration", 1000
        ));
```
