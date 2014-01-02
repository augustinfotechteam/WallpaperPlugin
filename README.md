# PhoneGap Wallpaper plugin

for Android, by []()	aakash

1. [Description](https://github.com/augustinfotechteam/WallpaperPlugin#1-description)
2. [Installation](https://github.com/augustinfotechteam/WallpaperPlugin#2-installation)
	2. [Automatically (CLI / Plugman)](https://github.com/augustinfotechteam/WallpaperPlugin#automatically-cli--plugman)
	2. [Manually](https://github.com/augustinfotechteam/WallpaperPlugin#manually)
	2. [PhoneGap Build](https://github.com/augustinfotechteam/WallpaperPlugin#phonegap-build)
3. [Usage](https://github.com/augustinfotechteam/WallpaperPlugin#3-usage)

## 1. Description

This plugin is used to set image(local/remote) as wallpaper & save image in internal storage/just store the image.

* Works with PhoneGap >= 3.0.
* Compatible with [Cordova Plugman](https://github.com/apache/cordova-plugman).
* [Officially supported by PhoneGap Build](https://build.phonegap.com/plugins/100).	aakash

### Android specifics
* User can call two function a. wallpaper.setImage (for saving image and set as wallpaper) b. wallpaper.saveImage (just for saving image) and pass parameters as (imagePath, imageTitle, folderName, success, error) where imagePath = local/remote image path, imageTitle = image title you wanna provide, folderName = folder name you want to create on internal storage, success (on success do something…) and error (on error do something…)
* Tested on Android >= 4.

## 2. Installation

### Automatically (CLI / Plugman)
Wallpaper is compatible with [Cordova Plugman](https://github.com/apache/cordova-plugman) and ready for the [PhoneGap 3.0 CLI](http://docs.phonegap.com/en/3.0.0/guide_cli_index.md.html#The%20Command-line%20Interface_add_features), here's how it works with the CLI:

```
$ phonegap local plugin add https://github.com/augustinfotechteam/WallpaperPlugin.git
```
or
```
$ cordova plugin add https://github.com/augustinfotechteam/WallpaperPlugin.git
```
don't forget to run this command afterwards:
```
$ cordova build
```

### Manually

1\. Add the following xml to your `config.xml`:
```xml
<!-- for Android -->
<feature name="Wallpaper">
	<param name="android-package" value="com.purplemad.wallpaper.Wallpaper"/>
</feature>
```

2\. Grab a copy of wallpaper.js, add it to your project and reference it in `index.html`:
```html
<script type="text/javascript" src="wallpaper.js"></script>
```

3\. Download the source files for Android and copy them to your project.

Android: Copy `Wallpaper.java` to `platforms/android/src/com/purplemad/wallpaper` (create the folders)

### PhoneGap Build

Using Wallpaper with PhoneGap Build requires these simple steps:

1\. Add the following xml to your `config.xml` to always use the latest version of this plugin:
```xml
<gap:plugin name="com.purplemad.wallpaper" />
```
or to use this exact version:
```xml
<gap:plugin name="com.purplemad.wallpaper" version="1.0" />
```

2\. Reference the JavaScript code in your `index.html`:
```html
<!-- below <script src="phonegap.js"></script> -->
<script src="js/plugins/Wallpaper.js"></script>
```


## 3. Usage

Basic operations, you'll want to copy-paste this for testing purposes:

```javascript
  // prep some variables
  var imagePath = "www/img/christmas.jpeg";	// Put some image into your assets folder and give its path here.
  var imageTitle = "christmas";			// Set title of your choice.
  var folderName = "PluginImages";		// Set folder Name of your choice. 
  var success = function() { alert("Success"); };	// Do something on success return.
  var error = function(message) { alert("Oopsie! " + message); };	// Do something on error return.

  // For setting wallpaper & saving image
  wallpaper.setImage(imagePath, imageTitle, folderName, success, error);
  
  // For saving image
  wallpaper.saveImage(imagePath, imageTitle, folderName, success, error);	
```