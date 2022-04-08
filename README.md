# OneSignal Flutter Integration

This repo contains a sample project integrating the [OneSignal Flutter SDK](https://github.com/OneSignal/OneSignal-Flutter-SDK) into a Flutter mobile app. 

## Getting Started 

There are quite a few moving pieces to get this sample to work due to the nature of Flutter and the platforms it targets. 

0. Make sure you have Flutter, Android, and Android Studio installed and properly setup (i.e. you can already create, run, and deploy Flutter apps). If you're targeting iOS, ensure CocoaPods are installed.
1. ⚠️ Open the project, find all `com.example.onesignal_and_flutter` terms and replace `com.example` with your unique identifier (e.g. `io.android.onesignal_and_flutter`).
2. Configure OneSignal.
3. Setup push for Android.
4. Setup push for iOS.
5. Start the project using `flutter run`. Alternatively, you can use Android Studio to start your project on the device you specify.

## OneSignal

[Setup OneSignal](https://app.onesignal.com/signup) account.

From your [OneSignal Dashboard](https://app.onesignal.com/apps).

### Configuring Android

1. Create a new app.
2. If you're targeting Android and iOS, set up mobile push for Android first; otherwise, select iOS.
3. Enter your Firebase info.
4. Select Flutter as your SDK.

### Configuring iOS

1. Select your app in the dashboard.
2. Navigate to settings.
3. Find and select iOS in the platform list.
4. Upload your certificate (`*.p12`).
5. Enter the passphrase for your certificate.
6. Select Flutter as your SDK.

## Android

### 1 - Add a new project to your [Firebase console](https://console.firebase.google.com/) – for Android push notifications

1. Add project.
2. Navigate to _Project settings_.
3. Select the _Cloud Messaging_ tab.
4. Copy **Server key** and **Sender ID**.

## iOS

It's impossible to send push notifications to the iOS simulator, so you will need to provide a certificate that will enable you to send messages to a physical device.

### 2 - Upload a push certificate to your Apple Developer account

#### 1 - Provision app identifier

From the [Apple developer portal](https://developer.apple.com).

1. Navigate to the _Indentifiers_ page.
2. Click the _Add Indentifier_ button.
3. Select **App IDs** option and continue.
4. Select the **App** option and continue.
5. Enter a short description of the app in the _Description_ field.
6. Copy the **Bundle ID** from the Xcode project, paste it into the _Bundle ID_ text field, and click _Continue_.
7. Confirm the configuration is correct and click the _Register_ button.

#### 2 - Create certificate request

Using Keychain Access.

1. From the top menu bar, choose _Keychain Access_ > _Certificate Assistant_ > _Request a Certificate From a Certificate Authority_.
2. Enter the email address and name you want to be associated with the cert.
3. Choose **Save to disk** option for the _Request is_ field.
4. Click continue to create the certificate request.

#### 3 - Add push capability to app identifier

From your [Apple developer portal](https://developer.apple.com).

1. Navigate to the _Indentifiers_ page.
2. Enable _Push_ in the capabilities list (you don't need to configure it).

#### 4 - Create a certificate

From your [Apple developer portal](https://developer.apple.com).

1. Navigate to the _Certificate_ page.
2. Click the _Add Certificate_ button.
3. Choose **Apple Push Notification service SSL (Sandbox & Production)** under _Services_ and click continue.
4. Select the _App ID_ to associate the certificate with and click _Continue_.
5. Upload the certificate request file.
6. Click the _Download_ button to get a local copy of `aps.cer`.

#### 5 - Create a private key

From your desktop environment.

1. Open `aps.cer` in Keychain Access.
2. Select **login** under **Default Keychains**.
3. Locate the Apple Push Service certificate.
4. Context-click on the cert and select _Export_.
5. Enter a password to encrypt the key.

#### 6 - Configuring OneSignal to push notifications to iOS

From your OneSignal app's settings page.

1. Upload the p12 private key to OneSignal.
2. Enter the password used to encrypt the key.

#### Potential issues you may face

A list of potential issues you may face and how to resolve them.

##### New certificate is not trusted

![Invalid certificate](<assets/keychain%20(censored).png>)

The underlying issue seems to be due to some CA expiring at the beginning of 2022 (ref: [Apple Worldwide Developer Relations Intermediate Certificate Expiration](https://developer.apple.com/support/expiration/)). Download the **Worldwide Developer Relations - G4 (Expiring 12/10/2030 00:00:00 UTC)** from the [Apple PKI](https://www.apple.com/certificateauthority/).
