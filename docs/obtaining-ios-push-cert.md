
# Obtaining an Apple Push Certificate

It's not possible to send push notifications to the iOS similator; however sending messages to a physical device requires a push certificate. This guide will walk you through provisioning a certificate that will enable to you to send notifications to a physical device.

## 1 - Provision app identifier

From your [Apple developer portal](https://developer.apple.com).

1. Navigate to _Indentifiers_ page.
2. Click the _Add Indentifier_ button.
3. Select **App IDs** option and continue.
4. Select **App** option and continue.
5. Enter a short description of the app in the _Description_ field.
6. Copy the **Bundle ID** from the Xcode project and paste it into the _Bundle ID_ text field and click _Continue_.
7. Confirm the configuration is correct and click _Register_ button.

## 2 - Create certificate request

Using Keychain Access.

1. From the top menu bar, choose _Keychain Access_ > _Certificate Assistant_ > _Request a Certificate From a Certificate Authority_.
2. Enter the email address and name you want associated with the cert.
3. Choose **Save to disk** option for _Request is_ field.
4. Click continue to create the certificate request.

## 3 - Add push capability to app identifier

From your [Apple developer portal](https://developer.apple.com).

1. Navigate to _Indentifiers_ page.
2. Enable _Push_ in the capabilities list (you don't need to configure it).

## 4 - Create a certificate

From your [Apple developer portal](https://developer.apple.com).

1. Navigate to the _Certificate_ page.
2. Click the _Add Certificate_ button.
3. Choose **Apple Push Notification service SSL (Sandbox & Production)** under _Services_ and click continue.
4. Select the _App ID_ to associate the certificate with and click _Continue_.
5. Upload the certificate request file that was created when you requested a certificate and click continue.
6. Click the _Download_ button to get a local copy of `aps.cer`.

## 5 - Create a private key

From your desktop environment.

1. Open `aps.cer` in Keychain Access.
2. Select **login** under **Default Keychains**.
3. Locate the Apple Push Service certificate.
4. Context-click on the cert and select _Export_.
5. Enter a password to encrypt the key.

## 6 - Configuring OneSignal to push notifications to iOS

From your OneSignal app's settings page.

1. Upload the p12 private key to OneSignal.
2. Enter the password used to encrypt the key.

## Potential issues you may face

A list of potenital issues you may face and how to resolve them.

### New certificate is not trusted

![Invalid certificate](</assets/keychain%20(censored).png>)

The underlying issue seems to be due to some CA expiring at the beginning of 2022 (ref: [Apple Worldwide Developer Relations Intermediate Certificate Expiration](https://developer.apple.com/support/expiration/)). Download the **Worldwide Developer Relations - G4 (Expiring 12/10/2030 00:00:00 UTC)** from the [Apple PKI](https://www.apple.com/certificateauthority/).
