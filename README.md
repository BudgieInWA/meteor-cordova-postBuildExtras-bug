# Local plugins break subsequent builds in 1.5.2-beta.11 and 1.6-beta.23

Inside the `meteor` directory:

1. `meteor run android`. The app will build and run.
1. `meteor run android` again. The build will fail with:


	```
	=> Errors executing Cordova commands:         
												  
	   While removing plugins cordova-plugin-meteor-webapp,cordova-plugin-splashscreen,cordova-plugin-statusbar,cordova-plugin-whitelist,cordova-plugin-wkwebview-engine,local-plugin from Cordova project:
	   Cordova error: Plugin "local-plugin" is not present in the project. See `cordova plugin list`.
	   (If the error message contains suggestions for a fix, note that this may not apply to the Meteor integration. You can try running again with the --verbose option to help diagnose the issue.)
	```

## Recreating This Repro

This project was created with

1. `meteor create meteor`
1. `meteor update --release 1.5.2-beta.11` or `meteor update --release 1.6-beta.23`
1. `meteor add-platform andriod`
1. Create the files under `plugin/` as you see them.
1. `meteor add cordova:local-plugin@file://../plugin`
