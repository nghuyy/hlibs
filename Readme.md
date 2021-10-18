#### HLIBS FOR ANDROID ####



Clone project by:
```bash
git submodule add https://github.com/nghuyy/hlibs.git
```
+ Old version 1.0-old is discontinue, you can checkout with tag: 1.0-old,
+ From v1.1.55 we switch to Kotlin language 

add gradle here:

```gradle
		 ext.kotlin_version = '1.5.10'
    		dependencies {
			classpath "org.jetbrains.kotlin:kotlin-gradle-plugin:$kotlin_version"
			....
    			
		dependencies { 
			implementation fileTree(include: [ '*.aar'], dir: '../hlibs')
			implementation "androidx.core:core-ktx:1.6.0"
			implementation "org.jetbrains.kotlin:kotlin-stdlib-jdk7:$kotlin_version"
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

Proguard:
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

Some permission on new Android to check application feature and ACRA Debug:
```
    <!-- android 11 -->
    <uses-permission android:name="android.permission.QUERY_ALL_PACKAGES" />
```


```
 Kotlin is new, but not good way to include Android project. Too more libs and more bugs. Not eazy to view code like java.
 Today, im going remove Kotlin from my libs. Bye!
```
