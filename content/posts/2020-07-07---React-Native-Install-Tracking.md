---
title: React Native Install Tracking
date: "2020-07-07T02:28:57.218Z"
template: "post"
draft: false
slug: "react-native-install-tracking"
category: "REACT-NATIVE"
tags:
  - "react-native"
  - "analytics"
  - "campaign"
  - "firebase"
  - "install tracking"
description: "This article will focus on how to tracking the download sources in a React Native app for both Apple and Google stores."
socialImage: "/media/image-3.jpg"
---

After publishing mobile app to the stores, you may want to run analytic to see different statistics like install & uninstall rates, user behaviours... You also want to run campaigns in order to grow install rate. And when a user installs your app you want to know exactly where your users came from, and which campaign worked best for you.

This article will focus on how to tracking the download sources in a React Native app for both Apple and Google stores.

### Apple

It's quite simple to measure the performance of a campaign in iOS. All you need to do is [generating a campaign link](https://help.apple.com/app-store-connect/#/itcfa7936330) using tool provided by Apple.

![Apple Campaign](/media/ios-campaign.png)

When a user clicks on an ad with that link, they will be redirected to the app's App Store page. If a customer downloads your app for the first time within 24 hours of using your campaign link, you will see this counted as an App Unit.

![Apple Campaign](/media/ios-campaign-sample.png)

Note: To see a campaign, your app needs to be installed by at least **5 individual Apple IDs**.

### Android

#### Option 1: Using Campaign Measurement

Measuring campaigns in Google Analytics enables the attribution of campaigns and traffic sources to user activity within your application.

Refer [here](https://developers.google.com/analytics/devguides/collection/android/v4/campaigns) on how to measure campaigns and traffic sources with the Google Analytics SDK v4 for Android.

**Note**: [Sunsetting the Google Analytics Services SDKs](https://support.google.com/firebase/answer/9167112?hl=en) and it's recommended to move to Option 2.

#### Option 2: Using Firebase with *first_open* event

Automatically collected events are triggered by integrating Firebase Analytics with your app. As long as you use the Firebase SDK, you don't need to write any single line of code to collect these [events](https://support.google.com/firebase/answer/6317485?hl=en). In this case, **first_open** is the event you want to track to know where your users came from.

To integrate Firebase in React Native, I'd recommend to use [rnfirebase](https://rnfirebase.io/). It's quite straightforward to integrate, the [Core](https://rnfirebase.io/) and [Analytics](https://rnfirebase.io/analytics/usage) are required modules to add into your app.

After integrating and publishing app to store, you can test by clicking on a campaign link and then installing the app. You'll see data from your Firebase console or Google Analytics dashboard after a couple hours.

![Android Campaign](/media/android-campaign.png)

You can use [Google Play URL Builder](https://developers.google.com/analytics/devguides/collection/android/v4/campaigns#google-play-url-builder) to create your own campaigns with different parameters.

![Google Play URL Builder](/media/google-play-url-builder.png)