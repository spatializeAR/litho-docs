# Learn how the Litho demo scene works

[![Banner image](../Images/banner.jpg)](#)
_Litho beta release 0.5.1 (02/12/2019)_

## Contents

* [Video Tutorial](#video-tutorial)
* [Instructions for the Litho Showcase Scene](#instructions-for-using-litho-in-the-unity-editor)

---

## Video tutorial

<a href="https://vimeo.com/361262684#t=171s" target="_blank">![Link to video](../Images/Icons/vimeo_small.png)

Watch the setup tutorial on Vimeo</a>

---

## Instructions for using Litho in the Unity Editor

> For more detailed information about the Litho showcase scene, see [here](UnityIntegration.md).

1. **Open the showcase scene** (_/Packages/Litho Beta SDK/Demo/LithoShowcase/LithoShowcase.unity_)

2. **Press _Play_** to run the scene (the _Play_ button should remain depressed and glow blue)

3. **Move your mouse over the Game view** to begin interacting with the scene using the [Litho Emulator](../Features/LithoEmulator.md) - use left-click (and hold) to interact using Litho; use right-click and drag (with W, A, S, D keys) to move the camera around

4. Open the Litho dropdown menu by clicking the hamburger icon in the top-right corner of the Game view - this is where you can connect to Litho on **Mac and mobile devices** only

5. If using Unity on Mac, **wait for your Litho device name to appear** on the list in the Game view. Ensure Bluetooth is enabled on your Mac and that your Litho device is charged - plug it in to charge if unsure. This may take a short while the first time you run the scene

4. In the Game view, **connect to your Litho** device by clicking its corresponding "Connect" button - the button will update to say it is "Connecting..." - wait briefly while the connection is established

5. **Calibrate your Litho** with the Unity editor:

    **Calibrate in game view:**
    1. Swipe through the Litho dropdown menu to the Litho device details tab (look for a picture of a Litho at the top)
    2. Make sure you are wearing Litho in the correct grip (configured by your app on the device details screen; default is [Point grip](UsingLitho.md#litho-grips))
    3. Point in an arbitrary direction (e.g. towards your screen) to use as 'forwards' whilst testing your app
    4. Click the _Calibrate Litho_ button

    **Calibrate using the Unity Menu:**

    [![Calibrate using the LITHO menu](../Images/Editor/CalibrateMenu.png)](#)
    1. Make sure you are wearing Litho in the correct grip (configured by your app; default is [Point grip](UsingLitho.md#litho-grips))
    2. Point in an arbitrary direction (e.g. towards your screen) to use as 'forwards' whilst testing your app
    3. In the Unity Editor menu bar press _LITHO -> Calibrate_

6. You should now be able to **see the laser pointer** protruding from the _Litho_ object, which should be tracking your real-world Litho position and orientation relative to the _ARCamera_ object

7. By **pointing at the cube** in the game world, and **touching and holding the touchpad** on the bottom of your Litho, you should be able to **manipulate the cube** in 3D space. Whilst holding in [Point grip](UsingLitho.md#litho-grips), twist your wrist left and right to move the cube along the axis of the pointer

8. When finished, click the _Play_ button again to **stop the scene** (the _Play_ button should return to its unpressed state)

---

# Navigation

[Home](../README.md)

[Wearing and using Litho (external link)](https://www.litho.cc/pages/using-litho)

[Litho Features](../Features/README.md)

[Set up your Litho project](ProjectSetup.md)

\> [Learn how the Litho demo scene works](DemoScene.md)

[Build your scene for iOS or Android](BuildInstructions.md)

[Integrate Litho into your Unity scene](UnityIntegration.md)

[Code your own Litho scripts](UnityScripting.md)

[Test your scene using the Litho Emulator](../Features/LithoEmulator.md)

[FAQs & Troubleshooting](../FAQ.md)

[Changelog](../Changelog.md)

---
