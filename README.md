# AppIconSplashScreen

1. Go to https://makeappicon.com/ and create icon for android and ios

App Icon

For IOS
Navigate to Xcode, select your project name, and go to the "Image" section. Then, drag all iOS icons onto the "appicon" section. If any warnings appear, remove the problematic icons. Additionally, if the larger iTunes icon is missing, locate it in the icon folder and drag it into the appropriate section. Once completed, restart the app and the app icon should be updated.

For Android
Navigate to "android->app->src->main->res" in your finder and delete all folders except for the "values" and "drawable" folder. Then, paste the downloaded app icon folder into the "res" folder and make sure not add any additonal folders like xml file in v26 folder other it give error while building the app. After restarting the app, the app icon should be updated.

SplashScreen
install
npm i react-native-splash-screen
then go to https://www.appicon.co/ and click on image sets and drag your splash screen annd generate it 

For IOS

Step 1.
To add a splash screen to your Xcode project, first select your project, then go to the "Image" section. Click the "+" icon at the bottom, select "Image Sets," and name the set "splash." Finally, paste the three splash images that you have generated into the newly created "splash" image set.
Step 2.
then select the "LaunchScreen" file. Delete any existing text and images so that only a white screen remains. Then, click on the "+" icon at the top right corner and select "Image View" from the available options. After importing the desired image, right-click on the image view and select "splash" from the dropdown menu to import it successfully. Next, resize the image as desired and position it accordingly. To ensure the splash screen stays centered, click on the second-to-last option, which looks like a triangle. Finally, select the "autoresizing" option and unselect all but the center arrow. This will keep the splash screen centered at all times. After completing these steps, restart the project.
Step 3.
Splashscreen is successfully applied but to customized the timing we need tto change tthe native code in appdelegate.m file
first import #import "RNSplashScreen.h"  then where this line you find 
"return [super application:application didFinishLaunchingWithOptions:launchOptions];"
replace it witth like this
  [super application:application didFinishLaunchingWithOptions:launchOptions];
    [RNSplashScreen show]; 
  return YES;
  
  the mainn doc is not updated for react nattive newwer versionn so we need tto change like that 
  then in app.js paste this code 
  import SplashScreen from 'react-native-splash-screen';
  useEffect(() => {
    setTimeout(() => {
      console.log('splashScreen Code...');
      SplashScreen.hide();
      console.log('splashScreen Code after ...');
    }, 1500);
  });

For Android
Step 1.
Go to "android->app->src->main->res" paste the drawable icon and make sure that inn drawable the name of spalshscreen does not contain '-' or if it contains then simply change the name like splash or splashscreen
Step 2
then in res folder make a folder named layout and in layout make file 'launch_screen.xml' and paste this code 
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">
    <ImageView android:layout_width="match_parent" android:layout_height="match_parent" android:src="@drawable/splash" android:scaleType="centerCrop" />
</RelativeLayout>
change the android:src="@drawable/splash" to android:src="@drawable/your splash screen name"
Step 3.
then go to MainActivity.java file 
import org.devio.rn.splashscreen.SplashScreen; // after facebook library installed or check old app how this import
  SplashScreen.show(this); //add this line
    return "TypescriptProject"; // instead of TypescriptProject this is your app name

if app is now and mainactivity.kt file exist then I am giving you some update
import android.os.Bundle 
import org.devio.rn.splashscreen.SplashScreen 

add this function after this line of code override fun getMainComponentName(): String = "TrueWallet"
override fun onCreate(savedInstanceState: Bundle?) {  // Correctly use Bundle
        SplashScreen.show(this)  // Show the splash screen
        super.onCreate(savedInstanceState)  // Ensure this call is made after showing the splash screen
    }
