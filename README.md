LibGDX on Gradle with Swarm connect
===============
## Goal
Make possible to build LibGDX application with Gradle plus Swarmconnect and Scala.

## Description
Repo contains only the build.gradle files, which you can use over build files that LibGDX gdx-setup.jar generated for you. 
But actually you have to compare them when your own files and copy only parts you need.
Because these files also for use with Scala.

## Prerequisites
You already have created LibGDX project with help of 'gdx-setup.jar'

## Usage
1. You've to download a Swarm SDK: http://swarmconnect.com/admin/docs/sdk
2. Put the 'library' folder from downloaded archive to root folder of your project as 'swarmlibrary' folder.
3. Add to project generated 'build.gradle' files recommended parts from this repo.
4. Also proguard config can be added. Its content the same as Swarm web-site recommends.
5. Put 'Swarm.jar' from archive to 'android/libs/'

### More details
1. 'swarmlibrary/build.gradle' can be fully copied from this repo. It is a simplified copy of generated 'android/build.gradle'.
2. The root 'build.gradle' added with:
	```
	project(":swarmlibrary") {
		apply plugin: "android-library"
	}
	```
3. To 'core/build.gradle' add:
	```
	dependencies {
		compile files('../android/libs/Swarm.jar')
	}
	```
4. To 'android/build.gradle' add:
	```
	android {
	...
		compileOptions {
			sourceCompatibility JavaVersion.VERSION_1_7
			targetCompatibility JavaVersion.VERSION_1_7
		}
	...
	}
	
	dependencies {
		compile project(':swarmlibrary')
		compile files('libs/Swarm.jar')
	}
	```
	
### Good luck!