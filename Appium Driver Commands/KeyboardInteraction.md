## Press Key Code
- Press a particular key on an Android Device
```
driver.pressKeyCode(AndroidKeyCode.SPACE, AndroidKeyMetastate.META_SHIFT_ON);
```

## Long Press Key Code
- Press and hold a particular key code on an Android device
```
driver.longPressKeyCode(AndroidKeyCode.HOME);
```

## Hide Keyboard
- Hide soft keyboard
```
driver.hideKeyboard();
```

## Is Keyboard Shown
- Whether or not the soft keyboard is shown
```
boolean isKeyboardShown = driver.isKeyboardShown();
```
