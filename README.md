# CloudGoogleSpeechToText
Running on Android 4.1+

If you have a problem running Google Cloud speech to text api on Android devices 4.1+

What I did in this project
1. Downloaded https://github.com/GoogleCloudPlatform/android-docs-samples/blob/master/README.md
2. Changed classes in project SpeechRecognitionClient in android-docs-samples-master\speech
  - Changed AudioRecord in AudoEmitter.kt to support API 16
3. Imported org.conscrypt:conscrypt-android:2.5.1 library
  - Had to exclude group org.conscrypt from google-cloud-speech (in build.gradle)
4. Added
  init {
      Security.insertProviderAt(Conscrypt.newProvider(), 1)
   }
   For Android 4.1 to run proper TLS for GRC to work
5. I downloaded https://github.com/googleapis project
  - Changed all StandardCharsets found in google-http-client to Charset.forName("UTF-8"))
  - And also changed some tests to work
  - https://imgur.com/a/iU7yjCZ (files changes)
6. I have build this project and gor .jar files, which I included here
7. And now it works!

HOW TO INSTALL:
1. Just add your credential.json in app/res/raw/credential.json
2. Run
