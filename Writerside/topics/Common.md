# Common

Setting on Common For Use Library

## Android
use `HelloginContainerProvider.setContainer(this)` on Activity onCreate

~~~kotlin
class AppActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        HelloginContainerProvider.setContainer(this)
    }
}
~~~

## iOS

use `HelloginContainerProvider.setContainer(this)` on MainViewController create

~~~kotlin
fun MainViewController(): UIViewController {
    return ComposeUIViewController { App() }.also {
        HelloginContainerProvider.setContainer(it)
    }
}
~~~