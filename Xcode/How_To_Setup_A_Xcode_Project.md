# Notes for Xcode

## How To Setup A Xcode Project

### Using Storyboard

- When setting up your project in Storyboard, make sure you set the **User Interface** as _Storyboard_.

- The **Bundle Identifier** is much like a url for apps.  It's a specific name/space for your app in the appStore.  This name is called a **reverse domain name** (e.g. dev.taylorpatterson.I-Am-Rich) which uses the _Organization Identifier_ (company's web address) to create a unique url for the app on the appStore.  

- For _Language_ choose Swift.

### Xcode Walkthrough

- The landing page, after setting up a project, will land on the _General Tab_ in Xcode.
  - Here you can change the version of the app, what version of iOS you want, device for the app to run on, and device orientation.
  - Generally, this will be pretty basic.  You will do most of your development in the Swift and Storyboad files.
- Xcode is divided up into 4 sections:
  - 1st at the to, the **Status bar** (which look like iTunes).
  - 2nd on the left, **Navigation Bar**
    - The most important sub-directory you will be in is the _Project Navigator_ tab.
    - For development use ViewController.swift file
    - For design use Main.storyboard file
      - You can add objects to the Storyboard by pushing the "+" button at the top of the file
  - 3rd on the right, **Inspector Pane**
    - To develop objects you add to your story board, you will use the inspector pane to design the objects on your app.
  - 4th is the debugger on the bottom.  The debugger will be for swift.

Check out this [map of Xcode](https://cloud.netlifyusercontent.com/assets/344dbf88-fdf9-42bb-adb4-46f01eedd629/debf7a18-1b0a-436b-8a45-50ec780cc4c9/design2xcode03f-large-opt.png)

Check out these [keyboad shortcuts](https://swifteducation.github.io/assets/pdfs/XcodeKeyboardShortcuts.pdf) to increase worktime.

### How ImageView work

- When laying out images or objects on the app, keep in mind the grid of the phone.  The top left corner is where it starts on the screen of the phone as well as the image you put on your screen.  
  - For example: the top left corner of the iPhone is at 0, depending on the size of the phone, the x and y axis will be different.
  - In relation to the grid of the phone, the image, which also starts its point at the top left corner, is positioned using x and y coordinates.
- When thinking about ImageView, think about it like a picture frame.

Use this [guide](https://www.paintcodeapp.com/news/ultimate-guide-to-iphone-resolutions) to find iPhone points and resolutions.

### How To Simulate Your App

- There are two ways to simulate your app with Xcode:
  
1. Use the **Simulator** built into Xcode.  
2. Use your iPhone or iPad to simulate the app with these steps:
   1. Check Xcode and iOs versions match.
   2. Add an Apple developer account.
   3. Sign the app.
   4. Connect physical device.
   5. Trust yourself.
   6. Build and run your app.

