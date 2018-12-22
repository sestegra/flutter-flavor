# flutter-flavor

Manage your Flutter app flavors.

## Getting started

In order to create a new Flutter project with 'dev' and 'prod' flavors, launch these commands.
```
$ flutter create <output directory> [arguments]
$ cd <output directory>
$ flutter-flavor enable dev prod
```

Then, use ``--flavor`` option with Flutter command.
```
$ flutter build apk --flavor dev
$ flutter build apk --flavor prod
$ flutter build ios --flavor dev
$ flutter build ios --flavor prod
```

## Optional tools

### Launcher icons per platform / per flavor

See pending Pull Request on following project https://github.com/fluttercommunity/flutter_launcher_icons/pull/69

### Assets management per platform / per flavor

In order to support different set of assets depending on platform and flavor parameters, see procedure in following project https://github.com/sestegra/flutter_assets_flavors.

## Usage
```
Manage your Flutter app flavors.

Usage: flutter-flavor <command> [arguments]

Available commands:
  check              Check if flavors have been enabled
  enable [flavors]   Enable flavors and optionaly add flavor(s)
  list               List enabled flavors
  add <flavors>      Add flavors
  remove <flavors>   Remove flavors
  help               Display help information```
```

### check

- Check if flavors have been enabled, exit status is different of 0 if not
```
$ flutter-flavor check
```

### enable

- Enable flavors only
```
$ flutter-flavor enable
```

- Enable flavors and add 'foo' flavor
```
$ flutter-flavor enable foo
```

### list

- List enabled flavor
```
$ flutter-flavor list
```

### add

- Add 'foo' flavor
```
$ flutter-flavor add foo
```

- Add 'foo' and 'bar' flavors
```
$ flutter-flavor add foo bar
```

### remove

- Remove 'foo' flavor
```
$ flutter-flavor remove foo
```

- Remove 'foo' and 'bar' flavors
```
$ flutter-flavor remove foo bar
```

## Limitations

- This project is only a POC (Proof-Of-Concept) to ease flavor management with Flutter app
- Only a Bash script with patch/grep/sed/awk commands
  - Possible improvement could be an implementation in Dart to support all platforms
    - Open question: How to read/write `build.gradle` file in Dart ? (petitparser ?)
    - Open question: How to read/write `project.pbxproj` file in Dart ? (petitparser ?)
- Only tested on macOS
  - Potential issues with sed/awk commands on Linux
- flavors tags are removed from XCode project file when updating it via XCode
  - Possible workaround could be to gate their removal with git-hooks using `flutter-flavor check` command

## References
### Documentation
- Android Plugin DSL Reference
http://google.github.io/android-gradle-dsl/current/index.html

- XCode project
https://developer.apple.com/library/archive/featuredarticles/XcodeConcepts/Concept-Projects.html#//apple_ref/doc/uid/TP40009328-CH5-SW1

### Projects
- A flutter app to show flavors in flutter
https://github.com/iakta/flutter_flavors

- Flutter Launcher Icons
https://github.com/fluttercommunity/flutter_launcher_icons

### Articles
- Separating build environments in Flutter apps
https://iirokrankka.com/2018/03/02/separating-build-environments/

- Flavoring Flutter (Android and iOS)
https://medium.com/@salvatoregiordanoo/flavoring-flutter-392aaa875f36

- Creating flavors of a Flutter app (Android only)
https://cogitas.net/creating-flavors-of-a-flutter-app/
