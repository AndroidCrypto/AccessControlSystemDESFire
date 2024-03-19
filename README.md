# Building an Access Control System based on Mifare DESFire
These are sample apps that are accompanying an article on medium.com.

In the code section you find 3 folder with pre-compiled apps in DEBUG mode:

## Issuing and Maintenance Application


## Door Opener Application


## Card Holder Application

## FAQ section

- How is the data secured on the tag ? The security concept of a Mifare DESFire tag is one of the best available. Each read or write access to a file within an application is secure by a key. We could setup the to be read- or writable without a key by using the magic key number 14 ("0Eh"). All files on the tag do not run this insecure setup, we are using different keys for different tasks: combined read & write access with key number 1, read access using key number 3 and write access is possible using key number 4.
- What algorithm is used for the keys ? The app is using the AES algorithm with 16 bytes key length ("AES-128").
- What communication mode is used for file access ? The complete communication including storage is done in Plain Communication Mode. For a real world application I'm recommending the "Full Encrypted Communication Mode", but for the sake of easy reading I stayed with the Plain mode.
- What keys were used within the app ? I'm using the insecure way of simply using the default keys ("00000000000000000000000000000000h"). In a real world application you have to personalize the keys by your individual ones, but for this task an addition step ("change key") need to get performed (skipped for simplicity).
- Can I view the data on the tag ? The most easy way is to use the Card Holder Application for this task, but if you are using a Mifare DESFire app (e.g. my "Mifare DESFire Beginner Tutorial App") you are been able to read and write to the Standard Data Files (file numbers 00 to 03) on the tag by using the default AES key. Please note: change of the data on the tag outside the Maintenance App can lead to undesired behavior or crashes, so please do not write to the tag !
- Are there other issues with the tag setup ? Yes, for the sake of simplicity I nether changed ("personalized") the application keys nor I changed the Master Application Key (it is still the "fabric" default DES-key). Another "issue" is to not change the application settings to prevent the listing or deletion of files without authentication with the Application Master Key. 
- Is the source code available ? I'm sorry, but I'm providing the apps as Debug Applications ("APK-files") only.
- Do the apps run on my Android device ? I compiled the apps for (minimum) Android 6 (SDK 23) up to Android 14 (SDK 34) using Android Studio Iguana | 2023.2.1 and Open JDK 17.0.9+0–17.0.9b1087.7–11185874 aarch64. Of course - your Android device needs a NFC reader unit to operate.
- Can I use an app to emulate real tags ? Of course, as long as you stay on Android you are beeing able to emulate a real DESFire tag by using Host-based Card Emulation ("HCE"). I have already done this within another project and I can confirm - it is possible to exchange the real Mifare DESFire tag with a HCE emulated one and the Access Control System is still running like a charm.
- What source do you recommend to learn how to work with DESGFire tags ? Well, I recently published a tutorial for this purpose here on medium.com ("Mifare DESFire EV3 - a beginner tutorial (Android Java) using the DESFire for Android tools").

