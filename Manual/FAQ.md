# FAQs and Troubleshooting

[![Banner image](../Images/banner.jpg)](#)
_Litho beta release 0.4.2 (16/10/2019)_

## Contents

* [Interaction](#Interaction)
* [Connection](#Connection)
* [AR](#AR)
* [Development](#Development)
* [Hardware](#Hardware)

---

## Interaction

[Why can't I see the laser pointer?](#why-cant-I-see-the-laser-pointer)

[Why is my Litho laser pointer inverted?](#why-is-my-litho-laser-pointer-inverted)

[Why is my pointer drifting to the left or the right over time?](#why-is-my-pointer-drifting-to-the-left-or-the-right-over-time)

[Why does my Litho feel laggy or jittery in the Unity editor or on iPhone?](#why-does-my-litho-feel-laggy-or-jittery-in-the-unity-editor-or-on-iPhone)

[In a Litho app, my pointer doesn’t feel like it's following my hand](#in-a-litho-app-my-pointer-doesnt-feel-like-its-following-my-hand)

---

## Connection

[Why is my Litho not connecting?](#why-is-my-Litho-not-connecting)

[Why is my Litho slow to connect on my phone?](#why-is-my-litho-slow-to-connect-on-my-phone)

[Why is my Litho not on the device selection screen?](#why-is-my-litho-not-on-the-device-selection-screen)

[Why is my Litho slow to connect in the Unity editor?](#why-is-my-litho-slow-to-connect-in-the-unity-editor)

---

## AR

[My AR planes are being slow to be discovered or my AR tracking is unreliable](#my-ar-planes-are-being-slow-to-be-discovered-or-my-ar-tracking-is-unreliable)

---

## Development

[Unity Editor crashes when pressing play](#unity-editor-crashes-when-pressing-play)

[I have Unity build errors](#i-have-unity-build-errors)

[I have Xcode build errors](#i-have-xcode-build-errors)

---

## Hardware

[Why is my Litho not charging?](#why-is-my-Litho-not-charging)

[Why is my trackpad or haptic motor behaving erratically?](#why-is-my-trackpad-or-haptic-motor-behaving-erratically)

[Why is my Litho's battery life so short (e.g. under 3 hours)?](#why-is-my-lithos-battery-life-so-short-eg-under-3-hours)

---

### Interaction

#### Why can't I see the laser pointer?

* Ensure you’re holding the device in the [grip](UsingLitho.md#wearing-litho) you have selected in the UI
* Your Litho might not be calibrated, see the [calibration instructions](DemoScene.md#instructions-for-the-litho-example-scene)

#### Why is my Litho laser pointer inverted?

* You might be holding Litho the wrong way around, have a look at [how to wear Litho](UsingLitho.md#wearing-litho)
* Ensure you’re holding the device in the [grip](UsingLitho.md#wearing-litho) you have selected in the UI

[_back to top_](#contents)

#### Why is my pointer drifting to the left or the right over time?

* To resolve this put your Litho on a table while it is still connected, and leave completely still for 30 seconds
* If this does not resolve the issue then download the _Litho Companion App_ on the App Store
    * Make sure you’re on the latest firmware. If you’re not press the _Update_ button
    * If your Litho has the latest firmware installed press the _Reset Litho_ button
    * After updating or resetting the device, please leave your Litho stationary on a table for another 30 seconds
* If problems persist, please email [support@litho.cc](mailto:support@litho.cc) with details

[_back to top_](#contents)

#### Why does my Litho feel laggy or jittery in the Unity editor or on iPhone?

* This is most likely a Bluetooth signal strength issue. This can be improved by reducing interference by doing things such as:
    * Disconnecting other Bluetooth devices such as headphones
    * Disconnecting any USB-C adapters as these can cause Bluetooth interference
    * Switching off WiFi and Handoff on Mac
    * Making sure your Litho device is close to the computer or phone
    * Restarting your computer or phone
    * Avoiding using Litho in places with many other 2.4GHz devices e.g conferences

[_back to top_](#contents)

#### In a Litho app my pointer doesn’t feel like it's following my hand

* Ensure you calibrate your Litho while you’re holding your phone at head height. The Litho must be recalibrate to each individual user
* Ensure the handedness option (in the menu/ UI) matches the hand you’re holding Litho in
* Ensure you have scanned the ground plane before [calibrating](DemoScene.md#instructions-for-the-litho-example-scene)
* Use your Litho as described in the using Litho video _(coming soon)_

_(General improvements to the quality of our positional tracking in a wider range of scenarios will be released over the following months.)_

[_back to top_](#contents)

---

### Connection

#### Why is my Litho not connecting?

* Ensure your Litho is [charged](Documentation/UsingLitho.md#charging-litho)
* Ensure your phone has Bluetooth enabled (check in phone settings)
* Ensure your phone has permitted the Litho app to access Bluetooth (check in phone app settings)

[_back to top_](#contents)

#### Why is my Litho slow to connect on my phone?

* Disconnect any other Bluetooth devices from your phone
* Switch off WiFi on your phone
* Bring your Litho as close to your phone as possible when connecting

[_back to top_](#contents)

#### Why is my Litho not on the device selection screen?

* If the light on your Litho device is on (pulsing slowly)
    * Your Litho is already connected to another app on your phone or computer. To disconnect, completely close any other Litho apps on the phone and make sure no scenes are running in the Unity Editor. If it is still connected, try switching off Bluetooth on your phone and Mac
    * Download the _Litho Companion App_ from the App Store
        * Make sure you’re on the latest firmware. If not, press the ‘update’ button
        * If you’re on the latest firmware press the ‘Reset’ Litho button
* If the light is off
    * Charge the Litho for at least 60 mins
    * Occasionally the device may take longer to appear on the selection screen. Please wait at least 30 seconds
    * Restart your phone or Mac
    * Download the _Litho Companion App_ on the App Store
        * Make sure you’re on the latest firmware. If you’re not press the _Update_ button.
        * If your Litho has the latest firmware installed press the _Reset Litho_ button.
    * If problems persist, please email [support@litho.cc](mailto:support@litho.cc) with details

[_back to top_](#contents)

#### Why is my Litho slow to connect in the Unity Editor?

* Macs have a buggy Bluetooth stack, so this connection issue is largely out of our hands. However, some suggesetions that may reduce problems are:
    * Use the [Litho emulator](../Features/LithoEmulator.md) for general development - this will mean you don't need to test with Litho hardware as frequently
    * Disconnect other Bluetooth devices such as headphones
    * Disconnect any USB-C adapters, as these can cause Bluetooth interference
    * Switch off WiFi and Handoff on Mac
    * Make sure your Litho device is close to the computer
    * Restart your computer or phone

[_back to top_](#contents)

---

### AR

#### My AR planes are being slow to be discovered or my AR tracking is unreliable

_(Welcome to mobile AR!)_

* Tips for improving AR tracking:
    * Cleaning the lens of your phone camera
    * Make sure your environment is well-lit
    * Avoid pointing your camera at reflective surfaces
    * Move your phone camera slowly (avoid sudden or large movements)
    * Ensure you are in a stationary environment (AR tracking will not work in moving vehicles, elevators, etc.)
* AR Tracking is generally getting better with each new generation of mobile phones, so you may benefit from upgrading your device - refer to your mobile phone retailer for advice on AR suitability of devices

[_back to top_](#contents)

---

### Development

#### Unity Editor crashes when pressing play

* Make sure you’re using the correct software versions (Unity Editor, ARFoundation, ARKit, ARCore) 
* If you are using the correct software versions, please report this bug to [support@litho.cc](mailto:support@litho.cc)

[_back to top_](#contents)

#### I have Unity build errors

* Make sure to use the exact versions of software (Unity Editor, ARFoundation, ARKit, ARCore) specified in the [getting started instructions](ProjectSetupDetailed.md)
* Even small differences in version number can lead to build errors

[_back to top_](#contents)

#### I have Xcode build errors

* If it relates to 'bitcode', please disable bitcode in Xcode by going to your project’s Build Settings in Xcode, searching for bitcode, and setting the corresponding flag to 'False'
* If it relates to architecture, please ensure that you have selected ARM64 architecture in Unity build settings
* If it relates to signing, please read [this guide](https://developer.apple.com/support/code-signing/) on getting started with iOS code signing
* If it relates to permissions, ensure you have [filled in a _Camera Usage Description_ in the Project Settings in Unity](ProjectSetupDetailed.md#3-prepare-your-project), then rebuild your project

[_back to top_](#contents)

---

### Hardware problems

#### Why is my Litho not charging?

* Ensure the cable you are using is fully plugged into a power outlet (check for loose connection)
* Ensure the cable you are using is fully plugged into your Litho (check for loose connection)
* Ensure the power outlet is switched on (if using a portable charger, ensure that it has battery remaining)

[_back to top_](#contents)

#### Why is my trackpad or haptic motor behaving erratically?

* Leave your Litho on a non-conductive surface for 30 seconds
* Disconnect and reconnect to the device
* If you still have issues:
    * Download the _Litho Companion App_ on the App Store
    * Make sure you’re on the latest firmware. If you’re not press the _Update_ button.
    * If your Litho has the latest firmware installed press the _Reset Litho_ button.

[_back to top_](#contents)

#### Why is my Litho's battery life so short (e.g. under 3 hours)?

* Make sure to disconnect the device from your phone when not in use. This can be done by completely closing the app using Litho or by switching off your phones Bluetooth
* If you still have issues, make sure you’re on the latest firmware:
    * Download the _Litho Companion App_ on the App Store
    * Make sure you’re on the latest firmware. If you’re not press the _Update_ button.
    * If your Litho has the latest firmware installed press the _Reset Litho_ button.

[_back to top_](#contents)

---

### I think I have another hardware issue...

Please email support@litho.cc and someone from the Litho team will get back to you soon

---

# Navigation

[Litho Features](../Features/README.md)

[Guide to using Litho](UsingLitho.md)

[Set up your Litho project](ProjectSetup.md)

[Learn how the Litho demo scene works](DemoScene.md)

[Build your scene for iOS or Android](BuildInstructions.md)

[Integrate Litho into your Unity scene](UnityIntegration.md)

[Code your own Litho scripts](UnityScripting.md)

[Test your scene using the Litho Emulator](../Features/LithoEmulator.md)

[FAQs & Troubleshooting](FAQ.md)

[Changelog](../Changelog.md)

---
