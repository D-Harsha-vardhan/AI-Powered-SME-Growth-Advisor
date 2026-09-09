# Hilt Navigation Implementation Plan

This plan outlines the steps to set up Hilt and implement a navigation flow (Splash -> Login -> Main) using Hilt-provided ViewModels in Jetpack Compose.

## User Review Required

> [!IMPORTANT]
> I will be adding Dagger Hilt to your project, which includes adding the Hilt Gradle plugin and several dependencies. I will also be creating a custom `Application` class.

> [!NOTE]
> I will use standard `androidx.navigation:navigation-compose` instead of the existing `androidx.navigation3` for this implementation, as it is the standard way to use `hiltViewModel()`.

## Proposed Changes

### [Dependencies]

#### [MODIFY] [libs.versions.toml](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/gradle/libs.versions.toml)
- Add Hilt and Hilt Navigation Compose versions and libraries.
- Add KSP plugin.

#### [MODIFY] [build.gradle.kts](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/build.gradle.kts)
- Add Hilt and KSP plugins to the root build file.

#### [MODIFY] [app/build.gradle.kts](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/build.gradle.kts)
- Apply Hilt and KSP plugins.
- Add Hilt and Navigation Compose dependencies.

---

### [Hilt Setup]

#### [NEW] [SmeApplication.kt](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/java/com/example/smeadvisor/SmeApplication.kt)
- Create a class annotated with `@HiltAndroidApp`.

#### [MODIFY] [AndroidManifest.xml](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/AndroidManifest.xml)
- Register `SmeApplication` in the `<application>` tag.

#### [MODIFY] [MainActivity.kt](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/java/com/example/smeadvisor/MainActivity.kt)
- Annotate with `@AndroidEntryPoint`.
- Replace existing `AndroidView` (WebView) with the new `NavHost` setup.

---

### [ViewModels & Screens]

#### [NEW] [SplashViewModel.kt](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/java/com/example/smeadvisor/ui/splash/SplashViewModel.kt)
#### [NEW] [LoginViewModel.kt](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/java/com/example/smeadvisor/ui/login/LoginViewModel.kt)
#### [NEW] [MainViewModel.kt](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/java/com/example/smeadvisor/ui/main/MainViewModel.kt)
- Implement simple `@HiltViewModel`s for each screen.

#### [NEW] [SplashScreenBinding.kt](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/java/com/example/smeadvisor/ui/splash/SplashScreen.kt)
#### [NEW] [LoginScreenBinding.kt](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/java/com/example/smeadvisor/ui/login/LoginScreen.kt)
#### [MODIFY] [MainScreen.kt](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/java/com/example/smeadvisor/ui/main/MainScreen.kt)
- Create simple Composable screens that take their respective ViewModels.

---

### [Navigation]

#### [NEW] [AppNavigation.kt](file:///D:/PRO/SME new/AI-Powered-SME-Growth-Advisor-main/app/src/main/java/com/example/smeadvisor/AppNavigation.kt)
- Implement the `NavHost` with routes for `splash`, `login`, and `main`.
- Use `hiltViewModel()` to inject ViewModels into each destination.

## Verification Plan

### Automated Tests
- I will attempt to build the project (via shell if possible, or just verify code integrity).

### Manual Verification
- You can run the app on your device to verify the Splash -> Login -> Main transition.
