# Oculus-OpenXR-Mobile
Documenting the use of openxr on the oculus mobile platform. 

current-sdk-version: 51 

</br>

Environment Config:
1. Android Studio (JDK, SDK), JDK bin folder is on PATH environment variable;
2. Python is on PATH environment variable;
3. NDK (need r21);

</br>

Descriptions:
1. If you have already downloaded the r21 NDK locally, you can directly modify the 'local.properties' file by adding the path, such as:
```
ndk.dir=F\:\\XXX\\android-ndk-r21e
```
2. Adding projects by modifying 'settings.gradle' file, such as
```
rootProject.projectDir = new File(settingsDir, '.')
rootProject.name = "OculusRoot"

include ':', \
    ':XrSamples:XrCompositor_NativeActivity:Projects:Android', \
	':XrSamples:XrHandsFB:Projects:Android', \
	'XrSamples:XrPassthrough:Projects:Android', \
    ':XrSamples:XrSpaceWarp:Projects:Android', \
    ':XrSamples:XrSpatialAnchor:Projects:Android'

// Top level settings
```
The above code adds 5 projects.

3. Add 'android.debug.keystore' to prevent project from reporting errors when compiling. Also you can generate one yourself with the following command:
```
keytool -genkey -v -keystore android.debug.keystore -storepass android -alias androiddebugkey -keypass android -keyalg RSA -keysize 2048 -validity 10000
```
Attention: You need to execute the above command in the folder where the error was reported, type whatever you want.

4. When the generated project was tested on quest2, it was found that it needed to be opened several times to enter the scene, the reason is unknown. Users need to pay attention to it.

The project file for the test is now successfully generated!

</br>
</br>

Furthermore, The main purpose of this project is to test the 'XR_KHR_composition_layer_equirect2' extension, so I added it to 'Oculus-OpenXR-Mobile/XrSamples/XrCompositor_NativeActivity/Src/XrCompositor_NativeActivity.c' to test the interface. 
If you want to test this, just open the macro command on 'XrCompositor_NativeActivity' line 3820.


</br>

Ref:
1. Oculus OpenXR mobile sdk ([Link](https://developer.oculus.com/downloads/package/oculus-openxr-mobile-sdk/));
2. OpenXR Khronos Group ([Link](https://registry.khronos.org/OpenXR/));
3. Related Video Tutorials ([Link](https://www.youtube.com/watch?v=GJyUvi59hMA&ab_channel=satchelfrost));
