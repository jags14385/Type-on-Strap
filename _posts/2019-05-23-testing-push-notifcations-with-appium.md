---
layout: post
title: Automating Android Push Notifications Tests with Appium
date: 2019-03-16
---

Lets talk about testing push notifications for Android.

## Why to do this ??

- To ensure the device registration works fine. This is required to identify which device the notification needs to be pushed.
- Ensure push notifications work for multiple devices for the same user.
- To have confidence that the notifications are received by the device for the given device. Currently, no way to 
  know if the notfication was delivered & received successfully.

## How to do this

- Using Appium
- Making the call to push notification
- Registration of device is tested implicitly i.e. 
  - A successful push notification is only received , if the device registration is succesful. 

## Test Flow 

- Login to a device to register the device implicitly ( because the app does it so ). If you have a different flow , do that to 
  ensure the device registration flow is triggered successfully.
- Make the call to push the notification. Mostly a REST call.
- Scroll the Notification Menu
- Check & poll for the push notification to be present.

## Code

- Scroll the Notification Menu

```
  scroll(0, 0, 450, 1750)
```
- Identify the notification

```
  @AndroidFindBy(id = 'android:id/big_text')
  MobileElement notificationElement
```