# React Native Barcode Scanner

This project was built to test the React Native Barcode scanner.

This project has only been tested in iOS.

In testing, I found that the default RNCamera caused compile problems in iOS, leading me to integrate the expo camera.

As I was not using Expo to create the project, I had to use Expo as an integration.

## Installing the Toolchain

To compile on macos, you must have:
* Xcode and xcode-command-line-tools, to compile brew and iOS project
* Brew, to install nodejs
* nodejs, to compile React Native
* coocapods, to install iOS framework dependencies

**Install Xcode:**

Go to App store and download Xcode. 30Gb required

When done, open the Terminal and type:

```
$ xcocde-select -p
```

**Install [Hebrew](https://brew.sh/):**

Homebrew should complete the xcode-command-line-tools installation.

```console
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
$ brew update
```

**Install [nodejs](https://nodejs.org/), npm, and npx**
```console
$ brew install nodejs
```

**Install [cocoapods](https://cocoapods.org/)**

```console
$ sudo gem install cocoapods
```


## Running

You can run this project by checking out, initializing, and compiling

```console
$ git clone https://github.com/backupbrain/iosreactnativebarcodescanner.git
$ cd iosreactnativebarcodescanner
$ npm install
$ npx pod-install
$ npx react-native run-ios
```

## How this project was created

### 1. Created React Native project

```console
$ npx create-react-native-app -y iosreactnativecamera
$ cd iosreactnativecamera
```

### 2. Install Expo package 

React Native doesn't support expo modules by default, so we must install them.

```console
$ npx install-expo-modules
```

More documentation available in [Installing Expo Modules](https://docs.expo.dev/bare/installing-expo-modules/)

### 3. Install expo-camera and expo-barcode-scanner

These modules talk to the iOS camera and the barcode scanner.

Instructions for integration are available for both [expo-camera](https://github.com/expo/expo/tree/master/packages/expo-camera) and [expo-barcode-scanner](https://github.com/expo/expo/tree/master/packages/expo-barcode-scanner).

```console
$ expo install expo-camera
$ expo install expo-barcode-scanner
```

### 4. Add permissions settings

We wneed to add descriptive text to the "Camera Usage Description" (and it seems the "Microphone Usage Description") for the project. This is done by editing the `ios/iosreactnativecamera/Info.plist` file. Add the following lines inside `plist.dict`:

```xml
  <key>NSCameraUsageDescription</key>
  <string>Allow $(PRODUCT_NAME) to use the camera</string>
  <key>NSMicrophoneUsageDescription</key>
  <string>Allow $(PRODUCT_NAME) to use the microphone</string>
```

### 5. Build code

Since this is a simple app, we will only be editing the `App.js` file.

Importantly, we will be:
1. Importing Camera, BarcodeScanner, and other UI elements
2. Requesting activation of the camera on first run
3. Determining the available width/height ratio of the camera image
4. Building the UI
5. Displaying the barcode when the camera detects a barcode

### 6. Install Cocoapods

```console
$ npx pod-install
```

### 7. Compile

Compile and run. This takes a few minutes.

It is important to note that the iOS Simulator doesn't support a camera.

```console
$ npx react-native run-ios
```

To test the barcode scanning and view the camera on an actual device, you must compile from Xcode by opening the project file and compiling from Xcode:

```
$ open ios/iosreactnativecamera/iosreactnativecamera.xcworkspace &
```
