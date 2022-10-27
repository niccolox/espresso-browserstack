# Onboarding


## Assemble APK
Build the main application: ./gradlew assemble (apk will be generated in the app/build/outputs/apk/debug/ directory)

./gradlew assemble

curl -u "BROWSERSTACK_USERNAME:BROWSERSTACK_ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/espresso/v2/app" \
-F "file=@/Users/nicholas/Projects/AppAutomate/BStackDemo/Espresso/espresso-browserstack/app/build/outputs/apk/debug/app-debug.apk"
{"app_name":"app-debug.apk","app_url":"bs://1025c0cb93ccda14ec53e92e3f0e831981945eb7","app_version":"1.0","app_id":"1025c0cb93ccda14ec53e92e3f0e831981945eb7","uploaded_at":"2022-10-27 01:52:34 UTC","expiry":"2022-11-26 01:52:34 UTC"}%

## Assemble APK Test
Build the test application: ./gradlew assembleAndroidTest (apk will be generated in the app/build/outputs/apk/androidTest/debug/ directory)

./gradlew assembleAndroidTest

curl -u "BROWSERSTACK_USERNAME:BROWSERSTACK_ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/espresso/v2/test-suite" \
-F "file=@/Users/nicholas/Projects/AppAutomate/BStackDemo/Espresso/espresso-browserstack/app/build/outputs/apk/androidTest/debug/app-debug-androidTest.apk"
{"test_suite_name":"app-debug-androidTest.apk","test_suite_url":"bs://5671ea4509958a48b372a118b6455fc26dd25166","test_suite_id":"5671ea4509958a48b372a118b6455fc26dd25166","uploaded_at":"2022-10-27 01:53:23 UTC","expiry":"2022-11-26 01:53:23 UTC","framework":"espresso"}% 

## Execute the Test via API

curl -u "BROWSERSTACK_USERNAME:BROWSERSTACK_ACCESS_KEY" \
-X POST "https://api-cloud.browserstack.com/app-automate/espresso/v2/build" \
-d '{"app": "bs://1025c0cb93ccda14ec53e92e3f0e831981945eb7", "testSuite": "bs://5671ea4509958a48b372a118b6455fc26dd25166", "devices": ["Samsung Galaxy S9 Plus-9.0"]}' \
-H "Content-Type: application/json" 

{"message":"Success","build_id":"0313dbf6d9feff460d0c4cb94f398347083734c4"}%

### Results
https://app-automate.browserstack.com/dashboard/v2/builds/0313dbf6d9feff460d0c4cb94f398347083734c4?buildUserIds=6504358