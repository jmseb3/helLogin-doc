# Apple

How To Use Apple Login

## Android
make service id for apple Login

### AppleOptionProviderAndroid
android need clientId and Redirect Url

~~~kotlin
class MyAppleOptionProvider : AppleOptionProviderAndroid {

   override val mClientId: String
      get() = "Your Service Id"

   override val mRedirectUrl: String
      get() = "Your Redirect Url"

   override val requestScope: AppleSignInRequestScope
      get() = AppleSignInRequestScope.FullNameAndEmail
}
~~~
~~~kotlin
class AppActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
         super.onCreate(savedInstanceState)
         AppleLoginHelper.setOptionProvider(MyAppleOptionProvider())
         //Add Other Code
    }
   
}
~~~

## iOS
no need any setting for Apple Login


## request Login

<tabs>
    <tab title="NO-UI">
        <code-block lang="kotlin">AppleLoginHelper.requestLogin(tokenResultHandler)</code-block>
    </tab>
    <tab title="With-UI">
        <code-block lang="kotlin">AppleLoginButton()</code-block>
    </tab>
</tabs>