# Google

How To Use Google Login

## Common

> don't forget [Google Api console setting](https://console.cloud.google.com/)

> also default setting look [Android](https://developers.google.com/identity/android-credential-manager) | [IOS](https://developers.google.com/identity/sign-in/ios/start-integrating)

## Android
How To Setting On Android

### GoogleOptionProviderAndroid

use `OptionProviderAndroid` because need [`GetGoogleIdOption`](https://developers.google.com/identity/android-credential-manager/android/reference/kotlin/com/google/android/libraries/identity/googleid/GetGoogleIdOption)


~~~kotlin
class MyGoogleOptionProvider : GoogleOptionProviderAndroid {

   override fun provideGoogleIdOption(): GetGoogleIdOption {
      return GetGoogleIdOption.Builder()
         .setFilterByAuthorizedAccounts(false)
         .setServerClientId("WEB_CLIENT_ID")
         .build()
   }
}
~~~
~~~kotlin
class AppActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
         super.onCreate(savedInstanceState)
         //...
         GoogleLoginHelper.setOptionProvider(MyGoogleOptionProvider())
    }
}
~~~

## iOS
no need any setting for google Login

> IOS need [`GoogeSigin`](https://github.com/google/GoogleSignIn-iOS) SPM or pods on Your Project

## request Login

<tabs>
    <tab title="NO-UI">
        <code-block lang="kotlin">GoogleLoginHelper.requestLogin(tokenResultHandler)</code-block>
    </tab>
    <tab title="With-UI">
        <code-block lang="kotlin">GoogleLoginButton()</code-block>
    </tab>
</tabs>