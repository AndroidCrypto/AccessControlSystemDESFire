# Building an Access Control System based on Mifare DESFire
These are sample apps that are accompanying an article on medium.com about **Building an Access Control System based on Mifare DESFire** (https://medium.com/@androidcrypto/design-an-access-control-system-based-on-mifare-desfire-ev3-nfc-tags-aa4a7142d85d).

In the code section you find 3 folder with pre-compiled Android apps in DEBUG mode:

## Issuing and Maintenance Application

Setting up and maintaining the access rights for card holders

## Door Opener Application

Emulates the behavior of a real door opener unit that reads the tag, verifies the access rights and releases the door by an electrical door opener

## Card Holder Application

Application for the Card Holder informing about the access rights and showing the logfile

## FAQ section

- How is the data secured on the tag ? The security concept of a Mifare DESFire tag is one of the best available. Each read or write access to a file within an application is secured by a key. We could setup the file to be read- or writable without a key by using the magic key number 14 ("0Eh"). All files on the tag do not run this insecure setup, we are using different keys for different tasks: combined read & write access with key number 1, read access using key number 3 and write access is possible using key number 4.
- What algorithm is used for the keys ? The app is using the AES algorithm with 16 bytes key length ("AES-128").
- What communication mode is used for file access ? The complete communication including storage is done in Plain Communication Mode. For a real world application I'm recommending the "Full Encrypted Communication Mode", but for the sake of easy reading I stayed with the Plain mode.
- What keys were used within the app ? I'm using the insecure way of simply using the default keys ("00000000000000000000000000000000h"). In a real world application you have to personalize the keys by your individual ones, but for this task an addition step ("change key") needs to get performed (skipped for simplicity).
- Can I view the data on the tag ? The most easy way is to use the Card Holder Application for this task, but if you are using a Mifare DESFire app (e.g. my "Mifare DESFire Beginner Tutorial App") you are been able to read and write to the Standard Data Files (file numbers 00 to 03) on the tag by using the default AES key. Please note: change of the data on the tag outside the Maintenance App can lead to undesired behavior or crashes, so please do not write to the tag !
- Are there other issues with the tag setup ? Yes, for the sake of simplicity I nether changed ("personalized") the application keys nor I changed the Master Application Key (it is still the "fabric" default DES-key). Another "issue" is to not change the application settings to prevent the listing or deletion of files without authentication with the Application Master Key. 
- Is the source code available ? I'm sorry, but I'm providing the apps as Debug Applications ("APK-files") only.
- Do the apps run on my Android device ? I compiled the apps for **(minimum) Android 6 (SDK 23) up to Android 14 (SDK 34)** using Android Studio Iguana | 2023.2.1 and Open JDK 17.0.9+0–17.0.9b1087.7–11185874 aarch64. Of course - your Android device needs a NFC reader unit to operate.
- Can I use an app to emulate real tags ? Of course, as long as you stay on Android you are beeing able to emulate a real DESFire tag by using Host-based Card Emulation ("HCE"). I have already done this within another project and I can confirm - it is possible to exchange the real Mifare DESFire tag with a HCE emulated one and the Access Control System is still running like a charm.
- What source do you recommend to learn how to work with DESGFire tags ? Well, I recently published a tutorial for this purpose here on medium.com ("Mifare DESFire EV3 - a beginner tutorial (Android Java) using the DESFire for Android tools")[https://medium.com/@androidcrypto/mifare-desfire-ev3-a-beginner-tutorial-android-java-using-the-desfire-for-android-tools-00aaecb8fa93].
- I do have a real Mifare DESFire EV1 / EV2 / EV3 tag - does the applications work with my tag as well ? As my apps are downwards compatible to generation EV1 the apps will work with generations EV2 and EV3 as well.
