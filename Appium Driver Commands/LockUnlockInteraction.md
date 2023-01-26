## Lock
- Lock the device
```
driver.lockDevice();
```

## Unlock
- Unlock the device
```
driver.unlockDevice();
```

## Is Device Locked
- Check whether the device is locked or not
```
boolean isLocked = driver.isDeviceLocked();
```

## Rotate
- Rotate the device in three dimensions
```
driver.rotate(new DeviceRotation(10, 10, 10));
```
