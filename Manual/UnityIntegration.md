# Integrate Litho into your Unity scene

[![Banner image](../Images/banner.jpg)](#)
_Litho beta release 0.4.0 (19/09/2019)_

## Contents

* [Augmented Reality and Litho Interaction](#augmented-reality-and-litho-interaction)
* [Litho Showcase Scene](#litho-showcase-scene)
* [ARSessionOrigin Object](#arsessionorigin-object)
* [ARCamera Object](#arcamera-object)
* [Litho Object](#litho-object)
* [Litho Event Helper Object](#litho-event-helper-object)
* [Showcase Object](#showcase-object)

---

## Augmented Reality and Litho Interaction

Below is a brief overview of the recommended augmented reality (AR) interaction flow to use with Litho. The AR side of the system is handled by [Unity's AR Foundation](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.0/manual/index.html), which is explained briefly [here](UnityIntegration.md#arsessionorigin_object). The Litho SDK sits within the AR Foundation framework, which allows you to tangibly reach into any AR experiences that you make. The following sections explain the objects that make up the Litho interaction system. The Litho showcase scene provides a smorgasbord of example implementation of the components described below.

---

## Litho Showcase Scene

The easiest way to get started with Litho is to take a look at the Litho showcase scene: it illustrates the different types of interaction that can be achieved using Litho.

* In your Unity project, open this scene by double-clicking on _Assets/Litho/Demo/Scenes/LithoShowcase.unity_ Ensure you have [set up your project](ProjectSetup.md) first.

> _It is highly recommended that you look through the features available in the Litho showcase before getting started with your own project. Future updates and new Litho interactions will be demonstrated in the showcase._

---

## _ARSessionOrigin_ Object

To make Litho work in AR, the project [relies on the AR Foundation package](ProjectSetup.md#install-ar-foundation-and-arkit). This prefab contains the other Litho and AR objects required to make the scene work. A basic overview is given below, but more detail on AR Foundation can be found [here](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.0/manual/index.html). How Litho's interactions work in Unity is covered in more detail [here](UnityScripting.md).

| Description | Inspector |
| :--- | :--- |
| <ol> <li> **[_Transform_](https://docs.unity3d.com/ScriptReference/Transform.html)** represents spatial properties of the AR Session Origin </li> <li> **[_AR Session Origin (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@latest?preview=1&subfolder=/api/UnityEngine.XR.ARFoundation.ARSessionOrigin.html)** handles coordinate information. </li> <li> **[_AR Session (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/api/UnityEngine.XR.ARFoundation.ARSession.html)** handles the AR session information, such as whether to process updates. </li> <li> **[_AR Input Manager (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/api/UnityEngine.XR.ARFoundation.ARInputManager.html)** manages motion input (e.g. camera tracking). </li> <li> **[_AR Plane Manager (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/api/UnityEngine.XR.ARFoundation.ARPlaneManager.html)** handles creation, updates and deletion of GameObjects representing real-world planes. </li> <li> **[_AR Point Cloud Manager (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.2/api/UnityEngine.XR.ARFoundation.ARPointCloudManager.html)** handles detection and tracking of 3D points in a point cloud. </li> <li> **_World Interpereter (Script)_** is essential for Litho to work. It uses AR Foundation to determine where the ground is, then places the [_Floor_ object](#floor-object) (a child of the _ARSessionOrigin_ object) at the correct height. This removes the need to scan the entire room before using the app </li> </ol> | [![AR Session Origin Object](../Images/Editor/ARSessionOriginObject.png)](#)|

---

## _ARCamera_ Object

This represents the real-world (mobile phone) AR camera and makes the Unity scene camera match its position.

| Description | Inspector |
| :--- | :--- |
| <ol> <li> **[_Transform_](https://docs.unity3d.com/ScriptReference/Transform.html)** locates the AR camera in Unity coordinates; values here will be **driven by the _TrackedPoseDriver_ script**. </li> <li> **[_Camera (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@latest?preview=1&subfolder=/api/UnityEngine.XR.ARFoundation.ARSessionOrigin.html)** handles the coordinate information. </li> <li> **[_Tracked Pose Driver (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@2.0/manual/index.html#basic-setup)** keeps this Unity camera aligned with the real-world camera (when the app is [running on a mobile device](BuildInstructions.md)) </li> <li> **[_AR Camera Manager (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@latest?preview=1&subfolder=/api/UnityEngine.XR.ARFoundation.ARCameraManager.html)** Handles camera texture and light estimation. </li> <li> **[_AR Camera Background (Script)_](https://docs.unity3d.com/Packages/com.unity.xr.arfoundation@latest?preview=1&subfolder=/api/UnityEngine.XR.ARFoundation.ARCameraBackground.html)** handles 'passthrough' of the camera video stream to the Unity camera buffer, allowing Unity objects to be rendered in front of real-world objects. </li> </ol> | [![AR Camera Object](../Images/Editor/ARCameraObject.png)](#) |

---

## _Litho_ Object

The _Litho_ object represents your Litho device in the scene ***(Only 1 copy of this object/ script should exist in your scene.)*** The laser pointer is cast from this object, which is automatically positioned relative to the camera. The _Litho_ object prefab can be found in the demo scene and should be a child of the _ARSessionOrigin_ object. When building your own Litho scene, make the _Litho_ prefab a child of the ARSessionOrigin object, and ensure you provide the _Litho_ object with a reference to the main AR camera object in your scene. Further details can be found [here](UnityScripting.md#litho)

| Description | Inspector |
| :--- | :--- |
| <ol> <li> **[_Transform_](https://docs.unity3d.com/ScriptReference/Transform.html)** represents the real-world position of your connected Litho in game world/AR coordinates. **Do not modify this manually or in other scripts** as it is overridden by the _Litho_ script. </li> <li> **_Litho (Script)_** needs a reference to the main AR camera to function (if not set, any object tagged with MainCamera will be used). Code in this script **should not be modified**, as it communicates directly with the Litho Plugin. However, you can set the default Litho _handedness_ and _grip_ here using the Unity Inspector window, and override the defaults whilst in play mode. </li> <li> **_Pointer (Script)_** controls the behaviour of the laser pointer and uses the Unity Line Renderer to visualize it. <ul> <li> **Ignore Layers** lets you select the layers the pointer should ignore </li><li> **Release Range** determines how far a [`Manipulable`](UnityScripting.md#manipulable) may move from where this [`Pointer`](UnityScripting.md#pointer) wants it to be before it is automatically dropped. </li> <li> **Pointer Properties** provides a set of advanced controls for how Litho touches and rotations map to object depth and yaw. </li> </ul> </li> <li> **_Line Renderer_** is a standard Unity component that renders the laser pointer. Modify the properties and materials here to change how the laser pointer looks. </li> <li> **_Game View Controller_** implements the [Litho emulator](../Features/LithoEmulator.md) and explains its controls in the Inspector window. </li> </ol> | [![Litho Object](../Images/Editor/LithoObject.png)](#) |

---

## _Litho Event Helper_ Object

The _Litho Event Helper_ prints Litho global events (and their parameters) to the Unity Console as they happen. This event logging can be toggled on or off using the _Log Global Litho Events_ field.

The _Litho Event Helper_ object is not critical to the Litho system - **you can delete this object** without any issues occurring, or simply disable the _Litho Global Event Logger_ script (uncheck the _Log Global Litho Events_ field) if the logging becomes obtrusive.

The code in the Litho Global Event Logger script can also be viewed as an example of how to access the events exposed by the Litho script - other code samples for Litho events can be found [here](UnityScripting.md#code_samples).

[![Litho Event Helper Object](../Images/Editor/LithoEventHelperObject.png)](#)

---

## _Floor_ Object

The _Floor_ object represents the height of the ground in AR space, which is updated by the _World Interpreter_ script (via the _Ground Plane_ Unity Inspector field). Objects that rest on or interact with the floor should have the _Floor_ object as their parent - this will ensure they don't get occluded (visually or physically) by the _Ground Plane_ object.

---

## _Ground Plane_ Object

The _Ground Plane_ object hosts a large box collider, which is positioned as a child of the _Floor_ object to prevent objects from falling through the floor - this simplifies AR scanning of the floor, as the entire floor becomes physically present after scanning only a small section.

---

## _Showcase_ Object

The Showcase object collates a variety of interaction prefabs into a small platform that is suitable for manipulation in AR. The interaction prefabs serve as examples of how to implement interactions with the Litho [`Pointer`](UnityScripting.md#pointer). The examples can be navigated by using the Litho pointer to click the arrow buttons on the showcase platform. Inspect these these objects in the Unity Hierarchy window to learn more about how to implement different interactions, and look [here](UnityScripting.md#basic-interaction-components) for more details.

| Scene View | Inspector |
| :- | :- |
| [![Scene overview](../Images/Editor/ShowcaseVisual.png)](#) | [![Scene overview](../Images/Editor/ShowcaseObject.png)](#) |

> More information about how these showcase objects work is provided [here](UnityScripting.md#basic-interaction-components).

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
