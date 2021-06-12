#### HLIBS FOR ANDROID ####

![Build Status](https://ci.vnapps.com/buildStatus/icon?job=hlibs&subject=Build:${buildNumber}(${startTime}))
![Build Status](https://ci-backup.vnapps.com/buildStatus/icon?job=hlibs&subject=Backup:${duration}(${startTime}))

Clone project by:
```bash
git submodule add https://github.com/nghuyy/hlibs.git
```
+ Old version 1.0-old is discontinue, you can checkout with tag: 1.0-old,
+ From v1.1.55 we switch to Kotlin language 

add gradle here:

```gradle
		dependencies { 
		implementation fileTree(include: [ '*.aar'], dir: '../hlibs/dist')
			....
```
to dependencies
