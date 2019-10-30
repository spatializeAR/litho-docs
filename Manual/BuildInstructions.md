# Build your scene for iOS using Xcode or directly for Android

[![Banner image](../Images/banner.jpg)](#)
_Litho beta release 0.4.4 (30/10/2019)_

## Contents

* [Build your Unity project as an iOS app](#build-your-unity-project-as-an-ios-app)
* [Running the demo scene](#running-the-demo-scene)

---

## Build your Unity project as an iOS or Android app:

> Note: Xcode build for iOS is only available on Mac

1. Open _/Packages/Litho Beta SDK/Demo/Scenes/LithoShowcase.unity_ in the Unity Editor

2. Open Build Settings (_File -> Build Settings..._)

3. Add _LithoExample.unity_ to the 'Scenes In Build' list (click _Add Open Scenes_ in Build Settings, if necessary)

4. Ensure _LithoShowcase_ is the only scene included in the build (only the _LithoShowcase_ checkbox should be ticked)

5. Ensure either _iOS_ or _Android_ platform is selected \- be sure to click _Switch Platforms_ to confirm platform changes

6. Plug your mobile device into your computer

7. **Android only**: Click _Build and Run_ to deploy straight to your device

8. **iOS only**: Click _Build_

9. Choose a name for the build directory (this can be whatever you like; a new name can be chosen each time if you would like to distinguish each build)

10. **iOS only**: Wait for Unity to finish compiling (the build directory will usually open)

11. **iOS only**: From the build directory, open the Xcode project - open _Unity-iPhone.xcworkspace_ (or _Unity-iPhone.xcodeproj_)

12. **iOS only**: Provide a unique bundle identifier to ensure your demo build does not get overwritten by future builds (e.g. _com.yourcompany.lithodemotest1_)

13. **iOS only**: Compile onto your phone with your usual Xcode settings (it should be safe to use Xcode as usual from this point)

---

## Running the demo scene

1. Run the app ensuring that you grant it access to the device camera and location when prompted
2. The built app can be interacted with in a similar manner to how you used the Game view in the Unity Editor, noting the following additional points:

   1. Additional calibration conditions must be adhered to when calibrating
   2. You must scan the ground with your phone camera - you will be instructed onscreen for this until it is sufficiently scanned 
   3. You must scan other key environmental features (e.g. tables, chairs) before you will be able to interact with them

3. If you have created additional scenes, you will need to adapt this build process as appropriate to include them (e.g. add them to _Scenes In Build_ in the Build Settings in addition to or instead of _LithoExample.unity_).
If you have used additional libraries, you may need to modify build settings to account for those

---

# Navigation

[Home](../README.md)

[Litho Features](../Features/README.md)

[Guide to using Litho](UsingLitho.md)

[Set up your Litho project](ProjectSetup.md)

[Learn how the Litho demo scene works](DemoScene.md)

\> [Build your scene for iOS or Android](BuildInstructions.md)

[Integrate Litho into your Unity scene](UnityIntegration.md)

[Code your own Litho scripts](UnityScripting.md)

[Test your scene using the Litho Emulator](../Features/LithoEmulator.md)

[FAQs & Troubleshooting](../FAQ.md)

[Changelog](../Changelog.md)

---
