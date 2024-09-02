# Marketo Mobile SDK for Android 0.8.13

The Marketo Mobile SDK allows integration with Marketo Mobile Engagement (MME).

# Change Log
v0.8.13 (August 14, 2024)
- Fixed a security issue & Bug fixes.

v0.8.12 (April 25, 2024)
- Enhancements & Bug fixes.

v0.8.11 (Jan 29, 2024)
- Enhancements & Bug fixes.

v0.8.10 (August 29, 2023)
- Enhancements & Bug fixes.

v0.8.9 (June 05, 2023)
- Added parameter to capture the type of framework used for development (native, ionic, phonegap or reactnative)

v0.8.8 (May 25, 2022)
- Added support for Android API Level 31
- Mnimum support Android API Level is now 21

v0.8.4 (Mar 23, 2021)
- Bug fixes

v0.8.2 (Feb 25, 2020)
- Added Android https TLSv1.3 compliance

v0.8.1 (Jul 18, 2019)
- Fixed Bugs

v0.8.0 (Mar 26, 2019)
- Fixed Bugs

v0.7.9 (Mar 04, 2019)
- FCM changes to support custom Marketo Push Notification Receiver
- Configured Push Notification Channel Name.
- Fixed Bugs

v0.7.8 (Dec 10, 2018)
- Added Support for Firebase Cloud Messaging
- Fixed Bugs

v0.7.7 (May 25, 2018)
- Added Support for Android API Level P (28)
- Fixed Bugs

v0.7.6 (January 18, 2018)
- Using Android Activity Lifecycle Callbacks
- Deprecated Marketo.onStart() and Marketo.onStop(), no longer required
- Added support for Android API Levels 26 and 27
- The minimum supported Android API Level is now 14

v0.7.5 (August 15, 2017)
- Fixed bug that crashed app when passing deeplink such as ":" to MarketoActivity

v0.7.3 - v0.7.4 (June 7, 2017)
- Exposed removeDevicePushToken() method
- Notifications are now dismissed from the notification center after tap (Android 4.0)
- Custom large notification icon no longer shows default image (Android 4.0)

v0.7.2 (November 30, 2016)
- Fixed bug when using Priority method in Android versions previous to 5.0
- Default sound in Android is now on when user receives a notification
- Android Push Notification text now wrap to make it more readable
- Migrated from HttpClient to HttpURLConnection

v0.7.1 (November 4, 2016)
- Remove GET_ACCOUNTS permission check
- No longer stacking push notifications
- Catching client protocol exception

v0.7.0 (October 13, 2016)
- Supporting Android Version 7.0

v0.6.4 (August 22, 2016)
- Exposed method [MarketoSDK reportAll] to immediately send events

v0.6.3 (July 15, 2016)
- Bug fixes related to inapp
- added display frequency 'once'

v0.6.0 (June 10, 2016)
- InApp Notifications

v0.5.3
- Fixed bug that stop push notification when app was closed

v0.5.2
- Removed deprecated android methods to allow building with Proguard

v0.5.1
- Fixed intent.getAction condition

v0.5.0
- New secure access feature
- New app type selection
- Android notificaiton config large icon

# Issues

If you encounter issues using or integrating this plugin, please file a support ticket at support.marketo.com

# Marketo Android SDK Installation Guide

