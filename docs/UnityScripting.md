# Scripting with Litho

![Banner image](Images/banner1.jpg)
_Litho beta release 0.2.1 (22/07/2019)_

## Contents

* [Augmented reality and interaction overview](#augmented-reality-and-interaction-overview)
* [Litho Events](#litho-events)

---

## Augmented reality and Litho interaction overview

Below is a brief overview of the recommended augmented reality (AR) interaction flow to use with Litho. The AR side of the system is handled by [Unity's AR Foundation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.0/manual/index.html). The Litho SDK sits within the AR Foundation framework, which allows you to tangibly reach into any AR experiences that you make. The lists below highlight the entities that manage the Litho SDK interaction flow; these correspond directly to Unity GameObjects and scripts within the _LithoExample_ Unity scene, included with the SDK.

### AR Foundation

(More detail is available [here](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.0/manual/index.html))

* **_ARSessionOrigin_** contains the _ARCamera_, _Litho_ and _Ground_ objects as children. This AR origin handles conversion between real-world and AR-space coordinates, so Unity objects can be aligned with real-world objects.

    * **[_Transform_](https://docs.unity3d.com/ScriptReference/Transform.html)** locates the AR origin in Unity coordinates.

    * **[_AR Session Origin (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@latest?preview=1&subfolder=/api/UnityEngine.XR.ARFoundation.ARSessionOrigin.html)** handles the coordinate information.

    * **[_AR Session (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/api/UnityEngine.XR.ARFoundation.ARSession.html)** handles the AR session information, such as whether to process updates.

    * **[_AR Input Manager (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/api/UnityEngine.XR.ARFoundation.ARInputManager.html)** manages motion input (e.g. camera tracking).

    * **[_AR Plane Manager (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/api/UnityEngine.XR.ARFoundation.ARPlaneManager.html)** handles creation, updates and deletion of GameObjects representing real-world planes.

    * **[_AR Point Cloud Manager (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/api/UnityEngine.XR.ARFoundation.ARPointCloudManager.html)** handles detection and tracking of 3D points in a point cloud.

    * **_World Interpreter (Script)_** (vital part of the Litho SDK) takes information from the _ARPlaneManager_ to estimate the height of the ground, then moves the referenced _Ground_ object to that height.

* **_ARCamera_** hosts the Unity Camera and AR camera management scripts.

    * **[_Transform_](https://docs.unity3d.com/ScriptReference/Transform.html)** locates the AR camera in Unity coordinates; values here will be **driven by the _TrackedPoseDriver_ script** (see below).

    * **[_Camera (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@latest?preview=1&subfolder=/api/UnityEngine.XR.ARFoundation.ARSessionOrigin.html)** handles the coordinate information.

    * **[_Tracked Pose Driver (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.0/manual/index.html#basic-setup)** keeps this Unity camera aligned with the real-world camera (when the app is running on a mobile device - see [Demo Build Instructions](BuildXcode))

    * **[_AR Camera Manager (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@latest?preview=1&subfolder=/api/UnityEngine.XR.ARFoundation.ARCameraManager.html)** Handles camera texture and light estimation.

    * **[_AR Camera Background (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@latest?preview=1&subfolder=/api/UnityEngine.XR.ARFoundation.ARCameraBackground.html)** handles 'passthrough' of the camera video stream to the Unity camera buffer, allowing Unity objects to be rendered in front of real-world objects.

### Litho SDK

* **_Litho_** is managed entirely by the Litho SDK and should generally not be significantly modified (although changes to the properties exposed in the Unity editor can be useful). This object is explicitly moved through space by the _Litho_ script, and approximates the real-world position of your Litho device relative to the camera.

    * **[_Transform_](https://docs.unity3d.com/ScriptReference/Transform.html)** locates your Litho device in Unity coordinates; values here will be **driven by the _Litho_ script**.

    * **_Litho (Script)_** handles connection to your real-world Litho device, position the _Litho_ object relative to the provided _Camera_ Transform property (_ARCamera_), and processes [events](#litho-events) occurring on your Litho device.

    * **_Pointer (Script)_** manages interactions between Litho and any Unity objects that host the _InteractableObject_ script.

        * _Should Grab On Enter_ (default: _false_) - whether swiping over an object whilst holding the touchpad should pick up that object (default is that an object can only be picked up by first pointing at it, then pressing and holding the touchpad)

        * _Should Apply Force_ (default: _true_) - whether the pointer is able to apply a force to objects

        * _Tension_ (default: _100_) - how much force the pointer applies to objects - this is tuned to the current system to produce a satisfying 'whippy' motion when moving objects

        * _Damping Factor_ (default: _0.25_) - how much damping the pointer applies to objects as it moves them - this is tuned to the current system to produce a satisfying 'whippy' motion when moving objects

        * _Depth Min Distance_ (default: _0.5_) - the shortest distance from the _Litho_ object that an object held by the pointer may be held at

        * _Map Twist To Depth Factor_ - the mapping from wrist twist to object depth when using the [Point grip](UsingLitho#litho-grips)

        * _Map Touch Pos To Yaw_ - the mapping from touchpad touch position (x-axis) to object yaw when using the [Point grip](UsingLitho#litho-grips)

        * _Map Touch Pos To Depth Factor_ - the mapping from touchpad touch position (x-axis) to object depth when using the [Clutch grip](UsingLitho#litho-grips)

        * _Map Twist To Yaw_ - the mapping from wrist twist to object yaw when using the [Clutch grip](UsingLitho#litho-grips)

        * _Touching_ - true if the pointer is aware that a touch is being held on the touchpad

        * _Grabbing_ - true if the pointer is aware that it is holding an object

        * _Current Object_ - the object currently held by the pointer

        * _Start Touch_ / _End Touch_ (Buttons) - used to simulate a touch press/ release for the pointer

    * **_Line Renderer_** renders a visualisation of the pointer, similar to a laser pointer. Modify the material properties of this if you want to change the appearance of the laser.

* **_Ground_** provides a large ground plane for Unity objects to be supported by. Without this, objects created in AR experiences will appear to fall through the real-world ground except in areas that have been explicitly scanned by the AR Foundation camera system.

---

## Litho Events

(If you are unfamiliar with C# events, you can read an overview [here](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/events/index) and get more detail on using events [here](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events)).

Litho events are processed in two categories: 'global' and 'object-specific'.

* **Global events** occur without any context of where the Litho is, what it is doing, or whether it is interacting with an object. Global events are processed and exposed by the _Litho_ script component, attached to the _Litho_ gameobject. They include touch events, which always occur when the Litho user interacts with the Litho touchpad, without reference to any other objects. Connection status and device information events are also global.

    Global events are implemented by the _Litho_ script as [conventional C# events](https://docs.microsoft.com/en-us/dotnet/csharp/programming-guide/events/index).

* **Object-specific events** occur on specific objects as the Litho pointer (managed by the _Pointer_ script) interacts with them. These transmit the information about the Litho touch interactions to the object that is being interacted with. Interactable objects can then use this information to modify their own behaviour based on how the pointer interacts with them.

    Object-specific events are implemented by the _InteractableObject_ script as [UnityEvents](https://docs.unity3d.com/ScriptReference/Events.UnityEvent.html), which work slightly differently, and can additionally be accessed from the Unity Editor Inspector window.

**Note:** Litho touch events may occur globally _and_ locally

An example of subscribing to global Litho events (with code) can be found [here](UnityIntegration#demo-event-object).

#### List of Global Litho Events

##### Litho Connection Status Events:

* **_OnDeviceFound(string deviceName)_** is called when a Litho device is discovered via Bluetooth.

* **_OnConnected(string deviceName)_** is called when a Litho device is connected to via Bluetooth.

* **_OnConnectionFailed(string deviceName)_** is called when an attempt is made to connect to a Litho device via Bluetooth, but it fails.

* **_OnDisconnected(string deviceName)_** is called when a Litho device is disconnected.

##### Litho Device Info Events:

* **_OnBatteryLevelReceived(int batteryLevel)_** is called when the connected Litho device reports its battery level (which occurs on connection and periodically whilst connected).

* **_OnFirmwareVersionReceived(string deviceInfo)_** is called when the connected Litho device reports its firmware version (which occurs on connection and when requested via the _Litho -> Get Info_ menu option in the Unity Editor.

* **_OnHardwareVersionReceived(string deviceInfo)_** is called when the connected Litho device reports its hardware version (which occurs on connection and when requested via the _Litho -> Get Info_ menu option in the Unity Editor).

* **_OnModelNumberReceived(string deviceInfo)_** is called when the connected Litho device reports its model number (which occurs on connection and when requested via the _Litho -> Get Info_ menu option in the Unity Editor).

##### Litho Touch Events:

* **_OnTouchStart([Vector2 position, Vector2 worldPosition](#touch-event-notes))_** is called when the thumb first makes contact with the touchpad (of the connected Litho device).

* **_OnTouchMove([Vector2 position, Vector2 worldPosition](#touch-event-notes))_** is called for every frame between the start and end of a touch (on the connected Litho device), providing updated touch position information.

* **_OnTouchEnd([Vector2 position, Vector2 worldPosition](#touch-event-notes))_** is called when the thumb loses contact with the touchpad (of the connected Litho device).

* **_OnTap([Vector2 position, Vector2 worldPosition](#touch-event-notes))_** is called when the thumb loses contact with the trackpad (of the connected Litho device) a fraction of a second after it initially makes contact.

* **_OnTouchAndHold([Vector2 position, Vector2 worldPosition](#touch-event-notes))_** is called once per frame after the thumb remains on the trackpad and does not move within a fraction of a second of making contact; after that fraction of a second, the thumb may move around whilst still producing the touch-and-hold event.

#### List of Object-Specific Litho Events

* **_OnPointerEnter()_** is called when the pointer starts pointing at the object this script is attached to.

* **_OnPointerExit()_** is called when the pointer stops pointing at the object this script is attached to and has also released this object if it was being held.

* **_OnPointerGrab()_** is called when a touch on the Litho touchpad starts whilst the pointer is pointing at the object this script is attached to.

* **_OnPointerRelease()_** is called when a touch on the Litho touchpad ends whilst the object this script is attached to is being grabbed by the pointer.

#### Touch Event Notes

Litho touch events provide two parameter values for touch positions. It is important to use the correct value in order to provide the same experience to left- and right-handed users. In the future, these positions might remap the touch coordinates to account for different [Litho grips](UsingLitho.md#litho-grips).

* **_position_** - represents the position of the touch **relative to the hand** (i.e. swiping towards the palm will produce the same sequence of values for both left- and right-handed users). Use this value for interactions that are **not spatially-aligned** with the world, such as **scaling objects**.

* **_worldPosition_** - represents the position of the touch **relative to the world** (i.e. swiping from right to left will produce the same sequence of values for both left- and right-handed users). Use this value for interactions that are **spatially-aligned** with the world, such as **scrolling a menu left or right**.

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
