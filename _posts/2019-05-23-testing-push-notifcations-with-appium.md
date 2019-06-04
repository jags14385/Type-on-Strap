---
layout: post
title: Automating Android Push Notifications Tests with Appium
date: 2019-03-16
---

Lets talk about testing push notifications for Android.

## Why to do this
- To ensure the device registration works fine. This is required to identify which device the notification needs to be pushed.
- Ensure push notifications work for multiple devices for the same user.
- To have confidence that the notifications are received by the device for the given device. Currently, no way to 
  know if the notfication was delivered & received successfully.

## How to do this
- Using Appium
- Tested on a real device
- Making the call to push notification
- Registration of device is tested implicitly i.e. 
  - A successful push notification is only received , if the device registration is succesful. 

## Test Flow 
- Login to a device to register the device implicitly ( because the app does it so ). If you have a different flow , do that to 
  ensure the device registration flow is triggered successfully.
- Make the call to push the notification. Mostly a REST call.
- Swipe the Android Status Bar
- Poll & check for the push notification to have arrived & be present.

## Code

  - Scroll the Notification Menu

  >```java
  new TouchAction(appiumDriver)
                  .press(PointOption.point(0,0))
                  .moveTo(PointOption.point(450, 1750))
                  .release()
                  .perform()
  ```

  - Identify the Push Notification
    This worked because my push notification was the first notification,else list all the notifications & then find the expected notification
  
  >```java
    @AndroidFindBy(id = 'android:id/big_text')
    MobileElement notificationElement
  ```

  - Poll for the element to be displayed & then edtract text for assertion
    Ensure the notification in question is displayed before the getText() call.

  >```java
  assert notificationElement.getText().toContain(<Expected Text>)
  ```

### Resources used for reference
  - [http://appium.io/docs/en/writing-running-appium/touch-actions](http://appium.io/docs/en/writing-running-appium/touch-actions/)
  - [https://stackoverflow.com/questions/51018055/how-to-scroll-up-in-android-appium](https://stackoverflow.com/questions/51018055/how-to-scroll-up-in-android-appium)
  - [https://appiumpro.com/editions/15](https://appiumpro.com/editions/15)