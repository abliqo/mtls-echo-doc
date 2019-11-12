# About

**Mutual TLS Echo** is a web application that requests [X509](https://en.wikipedia.org/wiki/X.509) client certificate, establishes [mutual TLS](https://en.wikipedia.org/wiki/Mutual_authentication) connection and returns information about the provided client certificate. It is useful for:
* Validating your web browser setup with hardware cryptographic devices that support smart card interface, such as classic smart cards and certain YubiKey devices
* Getting information about client certificates, such as serial number, subject, validity period, public key information, etc
* Programmatically validating client certificates

The service is available at [https://mtls-echo.bliqo.com](https://mtls-echo.bliqo.com)

For programmatic access, a JSON interface is available at [https://mtls-echo.bliqo.com/json](https://mtls-echo.bliqo.com/json)

# Setting Up Browser

In Chrome browser, the experience of specifying client certificate varies depending on the operating system. On macOS and Windows it typically does not require any manual setup. Just plugging in the supported cryptographic device is sufficient. On Linux systems, however, Chrome does not officially support smart card interface.

Firefox browser provides universal user experience on all operating systems that it supports, but requires some preliminary manual setup. To enable Firefox access client certificates on a cryptographic device, complete the following steps:
1. Plug in/insert the cryptographic device to your computer
2. Install [OpenSC software](https://github.com/OpenSC/OpenSC/wiki) for your operating system
3. In Firefox menu, go to *Preferences* > *Privacy & Security*
4. Scroll down to the very bottom and click on *Security Devices* button
5. In the *Device Manager* dialog, click on *Load* button and specify:
    * Set *Module Name* field to a string that describes your device, such as `YubiKey`
    * Set *Module filename* to a path to you OpenSC library appropriate to your operating system.
        * On Ubuntu Linux the path would be `/usr/lib/x86_64-linux-gnu/opensc-pkcs11.so`
        * On macOS the path would be `/Library/OpenSC/lib/opensc-pkcs11.so`
        * On Windows the path would be `C:\Program Files\OpenSC Project\OpenSC\pkcs11\opensc-pkcs11.dll`
    * Click *OK* button
6. In the *Device Manager* dialog, click *Log In* button and enter your PIN, if access to your device is protected by PIN
7. Close the *Device Manager*
8. Open new browser tab and go to [https://mtls-echo.bliqo.com](https://mtls-echo.bliqo.com) to test your device
