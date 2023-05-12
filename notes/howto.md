# How tos
> This document contains how-to for everything for setting up and running the `dev` version of the package.

### Install `react native` for `android` w/o `android studio`
1. Check for JAVA JRE and JDK. 
    ```sh
    java --version
    javac --version
    ```
2. move to `android-opt` and download command line tools using 
    ```sh
    wget https://dl.google.com/android/repository/commandlinetools-linux-9477386_latest.zip
    ```
3. now unzip and delete the archive. This will create a folder `cmdline-tool`.
4. Move back to project directory.
5. Export `ANDROID_HOME` (for each session).
6. Also make sure you have writing permissions in this directory.
    ```sh
    sudo chown -R $(whoami) $ANDROID_HOME
    ```
7. Export path to adb
    ```sh
    export PATH="${ANDROID_HOME}/platform-tools:${PATH}"
    ```

## Run
1. Export `ANDROID_HOME`.
    ```sh
    export ANDROID_HOME=/workspace/scheduly/android-opt
    ```
2. Enable writing permissions to this path
    ```sh
    sudo chown -R $(whoami) $ANDROID_HOME
    ```
3. Download the  sdkmanager again if it's missing else, just run
    ```sh
    $ANDROID_HOME/cmdline-tools/bin/sdkmanager "platform-tools" "platforms;android-29" "build-tools;29.0.2" "add-ons;addon-google_apis-google-24" --sdk_root=$ANDROID_HOME
    ```
4. Export path to adb
    ```sh
    export PATH="${ANDROID_HOME}/platform-tools:${PATH}"
    ```
5. Now run the project 
    ```sh
    yarn react-native run-android
    ```
6. For connecting android device here's a handy article: https://flutterawesome.com/demonstrate-how-to-easily-program-android-apps-on-gitpod/
    a. First run ngrok to pair, then run again to connect. Navigate to Wireless Debugging->pair device with pairing code. Now tunnel this and pair with adb.
    ```sh
    adb pair *.tcp.*
    adb connect *.tcp.*
    ```
7. Make sure your android never sleeps, otherwise it will return device offline and you need to pair again.
8. Then simply run
    ```sh
    yarn react-native start
    a # for android
    ```