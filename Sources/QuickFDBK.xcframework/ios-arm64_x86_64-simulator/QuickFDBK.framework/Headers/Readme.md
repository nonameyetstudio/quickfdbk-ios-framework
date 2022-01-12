# QuickFDBK

QuickFDBK is a swift framework for collecting feedback regarding your app features.

## Installation

1. Open Xcode and create a Frameworks group at the same level with Products or Pods files (if you don't have such a folder yet).
2. Right click on Frameworks group - Show in Finder and copy QuickFDBK folder inside Frameworks folder.
3. Drag and drop the QuickFDBK folder from Frameworks folder into Xcode Frameworks group. QuickFDBK folder should contain framework versions for both simulator and device platforms. 
The Active folder will contain the current framework version that is embedded in the app, depending on the selected platform.
4. Select your app target then go to General - Linked frameworks and libraries and remove QuickFDBK_device.framework, QuickFDBK_sim.framework and QuickFDBK.framework from the list.
5. Select your app target then go to General - Embedded binaries and add QuickFDBK.framework from the Active folder.
6. Select your app target then go to Build Phases and tap on + to add a New Run Script Phase. Copy the following script (do not copy the ``` mark):

```# This script selects the current framework based on the selected platform
echo "Copying frameworks for platform: $PLATFORM_NAME"
rm -R "${SRCROOT}/Frameworks/QuickFDBK/Active"
mkdir "${SRCROOT}/Frameworks/QuickFDBK/Active"
if [ "${PLATFORM_NAME}" = "iphonesimulator" ]; then
cp -af "${SRCROOT}/Frameworks/QuickFDBK/Simulator/QuickFDBK_sim.framework" "${SRCROOT}/Frameworks/QuickFDBK/Active/QuickFDBK.framework"
else
cp -af "${SRCROOT}/Frameworks/QuickFDBK/Device/QuickFDBK_device.framework" "${SRCROOT}/Frameworks/QuickFDBK/Active/QuickFDBK.framework"
fi
```
7. Drag the Run script above Compile Sources.
8. Build your project. It should work both for device and simulator.


## Usage

To start a feedback session use the initialize function from QuickFDBK singleton class. 
This function can take as parameter a custom gesture that will be used to trigger the feedback session.
For now, you can choose between a swipe with four fingers or a shake. If no parameter is provided than the default gesture is the shake one.
The initialize function can be called in applicationDidBecomeActive function from AppDelegate.swift file.

```swift
import QuickFDBK

QuickFDBK.shared.initialize()
QuickFDBK.shared.initialize(feedbackGesture: .fourFingers)
QuickFDBK.shared.initialize(feedbackGesture: .shake)
```

