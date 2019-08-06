# FAQs and Troubleshooting

![Banner image](Images/banner1.jpg)
_Litho beta release 0.3.0 (06/08/2019)_

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

[Why does my Litho feel laggy or jittery in Unity editor or iPhone?](#why-does-my-litho-feels-laggy-or-jittery-in-unity-editor-or-iPhone)

[In a Litho app, my pointer doesn’t feel like it's coming from my hand](#in-a-litho-app-my-pointer-doesnt-feel-like-it-is-coming-from-my-hand)

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

[Why is my Litho's battery life so short (e.g under 3 hours)?](#why-is-my-lithos-battery-life-so-short-eg-under-3-hours)

---

### Interaction

#### Why can't I see the laser pointer?

* Ensure you’re holding the device in the [grip](UsingLitho.md#wearing-litho) you have selected in the UI
* This could be because your Litho is not calibrated, see [here](Documentation/DemoScene.md) for calibration instructions

#### Why is my Litho laser pointer inverted?

* You are probably holding Litho the wrong way around, have a look at how to wear Litho [here](Documentation/UsingLitho.md#wearing-litho)
* Ensure you’re holding the device in the [grip](UsingLitho.md#wearing-litho) you have selected in the UI

[_back to top_](#contents)

#### Why is my pointer drifting to the left or the right over time?

* To resolve this put your Litho on a table while it is still connected, and leave completely still for 30 seconds
* If this does not resolve the issue then download the ‘Litho companion app’ on the App Store
  * Make sure you’re on the latest firmware. If you’re not press the ‘update’ button. If you’re on the latest firmware press the ‘Reset’ Litho button. After updating or resetting the device please leave your Litho stationary on the table for another 30 seconds
* If the problem persists please email our support - support@litho.cc

[_back to top_](#contents)

#### Why does my Litho feels laggy or jittery in Unity editor or iPhone?

* This is most likely a bluetooth signal strength issue. This can be improved by reducing interference by doing things such as:
    * Disconnecting other bluetooth devices such as headphones
    * Disconnecting any USB-C adapters as these can cause bluetooth interference
    * Switching off wifi and handover on mac
    * Making sure your Litho device is close to the computer or phone
    * Restarting your computer or phone
    * Avoiding using Litho in places with many other 2.4ghz devices e.g conferences

[_back to top_](#contents)

#### In a Litho app my pointer doesn’t feel like it is coming from my hand

* Ensure you calibrate your Litho while you’re holding your phone at head height. The Litho must be recalibrate to each individual user
* Ensure the handedness option is matches the hand you’re holding Litho in
* Ensure you have scanned the ground plane before calibrating
* Use your Litho as described as in the using Litho video _(coming soon)_

_(General improvements to the quality of our positional tracking in a wider array of scenarios will be coming in the following months.)_

[_back to top_](#contents)

---

### Connection

#### Why is my Litho not connecting?

* Ensure your Litho is [charged](Documentation/UsingLitho.md#charging-litho)
* Ensure your phone has Bluetooth enabled (check in phone settings)

[_back to top_](#contents)

#### Why is my Litho slow to connect on my phone?

* Disconnect any other bluetooth devices from your phone
* Switch off WiFi on your phone
* Bring your Litho as close to your phone as possible when connecting

[_back to top_](#contents)

#### Why is my Litho not on the device selection screen?

* If the light on the device is on
    * It’s already connected to another app on your phone or connected to your computer. To disconnect, completely close any other Litho apps on the phone and make sure the scence is not running in the Unity Editor. If it is still connecting, try switching off bluetooth on your phone or mac
    * Download the ‘Litho companion app’ on the App Store
        * Make sure you’re on the latest firmware. If not, press the ‘update’ button
        * If you’re on the latest firmware press the ‘Reset’ Litho button
* If the light is off
    * Charge the Litho for at least 60 mins
    * Occasionally the device may take longer to appear on selection screen. Please wait at least 30 seconds
    * Restart your phone or mac
    * Download the ‘Litho companion app’ on the App Store
        * Make sure you’re on the latest firmware. If you’re not press the ‘update’ button.
        *If you’re on the latest firmware press the ‘Reset’ Litho button
    * Email our support - support@litho.cc

[_back to top_](#contents)

#### Why is my Litho slow to connect in the Unity Editor?

* Macs have a buggy bluetooth stack so this connection issue is largely out of our hands. Things that may improve it though are:
    * Disconnecting other bluetooth devices such as headphones
    * Disconnecting any USB-C adapters as these can cause bluetooth interference
    * Switching off wifi and handover on mac
    * Making sure your Litho device is close to the computer or phone
    * Restarting your computer or phone

[_back to top_](#contents)

---

### AR

#### My AR planes are being slow to be discovered or my AR tracking is unreliable

_(Welcome to mobile AR!)_
* We’ve found cleaning your phone camera can make a big improvement to the quality of tracking
    * Other things to try:
        * Make sure you have enough light
        * Avoid reflexive surfaces
        * Move your phone camera slowly
        * AR tracking will not work in a moving vehicle
        * Newer phones generally have substantially better tracking

[_back to top_](#contents)

---

### Development

#### Unity Editor crashes when pressing play

* Make sure you’re using the correct software versions
* If so please report this bug to us at support@litho.cc

[_back to top_](#contents)

#### I have Unity build errors

Please make sure to use the exact versions of software (ARKit, Unity Editor, ARFoundation) specified in the [getting started instructions](ProjectSetup.md). Even small differences in version number can lead to build errors

[_back to top_](#contents)

#### I have Xcode build errors

* If it relates to bitcode please disable it in Xcode by going to your project’s Build Settings in Xcode and search for bitcode, and set it to False
* If it relates to architecture please ensure that you have selected ARM64 architecture in Unity build settings
* If it relates to signing please read [this guide](https://developer.apple.com/support/code-signing/) on getting started with iOS code signing
* If it relates to permissions ensure you have filled in a camera usage description in the project settings in Unity then rebuild your project

[_back to top_](#contents)

---

### Hardware problems

#### Why is my Litho not charging?

* Ensure the cable you are using is plugged into a power outlet fully
* Ensure the cable you are using is plugged into your Litho fully
* Ensure the power outlet is switched on (if using a portable charger, ensure that it has battery remaining)

[_back to top_](#contents)

#### Why is my trackpad or haptic motor behaving erratically?

* Leave your Litho on a non-conductive surface for 30 seconds
* Disconnect and reconnect to the device
* Download the ‘Litho companion app’ on the App Store
    * Make sure you’re on the latest firmware. If you’re not press the ‘update’ button
    * If you’re on the latest firmware press the ‘Reset’ Litho button

[_back to top_](#contents)

#### Why is my Litho's battery life so short (e.g under 3 hours)?

* Make sure to disconnect the device from your phone when not in use. This can be done by completely closing the app using Litho or by switching off your phones bluetooth
* Make sure you’re on the latest firmware
    * Download the ‘Litho companion app’ on the App Store
    * If you’re not already on the latest firmware and press the ‘update’ button

[_back to top_](#contents)

---

### I think I have another hardware issue...

Please email: support@litho.cc and someone from the Team will get back to you asap

---

# Navigation

[Guide to using Litho](UsingLitho.md)

[How to setup your Litho project](ProjectSetup.md)

[Learn how the Litho demo scene works](DemoScene.md)

[Build your scene for iOS using Xcode](BuildXcode.md)

[Integrate Litho into your Unity scene](UnityIntegration.md)

[Best practice for coding your own scripts with Litho](UnityScripting.md)

[FAQs & Troubleshooting](FAQ.md)

[Changelog](Changelog.md)

---
