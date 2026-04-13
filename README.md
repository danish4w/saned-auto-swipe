name: Build APK

on:
  push:
    branches: [ main ]
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest
    
    steps:
    - uses: actions/checkout@v4
    
    - name: Setup Android SDK
      uses: android-actions/setup-android@v3
    
    - name: Create full Android project
      run: |
        # Create folder structure
        mkdir -p app/src/main/java/com/saned/autoswipe
        mkdir -p app/src/main/res/layout
        mkdir -p app/src/main/res/values
        mkdir -p app/src/main/res/xml
        
        # Create build.gradle files (root and app)
        # Create all Kotlin and XML files
        # ... (complete code)
    
    - name: Build APK
      run: ./gradlew assembleDebug
      
    - name: Upload APK
      uses: actions/upload-artifact@v4
      with:
        name: Saned-Auto-Swipe
        path: app/build/outputs/apk/debug/*.apk