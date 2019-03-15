#### HLIBS FOR ANDROID ####

	Clone project into: /app/libs (detect the new update via gitsync)
			
```
		flatDir {
                   dirs 'libs/hlibs'
                }
```
        and:
```
        buildscript {
		    repositories {
		        jcenter()
		        mavenCentral()
		        google()
		    }
		    dependencies {
		        classpath 'com.android.tools.build:gradle:3.3.2'
		    }
		}

		allprojects {
		    repositories {
		        jcenter()
		        maven {url "https://jitpack.io"}
		        google()
		    }
		}
```
		to build.gradle 

		add:
```
			dependencies {
			implementation (name: 'hlibs-release', ext: 'aar')
			ext.toolversion = "28.0.0"
		    implementation "com.android.support:appcompat-v7:$toolversion"
		    implementation "com.android.support:support-v4:$toolversion"
		    implementation "com.android.support:design:$toolversion"
		    implementation "com.android.support:cardview-v7:$toolversion"
		    implementation "com.android.support:recyclerview-v7:$toolversion"
		    implementation "com.android.support:preference-v7:$toolversion"
			....
```
			to dependencies