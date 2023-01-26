# Swipe Element Gesture

This gesture performs swipe gesture on the given element/area.

- elementId: The id of the element to be swiped. If the element id is missing then swipe bounding area must be provided. If both the element id and the swipe bounding area are provided then the area is effectively ignored.
- left: The left coordinate of the swipe bounding area
- top: The top coordinate of the swipe bounding area
- width: The width of the swipe bounding area
- height: The height of the swipe bounding area
- direction: Swipe direction. Mandatory value. Acceptable values are: up, down, left and right (case insensitive)
- percent: The size of the swipe as a percentage of the swipe area size. Valid values must be float numbers in range 0..1, where 1.0 is 100%. Mandatory value.
- speed: The speed at which to perform this gesture in pixels per second. The value must not be negative. The default value is 5000 * displayDensity

## Different types of usages

```
// Java
((JavascriptExecutor) driver).executeScript("mobile: swipeGesture", ImmutableMap.of(
    "left", 100, "top", 100, "width", 200, "height", 200,
    "direction", "left",
    "percent", 0.75
));
```
## Screen Swipe
```
public void swipeScreen(Direction dir) {
    System.out.println("swipeScreen(): dir: '" + dir + "'"); // always log your actions

    // Animation default time:
    //  - Android: 300 ms
    //  - iOS: 200 ms
    // final value depends on your app and could be greater
    final int ANIMATION_TIME = 200; // ms

    final int PRESS_TIME = 200; // ms

    int edgeBorder = 10; // better avoid edges
    PointOption pointOptionStart, pointOptionEnd;

    // init screen variables
    Dimension dims = driver.manage().window().getSize();

    // init start point = center of screen
    pointOptionStart = PointOption.point(dims.width / 2, dims.height / 2);

    switch (dir) {
        case DOWN: // center of footer
            pointOptionEnd = PointOption.point(dims.width / 2, dims.height - edgeBorder);
            break;
        case UP: // center of header
            pointOptionEnd = PointOption.point(dims.width / 2, edgeBorder);
            break;
        case LEFT: // center of left side
            pointOptionEnd = PointOption.point(edgeBorder, dims.height / 2);
            break;
        case RIGHT: // center of right side
            pointOptionEnd = PointOption.point(dims.width - edgeBorder, dims.height / 2);
            break;
        default:
            throw new IllegalArgumentException("swipeScreen(): dir: '" + dir + "' NOT supported");
    }

    // execute swipe using TouchAction
    try {
        new TouchAction(driver)
                .press(pointOptionStart)
                // a bit more reliable when we add small wait
                .waitAction(WaitOptions.waitOptions(Duration.ofMillis(PRESS_TIME)))
                .moveTo(pointOptionEnd)
                .release().perform();
    } catch (Exception e) {
        System.err.println("swipeScreen(): TouchAction FAILED\n" + e.getMessage());
        return;
    }

    // always allow swipe action to complete
    try {
        Thread.sleep(ANIMATION_TIME);
    } catch (InterruptedException e) {
        // ignore
    }
}

public enum Direction {
    UP,
    DOWN,
    LEFT,
    RIGHT;
}
```
## Element Swipe
```
/**
 * Performs swipe inside an element
 *
 * @param el  the element to swipe
 * @param dir the direction of swipe
 * @version java-client: 7.3.0
 **/
public void swipeElementAndroid(MobileElement el, Direction dir) {
    System.out.println("swipeElementAndroid(): dir: '" + dir + "'"); // always log your actions

    // Animation default time:
    //  - Android: 300 ms
    //  - iOS: 200 ms
    // final value depends on your app and could be greater
    final int ANIMATION_TIME = 200; // ms

    final int PRESS_TIME = 200; // ms

    int edgeBorder;
    PointOption pointOptionStart, pointOptionEnd;

    // init screen variables
    Rectangle rect = el.getRect();
    // sometimes it is needed to configure edgeBorders
    // you can also improve borders to have vertical/horizontal
    // or left/right/up/down border variables
    edgeBorder = 0;

    switch (dir) {
        case DOWN: // from up to down
            pointOptionStart = PointOption.point(rect.x + rect.width / 2,
                    rect.y + edgeBorder);
            pointOptionEnd = PointOption.point(rect.x + rect.width / 2,
                    rect.y + rect.height - edgeBorder);
            break;
        case UP: // from down to up
            pointOptionStart = PointOption.point(rect.x + rect.width / 2,
                    rect.y + rect.height - edgeBorder);
            pointOptionEnd = PointOption.point(rect.x + rect.width / 2,
                    rect.y + edgeBorder);
            break;
        case LEFT: // from right to left
            pointOptionStart = PointOption.point(rect.x + rect.width - edgeBorder,
                    rect.y + rect.height / 2);
            pointOptionEnd = PointOption.point(rect.x + edgeBorder,
                    rect.y + rect.height / 2);
            break;
        case RIGHT: // from left to right
            pointOptionStart = PointOption.point(rect.x + edgeBorder,
                    rect.y + rect.height / 2);
            pointOptionEnd = PointOption.point(rect.x + rect.width - edgeBorder,
                    rect.y + rect.height / 2);
            break;
        default:
            throw new IllegalArgumentException("swipeElementAndroid(): dir: '" + dir + "' NOT supported");
    }

    // execute swipe using TouchAction
    try {
        new TouchAction(driver)
                .press(pointOptionStart)
                // a bit more reliable when we add small wait
                .waitAction(WaitOptions.waitOptions(Duration.ofMillis(PRESS_TIME)))
                .moveTo(pointOptionEnd)
                .release().perform();
    } catch (Exception e) {
        System.err.println("swipeElementAndroid(): TouchAction FAILED\n" + e.getMessage());
        return;
    }

    // always allow swipe action to complete
    try {
        Thread.sleep(ANIMATION_TIME);
    } catch (InterruptedException e) {
        // ignore
    }
}

```
