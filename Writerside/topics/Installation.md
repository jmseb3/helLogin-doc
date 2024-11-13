# Installation

How To Install Hellogin Library

## implementation

HelLogin is available on Maven Central. In your root project `build.gradle.kts` file (
or `settings.gradle` file) add `mavenCentral()` to repositories.

```kotlin
repositories {
    mavenCentral()
}
```

Then in your shared module add desired dependencies in `commonMain`. Latest


version: ![Maven Central Version](https://img.shields.io/maven-central/v/io.github.jmseb3/hellogin-bom)

### toml
Use Version Catalog
~~~toml
[versions]
hellogin = "1.1.0"

[libraries]
hellogin-bom = { module = "io.github.jmseb3:hellogin-bom", version.ref = "hellogin" }

hellogin-google = { module = "io.github.jmseb3:hellogin-google" }
hellogin-github = { module = "io.github.jmseb3:hellogin-github" }
hellogin-apple = { module = "io.github.jmseb3:hellogin-apple" }
# OR
hellogin-google-ui = { module = "io.github.jmseb3:hellogin-google-ui" }
hellogin-github-ui = { module = "io.github.jmseb3:hellogin-github-ui" }
hellogin-apple-ui = { module = "io.github.jmseb3:hellogin-apple-ui" }

~~~

```kotlin
sourceSets {
    commonMain.dependencies {
        implementation(project.dependencies.platform(libs.hellogin.bom))

        implementation(libs.hellogin.google)
        implementation(libs.hellogin.github)
        implementation(libs.hellogin.apple)
        // or 
        implementation(libs.hellogin.google.ui)
        implementation(libs.hellogin.github.ui)
        implementation(libs.hellogin.apple.ui)
    }
}
```

### gradle
Use Default 
```kotlin
sourceSets {
    commonMain.dependencies {
        implementation(platform("io.github.jmseb3:hellogin-bom:1.1.0"))

        implementation("io.github.jmseb3:hellogin-google") //google login library
        implementation("io.github.jmseb3:hellogin-github") //github login library 
        implementation("io.github.jmseb3:hellogin-apple") //apple login library
        // or
        implementation("io.github.jmseb3:hellogin-google-ui") //google login with ui library
        implementation("io.github.jmseb3:hellogin-github-ui") //github login with ui library
        implementation("io.github.jmseb3:hellogin-apple-ui") //apple login with ui library
    }
}
```

> `io.github.jmseb3:hellogin-*-ui` contain `io.github.jmseb3:hellogin-*`