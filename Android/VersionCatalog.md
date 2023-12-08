## Migrate to Version Catalog

### What is it?
- It's a `.toml` file which ideally sits in your project `gradle` folder and named as `libs.versions.toml`
- Allows to store all the libraries and versions at one place instead of separate `build.gradle` files for multi-module projects
- Allows auto complete in `build.gradle` file

### Migration steps
1. Create `libs.versions.toml` file under root `gradle` folder. Gradle looks for the catalog in the `libs.versions.toml` file by default, so use this default name
2. Add these sections in the file

```
[versions]
kotlin = "1.8.20"
compose = "1.4.3"
activityKtx = "1.6.1"
fragmentKtx = "1.5.5"

[libraries]
activityKtx = { group = "androidx.activity", name = "activity-ktx", version.ref = "activityKtx" }
fragmentKtx = { group = "androidx.fragment", name = "fragment-ktx", version.ref = "fragmentKtx" }

[bundles]
compose = ["compose.ui", "compose.material", "compose.tooling", "compose.runtime"]

[plugins]
android-application = { id = "com.android.application", version.ref = "androidGradlePlugin" }
android-library = { id = "com.android.library", version.ref = "androidGradlePlugin" }
kotlin-android = { id = "org.jetbrains.kotlin.android", version.ref = "kotlin" }
```

In `build.gradle.ktx` file, do this

```
// Top-level build file where you can add configuration options common to all sub-projects/modules.
plugins {
    alias(libs.plugins.android.application) apply false
    alias(libs.plugins.android.library) apply false
    alias(libs.plugins.kotlin.android) apply false
}

// app level plugins
plugins {
    alias(libs.plugins.android.application)
    alias(libs.plugins.kotlin.android)
}

// module level plugins
plugins {
    alias(libs.plugins.android.library)
    alias(libs.plugins.kotlin.android)
    id("kotlin-kapt")
}

dependencies {
    api(libs.appCompat)
    api(libs.activityKtx)
    api(libs.fragmentKtx)
}
```

## Source
https://developer.android.com/build/migrate-to-catalogs  
https://proandroiddev.com/migrating-to-version-catalog-ce737cb94233