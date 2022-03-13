# Android Auto 

Developing for Android Auto is not as straightforward as developing for CarPlay as the package the current solution is based is not well maintained or even working out of the box. [Link to the library](https://github.com/Shopify/react-native-android-auto)

> (Harness App) Right now JS code is still not getting bundled right, therefore only the native code is rendered.

## Running Harness app

To run this app on a desktop head unit first you will need to download an additional SDK in your Android Studio - [Google Docs reference](https://developer.android.com/training/cars/testing). However **DO NOT** switch to the Beta channel as the docs say you should. **The 2.0 rc1 version does not work on Mac OS, so stick with the 1.1 version.**

## Configuring Android Auto on your phone

To test Android Auto implementation you need a device with this application installed. On `Android 10` and up it is already installed by default and it's configuration can be opened in your `Settings -> Android Auto`. This can also be searched for. On `Android 9` and older devices you will need install `Android Auto`. Some countries do have an official support for this, so it can be done through the `PlayStore`, but for example in Lithuania is still not officially supported, so just find an .apk online and install it ([Recommended link for .apk download needed for Android 9 and lower](https://www.apkmonk.com/app/com.google.android.projection.gearhead/)).

Developer mode will have to be enabled on `Android Auto` app to proceed. To do that, you will need to [click multiple times on the version name](https://support.google.com/androidauto/thread/9008705/psa-how-to-enable-developer-mode-in-the-updated-android-auto-app?hl=en) to become a developer and once that is done you need to change App Mode to 'Developer' (this part is missing from documentation, I found it [here](https://stackoverflow.com/a/66375498/12541129) and start a head unit server.

> This is done in Developer Settings, but on Samsung Tablet with Android 10 settings screen was empty for me, so you might also need an Android 9 phone. Although, your experience may vary.

When the server is running on your mobile device you should see a notification in your notifications tray notifying you about this, so before installing the application with rnv make sure it's working. Build and instalation of the app can be done with `yarn android:debug` or you can run regular `rnv run -p android` yourself, what's important is that this is done before running Desktop Head Unit, because it tends to fail to connect if you run it first.

## Running the Desktop Head Unit on your device

Launching the emulator is fairly easy, it can be done with a command in android-auto project - `yarn androidAuto:emulator`

> Note: One part of the command contains `sudo` so you will be prompted to enter your password


## What the `androidAuto:emulator` command does?

First of all you need to link the ports of your device with the port Desktop Head Unit will use. Here we will just be using the default `5277`. To do this manually:

```
adb forward tcp:5277 tcp:5277
```

> If there is a server already running, you reloaded the application or connected/disconnected device you will need to run `adb kill-server` before being able to run the application again (will also need to link port again)

Having installed Desktop Head Unit it is located in `~/Library/Android/sdk/extras/google/auto` on your machine. You will need to access that location and run the command as per Google documentation (Android SDK folder is protected, hence `sudo` is needed here).:

```
sudo ./desktop-head-unit
```
