# UVC Camera Android
UVC Camera Android is a library that allows for the use of USB cameras on Android devices. The library was brought over from
the [hthetiot/UVCCamera](https://github.com/hthetiot/UVCCamera/tree/master) repo which is a fork
of [saki4510t/UVCCamera](https://github.com/saki4510t/UVCCamera/tree/master).
The fork was used as it has been updated for later android versions.

### Methodolgy

1. Create the library `libuvccamera` in android project
2. Copy the `libuvccamera/src/main/jni` folder to the `libuvccamera/src/main` folder.
3. Copy the `libuvccamera/src/main/java/com/serenegiant/usb` folder to the `libuvccamera/src/main/java/ai/aloft/core` folder.
4. Added the tasks from the `libuvccamera/build.gradle` to the `libuvccamera/build.gradle`
   and included the `sourceSets`.
5. Added the `libuvccamera` `res` values to the `libuvccamera` `res` folder.
6. Added `com.serenegiant:common` dependency to library `build.gradle`
7. Added generated libs folder dependency to library `build.gradle``
8. Added `saki4510t` maven dependency to `settings.gradle`
9. Ran `./gradlew build` to create the libs folder

### Modifications

Normally to grab the frame data you would need to render it on a surface and then you would be able
to get the frames. The `UVCPreview.cpp` was modified, mostly the `do_capture_callback`, to bypass
the requirement of rendering it on a surface. The gist of changes can be found from
this [closed issue](https://github.com/saki4510t/UVCCamera/issues/596), but there are some
differences between the actual implementation and the issue.
