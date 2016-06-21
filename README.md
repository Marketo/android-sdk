# Marketo Mobile SDK for Android 0.6.2

The Marketo Mobile SDK allows integration with Marketo Mobile Engagement (MME).  

Installation instructions and more are [here](http://developers.marketo.com/documentation/mobile/ "Marketo for Mobile").

Change Log

v0.6.0
- InApp Notifications

v0.5.3
- Fixed bug that stop push notification when app was closed

v0.5.2
- Removed depricated android methods to allow building with Proguard

v0.5.1
- Fixed intent.getAction condition

v0.5.0
- New secure access feature
- New app type selection
- Android notificaiton config large icon

## Contributing Code

We accept pull requests! Please raise a merge request.

## Issues

Please contact <developerfeedback@marketo.com> for any issues integrating or using this plugin.

## Marketo Android SDK Installation Guide 

### Prerequisites 
1.  Register an application in Marketo Admin portal, get your application secret key and munchkin id.
2.  Configure Android Push access [learn here](http://docs.marketo.com/display/public/DOCS/Configure+Mobile+App+Android+Push+Access)

### Android SDK Setup
1. Open Android Studio and open the application![file] ( ScreenShots/1.png )
2. once the application is opened in the Android Studio and check all the gradle dependancies are clear ![file]( ScreenShots/2.png)
3. Right click on your project and select #Open Module Settings#![file]( ScreenShots/3.png)
4. Click on the '+' button on the top Left Corner ![file]( ScreenShots/4.png)
5. Select 'Import .JAR/.AAR package' and click 'Next'![file]( ScreenShots/5.png)
6. Now clik on the '...' button and select the location of the .aar file from Marketo Android SDK ![file]( ScreenShots/6.png)
7. You can change the name of the sub project and select finish and select ok ![file]( ScreenShots/7.png)
8. Right click on your project and select #Open Module Settings#![file]( ScreenShots/3.png)
9. Select your project name in the Modules and click on the dependancies tab![file]( ScreenShots/10.png)
10. Click on the '+' button (at the bottom on Mac and at the left right top corner on windows) and select Module dependency ![file]( ScreenShots/11.png)
11. select the name which you gave in step 7 ![file]( ScreenShots/12.png)
12. select ok and let the gradle sync the project and resolve the dependancy![file]( ScreenShots/13.png)
13. once gradle is complete it will show you the following info in Gradle Console![file]( ScreenShots/14.png)


