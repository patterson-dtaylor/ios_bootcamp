# Third-Party Libraries

- Libraries are other sources to help you complete your code like an animation library that will help you and your app.

## Cocoapods

- Cocoapods is a dependency manager much like npm, but Cocoapods is for Swift and Objective-c.

### Cocoapod Setup:

1. In terminal, navigate to your app directory and set up a Podfile with ```pod init```.
2. Open Podfile with Xcode and edit the file.
   1. Define the global platform - the **lowest** verions iOS you want the app to run on (ex: iOS 9.0 or above). 
3. Delete comments and add the install line from the cocoapod to the Podfile
4. Close Xcode and run ```pod install``` in terminal
5. When finished, **REMEMBER** to only use the .xcworkspace file (it has a white logo).
6. Open your app with the correct file and go for it!

### Cocoapod Potential Problems and How to Update a Cocoapod

- Sometimes cocoapods can become out of date.  It is a good idea to look at the GitHub repo and find what is the latest version of a pod and adjust the global platform of version to meet the requirements for the cocoapod.  Most of the time, it's super easy, but sometimes you need to go through this process. 

### Uninstall Cocoapod

1. Convert everything back to original.
2. Delete cocoapod from Podfile
3. Close Xcode and run ```pod install``` in terminal
4. Reopen Xcode using .xcworkspace file

## Other Dependency Managers

### Carthage

- Updating is a pain.  Don't use it.

### Swift Package Manager
 - You can use this straight from Xcode by going to:
   - file/Swift Packages/ Add Package Dependency...
   - selecting your project
   - and searching for the url