# QuickFDBK

## Release for a specific app

QuickFDBK framework should be released in two versions: one for devices and one for simulators.

1. Obtain the bundle id of the app that will integrate QuickFDBK framework
2. Create a new folder somewhere on your computer and name it QuickFDBK
3. Inside QuickFDBK folder add three new folders called Active, Device and Simulator
4. Open QuickFDBK framework project
5. Go to QuickFDBK - Support Files - Constants - Configs.swift and edit the bundle id - it should be replaced with the bundle id of the app that will integrate QuickFDBK framework
6. Select QuickFDBK scheme and Edit it by changing Run - Build configuration to Release.
7. Select a simulator from the list and build the framework
8. Go to Products folder inside the framework where QuickFDBK.framework has been generated
9. Right click on QuickFDBK.framework and select Show in Finder.
10. Copy QuickFDBK.framework file to Simulator folder that you already created and rename it to QuickFDBK_sim.framework
11. Select Generic iOS Device from the list
12. Go to QuickFDBK target - Build Settings and set Skip Install to NO
13. Archive the framework project from Product-Archive
14. Right click on the archive, select Show in Finder then Show Package Contents and navigate to Products - Library - Frameworks where you should find the QuickFDBK.framework that was generated.
15. Copy QuickFDBK.framework file to Device folder that you already created and rename it to QuickFDBK_device.framework
16. Copy QuickFDBK.framework file also to Active folder but this time do not rename it
17. Reset Skip Install setting to YES
17. Now you have the QuickFDBK folder prepared to be imported in the specific app.
