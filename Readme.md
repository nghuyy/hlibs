#### HLIBS FOR ANDROID ####

![Build Status](https://ci.vnapps.com/buildStatus/icon?job=hlibs&subject=Release&status=1.1.${buildNumber}(${startTime}))
![Build Status](https://ci-backup.vnapps.com/buildStatus/icon?job=hlibs&subject=Backup&status=${duration}(${startTime}))

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

Net class require TLSv1.3. We need include Google Conscrypt Library:
```
implementation 'org.conscrypt:conscrypt-android:2.5.1'

static
 {
     Security.insertProviderAt(Conscrypt.newProvider(), 1);
 }
```

```proguard
-keep class huynguyen.hlibs.** { *; }
-keep class org.conscrypt.** { *; }

# Backward compatibility code.
-dontnote libcore.io.Libcore
-dontnote org.apache.harmony.xnet.provider.jsse.OpenSSLRSAPrivateKey
-dontnote org.apache.harmony.security.utils.AlgNameMapper
-dontnote sun.security.x509.AlgorithmId

-dontwarn android.util.StatsEvent
-dontwarn dalvik.system.BlockGuard
-dontwarn dalvik.system.BlockGuard$Policy
-dontwarn dalvik.system.CloseGuard
-dontwarn com.android.org.conscrypt.AbstractConscryptSocket
-dontwarn com.android.org.conscrypt.ConscryptFileDescriptorSocket
-dontwarn com.android.org.conscrypt.OpenSSLSocketImpl
-dontwarn org.apache.harmony.xnet.provider.jsse.OpenSSLSocketImpl

```
