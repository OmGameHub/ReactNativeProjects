# React Native installation on MAC

## React Native

[React Native](https://github.com/facebook/react-native) is an open-source framework for building mobile apps using JavaScript and React. It was developed by Facebook and is widely used for developing cross-platform mobile apps for iOS and Android.

## Install Homebrew

Install Homebrew by running the following command in your terminal:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Run these commands in your terminal to add homebrew to your PATH:

```bash
(echo; echo 'eval "$(/opt/homebrew/bin/brew shellenv)"') >> /Users/<username>/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```

restart your terminal and check if brew is installed correctly

```bash
brew --version
```

## Install Nvm & Node Js LTS

[Nvm](https://github.com/nvm-sh/nvm) is a version manager for node js. It allows you to install multiple versions of node js and switch between them easily.

Run the following command in your terminal to install nvm:

```bash
brew install nvm
```

now run the following command to install node js lts version

```bash
nvm install --lts
```

check if node is installed correctly

```bash
node --version
```

## Install Watchman

[Watchman](https://facebook.github.io/watchman/) is a tool by Facebook for watching changes in the filesystem. It is highly recommended you install it for better performance.

Install Watchman by running the following command in your terminal:

```bash
brew install watchman
```

## _IOS Development Environment_

## Install rbenv & ruby

[rbenv](https://github.com/rbenv/rbenv) is a version manager tool for the ruby programming language on Unix-like systems. It is useful for switching between multiple Ruby versions on the same machine and for ensuring that each project you are working on always runs on the correct Ruby version.

Install rbenv by running the following command in your terminal:

```bash
brew install rbenv ruby-build
```

now check the latest stable ruby versions

```bash
rbenv install -l
```

![latest stable ruby versions](./Screenshots/ListLatestStableRubyVersionsScreenshot.png?align="center")

Install the stable ruby version from the list in my case it is 3.2.2

```bash
# rbenv install <version>
rbenv install 3.2.2
```

now set ruby version as global so that it can be used by all projects

```bash
# rbenv global <version>
rbenv global 3.2.2
```

now add rbenv to your PATH so that it can be used by your shell

```bash
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(rbenv init -)"' >> ~/.zshrc
```

check if ruby latest stable version is installed correctly

```bash
ruby --version
```

## Xcode

The easiest way to install [Xcode](https://itunes.apple.com/us/app/xcode/id497799835?mt=12) is via the Mac App Store. Installing Xcode will also install the iOS Simulator and all the necessary tools to build your iOS app.

## _Android Development Environment_

## Java Development Kit (JDK)

Install Open JDK 11 by running the following command in your terminal

```bash
brew install openjdk@11
```

For the system Java wrappers to find this JDK, symlink it with

```bash
sudo ln -sfn /opt/homebrew/opt/openjdk@11/libexec/openjdk.jdk /Library/Java/JavaVirtualMachines/openjdk-11.jdk
```

If you need to have openjdk@11 first in your PATH, run

```bash
echo 'export PATH="/opt/homebrew/opt/openjdk@11/bin:$PATH"' >> ~/.zshrc
```

For compilers to find openjdk@11 you may need to set

```bash
export CPPFLAGS="-I/opt/homebrew/opt/openjdk@11/include"
```

## Setup Android Environment

### Step 1: Android Studio

Run the following command in your terminal to install [Android Studio](https://developer.android.com/studio)

```bash
brew install --cask android-studio
```

### Step 2: Android SDK

Open Android Studio, click on "More Actions" button and select "SDK Manager".

![Android Studio](/Screenshots/AndroidStudioScreenshot.png?align="center")

In the SDK Platforms tab, check the box next to "Show Package Details" in the bottom right corner. Look for and expand the Android 13 (Tiramisu) entry, then make sure the following items are checked:

-   Android SDK Platform 33

-   Intel x86 Atom_64 System Image or Google APIs Intel x86 Atom System Image or (for Apple M1 Silicon) Google APIs ARM 64 v8a System Image

![SDK Platforms Tab](./Screenshots/SdkPlatformScreenshot.png?align="center")

Next select the SDK Tools tab and check the following boxes:

-   Android SDK Build-Tools

-   Android SDK Command-line Tools (latest)

-   Android Emulator

-   Android SDK Platform-Tools

-   Google Play Services

![SDK Tools Tab](./Screenshots/SdkToolsScreenshot.png?align="center")

Finally, click "Apply" to download and install the Android SDK and related build tools.

### Step 3: Configure the ANDROID_HOME environment variable

React Native tools require some environment variables to be set up in order to build apps with native code.

Add the following lines to your ~/.zprofile or ~/.zshrc (if you are using bash, then ~/.bash_profile or ~/.bashrc) config file:

run the following command in your terminal to add Android SDK path to your PATH:

```bash
echo 'export ANDROID_HOME=$HOME/Library/Android/sdk' >> ~/.zshrc
echo 'export PATH=$PATH:$ANDROID_HOME/emulator' >> ~/.zshrc
echo 'export PATH=$PATH:$ANDROID_HOME/platform-tools' >> ~/.zshrc
```

> Please make sure you use the correct Android SDK path. You can find the actual location of the SDK in the Android Studio "More Actions" button -> SDK Manager -> Android SDK -> Android SDK Location.

![Android SDK Location](./Screenshots/AndroidSDKLocation.jpeg?align="center")

check if Android SDK path is set correctly

```bash
echo $ANDROID_HOME
```

## Create a new react native app

> If you previously installed a global react-native-cli package, please remove it as it may cause unexpected issues.
>
> ```bash
> npm uninstall -g react-native-c
> ```

Run the following command in your terminal to create a new React native project

```bash
npx react-native init MyApp
```

## Run react native app

Now go to your project directory and run the following commands in your terminal

```bash
cd MyApp
```

run the following command in your terminal to run your react native app on ios simulator or device

```bash
npm run ios
```

run the following command in your terminal to run your react native app on android simulator or device

```bash
npm run android
```

![run React Native app on android & ios](./Screenshots/RunAppScreenshot.png?align="center")

Finally, It's done. Now you can start developing your react native app.

If I have made a mistake somewhere or missed any important point, do let me know in the comments.

Thanks for reading.