## Prerequisites
1.  Register an application in Marketo Admin portal, get your application secret key and munchkin id.
2.  Configure Android Push access [learn here](http://docs.marketo.com/display/public/DOCS/Configure+Mobile+App+Android+Push+Access)

## Android SDK Setup
Include the following URL in your Application gradle file:

    implementation ‘com.marketo:MarketoSDK:0.8.2’


<!-- 3. Click on the '+' button on the top Left Corner ![file]( ScreenShots/4.png)
4. Select 'Import .JAR/.AAR package' and click 'Next'![file]( ScreenShots/5.png)
5. Now clik on the '...' button and select the location of the .aar file from Marketo Android SDK ![file]( ScreenShots/6.png)
6. You can change the name of the sub project and select finish and select ok ![file]( ScreenShots/7.png)
7. Right click on your project and select #Open Module Settings#![file]( ScreenShots/3.png)
8. Select your project name in the Modules and click on the dependancies tab![file]( ScreenShots/10.png)
9. Click on the '+' button (at the bottom on Mac and at the left right top corner on windows) and select Module dependency ![file]( ScreenShots/11.png)
10. select the name which you gave in step 7 ![file]( ScreenShots/12.png)
11. select ok and let the gradle sync the project and resolve the dependancy![file]( ScreenShots/13.png)
12. once gradle is complete it will show you the following info in Gradle Console![file]( ScreenShots/14.png) -->

## (Note) Marekto SDK supports Android API Level 14 and above
## (Troubleshooting) 
If following error occures while building application with marketo sdk v0.7.8 .  
Caused by: org.gradle.api.internal.artifacts.ivyservice.ivyresolve.parser.MetaDataParseException: inconsistent module metadata found. Descriptor: com.marketo:MarketoSDK:0.7.7 Errors: bad version: expected='0.7.8' found='0.7.7'

Follow steps:
1. You can delete all the existing artifacts (artifacts and metadata) Gradle has downloaded using:

For Unix:
```java
rm -rf $HOME/.gradle/caches/
```
For Windows:
```java
rmdir C:\Users\[username]\.gradle\caches\
```
2. Run gradle build (or gradlew build if using gradle wrapper) in the project's root directory. 

## Configure Permissions

- Add following permission inside application tag.

 Open AndroidManifest.xml and add following permissions. Your app must request the “INTERNET” and “ACCESS_NETWORK_STATE” permissions. If your app already requests these permissions, then skip this step.
```java
    <uses‐permission android:name="android.permission.INTERNET"/>
    <uses‐permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
```

Note :-  If the Build vesion is Android P then please Add following Permission 
```java
  <uses-permission android:name="android.permission.FOREGROUND_SERVICE"/>
```


### Android Test Devices

Add Marketo Activity in manifest file inside application tag.
```java
    <activity android:name="com.marketo.MarketoActivity"  android:configChanges="orientation|screenSize" >
        <intent-filter android:label="MarketoActivity" >
            <action  android:name="android.intent.action.VIEW"/>
            <category  android:name="android.intent.category.DEFAULT"/>
            <category  android:name="android.intent.category.BROWSABLE"/>
            <data android:host="add_test_device" android:scheme="mkto" />
        </intent-filter>
    </activity>
```

## SDK Initialization

- Open your Application or Activity class in your app and import the Marketo SDK into your Activity before setContentView or in Application Context.

 ```java
    // Initialize Marketo
    Marketo marketoSdk = Marketo.getInstance(getApplicationContext());
    marketoSdk.initializeSDK("munchkinAccountId","secretKey");
```

## Marketo FCM Push Notification Integration.

 1. Configure Firebase App on Firebase Console.
    - Create/Add a Project on Firebase Console.
       -  In the Firebase console, select Add Project.
        - Select your GCM project from the list of existing Google Cloud projects, and select Add Firebase.
        -  In the Firebase welcome screen, select Add Firebase to your Android App.
        -  Provide your package name and SHA-1, and select Add App. A new google-services.json file for your Firebase app is downloaded.
        -  Select Continue and follow the detailed instructions for adding the Google Services plugin in Android Studio.
    - Navigate to ‘Project Settings’ in Project Overview
        - Click on ‘General’ tab. Download the ‘google-services.json’ file.
        - Click on ‘Cloud Messaging’ tab. Copy ‘Server Key’ & ‘Sender ID’. Provide these ‘Server Key’ & ‘Sender ID’ to Marketo.
    - Configure FCM changes in Android App
        - Switch to the Project view in Android Studio to see your project root directory
        - Move the downloaded ‘google-services.json’ file into your Android app module root directory
        - In Project-level build.gradle add the following:
             ```java
            buildscript {
              dependencies {
                Classpath 'com.google.gms:google-services:4.0.1'
              }
            }
            ```
        - In App-level build.gradle add the following:
             ```java
            dependencies {
              compile 'com.google.firebase:firebase-core:17.3.4'
            }
            // Add to the bottom of the file
            apply plugin: 'com.google.gms.google-services'
            ```
        - Finally, click on “Sync now” in the bar that appears in the ID

 2. Add / Edit FCM Messaging Service
    - If Customer don’t have their own FireBaseMessagingService they need to add MyFirebaseMessagingService.java.

        ```java
        import com.google.firebase.messaging.FirebaseMessagingService;
        import com.google.firebase.messaging.RemoteMessage;
        import com.marketo.Marketo;

        public class MyFirebaseMessagingService extends FirebaseMessagingService {
            public static final String TAG = "MsgFirebaseServ";

            @Override
            public void onNewToken(String token) {
                super.onNewToken(token);
                Marketo marketoSdk = Marketo.getInstance(getApplicationContext());
                marketoSdk.setPushNotificaitonToken(token);
            }

            @Override
            public void onMessageReceived(RemoteMessage remoteMessage) {
                Marketo marketoSdk = Marketo.getInstance(getApplicationContext());
                marketoSdk.showPushNotificaiton(remoteMessage);
            }
        }
        ```

    - If Customer have their own FirebaseMessagingService then they must provide Push notification token once received. They also need to provide RemoteMessage Object once Received.

        ```java
            @Override
            public void onNewToken(String s) {
                super.onNewToken(s);
                Marketo marketoSdk = Marketo.getInstance(getApplicationContext());
                marketoSdk.setPushNotificaitonToken(s);
                // Add your custom logic here...

            }
            @Override
            public void onMessageReceived(RemoteMessage remoteMessage) {
                //check for the data/notification entry from the payload
                Marketo marketoSdk = Marketo.getInstance(getApplicationContext());
                marketoSdk.showPushNotificaiton(remoteMessage);
                // Add your custom logic here...

         }
        ```

 3. Edit your app’s manifest
    - The FCM SDK automatically adds all required permissions as well as the required receiver functionality. Make sure to remove the following obsolete (and potentially harmful, as they may cause message duplication) elements from your app’s manifest.
        ```java
        <permission android:name="<your-package-name>.permission.C2D_MESSAGE" android:protectionLevel="signature"/>
        <uses-permission android:name="<your-package-name>.permission.C2D_MESSAGE" />

        <receiver>
            android:name="com.google.android.gms.gcm.GcmReceiver"
            android:exported="true"
            android:permission="com.google.android.c2dm.permission.SEND">
            <intent-filter>
                <action android:name="com.google.android.c2dm.intent.RECEIVE" />
                <category android:name="<your-package-name>" />
            </intent-filter>
        </receiver>

        <meta-data
            android:name="com.google.android.gms.version"
            android:value="@integer/google_play_services_version" />
        ```

    - Add Following in the AndroidManifest.xml
        ```java
        <service android:name=".MyFirebaseMessagingService">
           <intent-filter>
                <action android:name="com.google.firebase.INSTANCE_ID_EVENT"/>
                <action android:name="com.google.firebase.MESSAGING_EVENT"/>
           </intent-filter>
        </service>
        ```

 4. Initialize Marketo Push
    - After saving the configuration above, you must initialize Marketo Push Notification. Create or open your Application class and copy/paste the code below. You can get your sender ID from the Firebase Console. You need to provide any push notification CHANNEL_NAME which will be shown under App's Notification Settings. (By default CHANNEL_NAME will be 'MKTO')

        ```java
        marketoSdk.initializeMarketoPush(SENDER_ID, CHANNEL_NAME);
        ```

###### The token can also be unregistered when user logs out.

```java
marketoSdk.uninitailizeMarketoPush();
```

###Set Notification Icon (Optional)

To configure a custom notification icon the following method should be called.
```java
    MarketoConfig.Notification config = new MarketoConfig.Notification();
    // Optional bitmap for honeycomb and above
    config.setNotificationLargeIcon(bitmap);
    // Required icon Resource ID
    config.setNotificationSmallIcon(R.id.notification_small_icon);
    // Set the configuration
    Marketo.getInstance(context).setNotificationConfig(config);
    // Get the configuration set
    Marketo.getInstance(context).getNotificationConfig(config);
```

###How to Create User Profile on Android

- Create User Profile

You can create rich profiles by sending user fields as shown below.
```java
    MarketoLead profile = new MarketoLead();
    // Get user profile from network and populate
    try {
        profile.setEmail("htcone3@gmail.com");
        profile.setFirstName("Mike");
        profile.setLastName("Gray");
        profile.setFacebookId("facebookid");
        profile.setAddress("1234 King Fish Blvd");
    }
    catch (MktoException e) {
        e.printStackTrace();
    }
```
- Add more Standard Fields.

```java
    // Add other custom fields
    profile.setCustomField("mobilePhone", "123.456.7890");
    profile.setCustomField("numberOfEmployees", "10");
    profile.setCustomField("phone", "123.456.7890");
    profile.setCustomField("rating", "R");
    profile.setCustomField("facebookDisplayName", "mini");
    profile.setCustomField("facebookReach", "10");
    profile.setCustomField("facebookReferredEnrollments", "100");
    profile.setCustomField("facebookReferredVisits", "9998");
    profile.setCustomField("lastReferredEnrollment", "03/01/2015");
    profile.setCustomField("lastReferredVisit", "03/01/2015");
    profile.setCustomField("linkedInDisplayName", "Android");
```

- Report User Profile
```java
    MarketoLead profile = new MarketoLead();
    // This method will update user profile
    marketoSdk.associateLead(profile);
```

###You can track user interaction by sending custom actions.

- Send custom action.
```java
    Marketo.reportAction("Login", null);
```
- Add custom action meta data.
```java
    MarketoActionMetaData meta = new MarketoActionMetaData();
    meta.setActionType("Shopping");
    meta.setActionDetails("RedShirt");
    meta.setActionLength("20");
    meta.setActionMetric("30");

    Marketo.reportAction("Bought Shirt", meta);
```

### ProGuard Configuration (Optional)
If you are using ProGuard for your app, then add the following lines in your proguard.cfg file. The file will be located within your project folder. Adding this code will exclude the Marketo SDK from the obfuscation process.

```java
    -dontwarn com.marketo.*
    -dontnote com.marketo.*
    -keep class com.marketo.**{ *; }
```

###Advanced Security Access Mode

This setup must be implemented before the Secure Access mode has been enable via the Marketo Admin -> Mobile Apps & Devices page. The following further steps describe the process required to complete the security validation process:

Secure Access mode requires implementing the signature algorithm on the customer server-side that will provide an endpoint to retrieve the access key, calculated signature, expiry timestamp, and email. This algorithm requires the user access key, access secret, email, timestamp, and device id to preform the calculation. The customer is responsible for setting up endpoint, implementing the algorithm to preform signature calculations, and also keep expiration timestamp fresh.[Link Here](http://developers.marketo.com/documentation/mobile/advanced-security-access-mode/)

The Marketo SDK exposes new methods to set and remove the security signature. There is also a utility method to retrieve the device ID. The device ID should be passed along with the email, upon login, to the customer server for use in calculating the security signature. The SDK should the hit new endpoint, pointing to algorithm listed above, to retrieve the necessary fields to instantiate the signature object. Setting this signature in the SDK is a necessary step if the Security Access Mode has been enabled in Marketo Mobile Admin.

```java
      Marketo sdk = Marketo.getInstance(getApplicationContext());
      // set signature
      MarketoConfig.SecureMode secureMode = new MarketoConfig.SecureMode();
      secureMode.setAccessKey(<ACCESS_KEY>);
      secureMode.setEmail(<EMAIL_ADDRESS>);
      secureMode.setSignature(<SIGNATURE_TOKEN>);
      secureMode.setTimestamp(<EXPIRY_DATE>);
      if (secureMode.isValid()) {
        sdk.setSecureSignature(secureMode);
      }
      // remove signature
      sdk.removeSecureSignature();
      // get device id
      sdk.getDeviceId();
```
