# Android: persist your app data after uninstall

> This was originally posted on cafonsomota.xyz

<figure>
	<p align="center">
		<img src="https://miro.medium.com/max/700/1*MwRkHL4HC4yaFVv5VJzH7g.jpeg" alt="Android features: persist your app data after uninstall cover">
	</p>
</figure>

I’ve recently noticed that an application was asking me if I wanted to keep my app data after uninstalling it.

* What kind of sorcery is this? 🧙‍♂️

I was unaware of this feature, which was introduced in Android 10, and can be useful for some applications.

<figure>
	<p align="center">
		<img src="https://cdn-images-1.medium.com/max/2000/1*CMXNIws5JbdzNlUZsm3B4g.png" alt="User prompt when uninstalling an app with hasFragileUserData attribute set">
	</p>
	<figcaption>User prompt when uninstalling an app with hasFragileUserData attribute set</figcaption>
</figure>

### How to implement

The feature itself is quite straightforward since the OS already takes care of everything. You just need to declare `hasFragileUserData` and set it as `true` on the application section of the **AndroidManifest.**

```xml
<application
  android:allowBackup="true"
  android:icon="@mipmap/ic_launcher"
  android:label="@string/app_name"
  android:roundIcon="@mipmap/ic_launcher_round"
  android:supportsRtl="true"
  android:theme="@style/AppTheme"
  android:hasFragileUserData="true"
    tools:targetApi="q">
  ...
</application>
```

Since this feature is only available on Android 10 and afterward, I’ve also added the `targetApi="q"`.

**Note:** this feature is only available if you uninstall the app from the native settings. If you decide to uninstall from the Google Play Store, there will be no prompt asking if you want to keep the user data or not.

Do you have a better approach? Something didn’t quite work with you? Feel free to send me a [message](https://twitter.com/cafonsomota) 🙂.
