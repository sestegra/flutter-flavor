# How-to

## Android flavor
### Configuration
- Replace `android:label` value by `@string/app_name` in `android/app/src/main/AndroidManifest.xml`.
- Add `productFlavors` section in `android/app/build.gradle` file.
- Create `lib/main_<target>.dart` target file.
```
android {
    ...
    buildTypes {
        ...
    }

    flavorDimensions "flavor-type"

    productFlavors {
        <flavor> {
            dimension "flavor-type"
            applicationIdSuffix ".<flavor>"
            resValue "string", "app_name", "<flavor>"
        }
    }
}
```

### Icons
- Flavor icons are located in `android/app/src/<flavor>/res`

### Build
- `flutter build apk --flavor <flavor> --target lib/main_<flavor>.dart`

## iOS flavor
### Configuration
- Replace `CFBundleName` value by `$(bundle_name)` in Info.plist
- Open `ios/Runner.xcworkspace` with Xcode
- In Xcode menu, select Product -> Scheme -> New Scheme entry to create new flavor
- Create xcconfig file
    1. Create `ios/Flutter/Release-<flavor>.xcconfig` that contains
       ```
       #include "Release.xcconfig
       #include "<flavor>.xcconfig
       ```
    2. Create `ios/Flutter/Debug-<flavor>.xcconfig`
       ```
       #include "Debug.xcconfig
       #include "<flavor>.xcconfig
       ```
    3. Create `ios/Flutter/<flavor>.xcconfig` that contains
       ```
       bundle_name = <flavor app name>
       ```
- Add xcconfig files into the project
    1. Right-click on "Flutter" group in the project navigator
    2. Select "Add Files to "Runner"..."
    3. Select created files from previous step
- Duplicate configurations for Release and Debug and suffix them with `-<flavor>`
    1. Click on "Runner" in the top of project navigator.
    2. Ensure the Runner PROJECT is selected, not the Runner TARGET.
    3. Click the Editor -> Add Configuration -> Duplicate "Release" Configuration.

### Icons
- Duplicate `ios/Runner/Assets.xcassets/AppIcon.appiconset` directory to `ios/Runner/Assets.xcassets/AppIcon-<flavor>.appiconset/`
- Update `ASSETCATALOG_COMPILER_APPICON_NAME` value to `AppIcon-<flavor>`
in related Release and Debug configurations

### Build
- `flutter build ios --flavor <flavor> --target lib/main_<flavor>.dart`
