# cordova-plugin-ussdinvoq

A Cordova plugin version of [VoIpUSSD](https://github.com/romellfudi/VoIpUSSD).

## Installation

```shell
cordova plugin add https://github.com/guidoTheNative/cordova-plugin-ussdinvoq.git

## Configuration
On AndroidManifest.xml file

Add the following service:

<service android:name="com.ramymokako.plugin.ussd.android.USSDService" android:permission="android.permission.BIND_ACCESSIBILITY_SERVICE">
    <intent-filter>
        <action android:name="android.accessibilityservice.AccessibilityService" />
    </intent-filter>
    <meta-data android:name="android.accessibilityservice" android:resource="@xml/ussd_service" />
</service>

Also, add the following permissions:

<uses-permission android:name="android.permission.CALL_PHONE" />
<uses-permission android:name="android.permission.SYSTEM_ALERT_WINDOW" />
<uses-permission android:name="android.permission.READ_PHONE_STATE" />

On res/xml/ folder

Create an empty file named ussd_service.xml and insert the following content:

<?xml version="1.0" encoding="utf-8"?>
<accessibility-service xmlns:android="http://schemas.android.com/apk/res/android"
    android:accessibilityEventTypes="typeWindowStateChanged"
    android:packageNames="com.android.phone"
    android:accessibilityFeedbackType="feedbackGeneric"
    android:accessibilityFlags="flagDefault"
    android:canRetrieveWindowContent="true"
    android:notificationTimeout="0"/>

## Usage

window.plugins.voIpUSSD.show('*105#', function (data) {
   console.log('USSD Success: ' + data);
}, function (err) {
   console.log('USSD Error: ' + err);
});
