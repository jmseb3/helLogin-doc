# Edit UI Button

Use Button Type/Theme

## Button Type

~~~kotlin
sealed interface ButtonType {

    /**
     * Icon Only
     */
    data object IconOnly : ButtonType

    /**
     * Icon With Text
     */
    data class WithText(val text: String) : ButtonType
}
~~~

## Button Theme

~~~kotlin
sealed interface ButtonTheme {

    /**
     * Light mode
     */
    data object Light : ButtonTheme

    /**
     * Dark mode
     */
    data object Dark : ButtonTheme
}
~~~