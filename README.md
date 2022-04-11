# OneSignal Flutter Integreation

This repo contains a sample project integrating the [OneSignal Flutter SDK](https://github.com/OneSignal/OneSignal-Flutter-SDK) into a starter Flutter targeting for Android and iOS.

## Getting Started

There are quite a few moving pieces to get this sample to work due to the nature of Flutter and the platforms it targets.

### Configuring OneSignal

0. [Setup a OneSignal account](https://app.onesignal.com/signup) if you don't already have one.
1. Use the [OneSignal Dashboard](https://app.onesignal.com/apps) to create a new app.
2. Configure the platform you'd like to target...

### Configuring Android

I recommend starting with Android first.

0. [Create a new Firebase project](/docs/setting-up-firebase-project.md)
1. Select your app in the OneSignal dashboard.
2. Enter your Firebase info.
3. Select Flutter as your SDK.

### Configuring iOS

0. [Obtain an Apple push certficate](docs/obtaining-ios-push-cert.md)
1. Select your app in the OneSignal dashboard.
2. Navigate to settings.
3. Find and select iOS in the platform list.
4. Upload your certificate (`*.p12`).
5. Enter the passphrase you encrypted your certificate with.
6. Select Flutter as your SDK.

### Configuring Flutter project

#### Update bundle identifier

Open the project in Android Studio or VS Code.

1. Find all occurrences of, `com.example.onesignal_and_flutter`
2. Replace all occurrences with the unique bunlde identifier you used in setting up iOS.
    * If you're deploying to Android only, replace the `com.example` bit of the identifier with something unique to you.

#### Starting app

1. Install Flutter dependencies, `flutter pub get`
2. Install iOS dependendies. From `ios` directory, `pod install`  (required if targeting iOS)
3. Start the project. From project root, `flutter run`

## Community

OneSignal has a growing [community](https://onesignal.com/onesignal-developers) of excited developers and integrators. You can join us on [Discord](https://discord.gg/aanp5VFp6M) and follow us on [Twitter](https://twitter.com/onesignaldevelopers).

## Beta Program

The [OneSignal Beta Program](https://onesignal.com/beta-program) is a diverse group of users and companies who participate in our feature development process. Beta members help shape the future of OneSignal products by providing feedback, sharing ideas, and testing out new features before they're released.
