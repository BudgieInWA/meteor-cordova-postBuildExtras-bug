# Using `ext.postBuildExtras` Breaks Cordova Build

1. `meteor run android` inside `meteor/` and watch the andoid app crash.
1. Delete the contents of `plugin/build-extras.gradle`: `echo > plugin/build-extras.gradle`.
1. `meteor run android` inside `meteor/` again and watch the andoid app run.

Note that resetting the contents of `plugin/build-extras.gradle` will not cause the crash to come
back until you also delete `meteor/.meteor/local/cordova-build`, or at least the
`cdvassets.manifest` file within it.

## Recreating This Repro

This project was created with

1. `meteor create meteor`
1. `meteor add-platform andriod`
1. Create the files under `plugin/` as you see them.
1. `meteor add cordova:breaking-plugin@file://../plugin`
