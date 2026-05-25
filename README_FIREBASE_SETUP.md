# Firebase Integration Instructions

This file documents all configuration and code snippets required for Firebase integration as we progress step-by-step.

---

## Step 1A: Google Services File
1. Go to your Firebase project settings in the Firebase Console.
2. Register your Android app with your package name (e.g., `com.example.focusguard`).
3. Download the `google-services.json` file and place it inside the `app/` directory.

---
## Step 1B: Project-level build.gradle
Add the following inside your `buildscript { dependencies { ... } }` block:

```groovy
classpath 'com.google.gms:google-services:4.4.1'
```

---
## Step 1B: App-level build.gradle
**Plugins section:**
```groovy
id 'com.google.gms.google-services'
```
**Dependencies section:**
```groovy
implementation platform('com.google.firebase:firebase-bom:32.8.0')
implementation 'com.google.firebase:firebase-firestore-ktx'
implementation 'com.google.firebase:firebase-auth-ktx'
```

---
## Step 1C: Verify Firestore Initialization in MainActivity.kt
Add to your `onCreate` method:
```kotlin
import com.google.firebase.ktx.Firebase
import com.google.firebase.firestore.ktx.firestore

val db = Firebase.firestore
db.collection("debugInit").add(mapOf("hello" to "world"))
```

---
**Next:** Let us know when you see the test data ("debugInit" doc) appear in the Firebase Console, so we can continue to Step 2!
