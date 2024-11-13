# GitHub

How To Use Github Login

## Common

make [Github OAuth Apps](https://github.com/settings/developers) and don't forget your `GITHUB_CLIENT_ID` and `GITHUB_CLIENT_SECRET`

### GithubOptionProvider

install the GithubOptionProvider in the commonMain module (or separately for each platform if
needed).

~~~kotlin
class GitHubProvider : GithubOptionProvider {
    companion object {
        const val GITHUB_CLIENT_ID = "YOUR_CLIENT_ID"
        const val GITHUB_CLIENT_SECRET = "YOUR_CLIENT_SECRET"
    }

    override fun provideLoginId(): CodeRequestData {
        return CodeRequestData(
            GITHUB_CLIENT_ID
        )
    }

    override fun provideClientData(): ClientData {
        return ClientData(
            GITHUB_CLIENT_ID,
            GITHUB_CLIENT_SECRET
        )
    }

    override fun provideScheme(): String {
        return "hellogin"
    }
}
~~~

~~~kotlin
@Composable
internal fun App() = AppTheme {
    LaunchedEffect(true) {
        GithubLoginHelper.setOptionProvider(GitHubProvider())
    }
}
~~~


## Android

### Scheme Setting
~~~xml
<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android">

    <application>
        <activity>
            ...
            <intent-filter>
                <action android:name="android.intent.action.VIEW" />

                <category android:name="android.intent.category.DEFAULT" />
                <category android:name="android.intent.category.BROWSABLE" />

                <data android:host="login" android:scheme="hellogin" />
            </intent-filter>
        </activity>
    </application>

</manifest>
~~~

### Parse Code onNewIntent 
~~~kotlin
class AppActivity : ComponentActivity() {
    override fun onNewIntent(intent: Intent) {
        super.onNewIntent(intent)
        CoroutineScope(Dispatchers.Main).launch {
            intent.data?.getQueryParameter("code")?.let { code ->
                // Get Token By Intent
                GithubLoginHelper.requestAuth(code)
            }
        }
    }
}
~~~

## iOS
no need any setting for github Login


## request Login

<tabs>
    <tab title="NO-UI">
        <code-block lang="kotlin">GithubLoginHelper.requestLogin(tokenResultHandler)</code-block>
    </tab>
    <tab title="With-UI">
        <code-block lang="kotlin">GithubLoginButton()</code-block>
    </tab>
</tabs>