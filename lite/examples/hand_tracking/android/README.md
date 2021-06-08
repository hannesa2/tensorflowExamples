# TensorFlow Lite Hand Tracking Android Demo
### Overview
This is an app that uses MediaPipe's [Hands](https://google.github.io/mediapipe/solutions/hands.html) model to detect the hand parts in the frames seen by your device's camera. These instructions walk you through building and running the demo on an Android device. Camera captures are discarded immediately after use, nothing is stored or saved. 

![Demo Image](screenshot.png)

## Integrate to your app

Hand detection logic is implemented in classes inside the package `org.tensorflow.lite.examples.handdetection`. Follow these steps to integrate the model into your own app.

1. Copy the TFLite models (`palm_detection_full.tflite`  and `hand_landmark_full.tflite`) to your app's `assests` folder.

2. Add these dependencies to your app's `build.gradle` file:
    * `implementation 'org.tensorflow:tensorflow-lite-support:0.2.0'`
    * `implementation 'org.tensorflow:tensorflow-lite-gpu:2.5.0'`

3. Copy all files under the `org.tensorflow.lite.examples.handdetection.handlandmark` package to your app.

4. Initialize a hand detector instance:

```kotlin
val detector = HandDetector.create(this)
```

5. Detect hand landmarks:
```kotlin
val landmarks = detector.process(bitmap)
// Do something with the landmarks
```

6. Close the hand detector once completed:
```kotlin
detector.close()
```

### Model used
Downloading, extraction and placement in assets folder has been managed
 automatically by `download.gradle`.

If you explicitly want to download the model, you can download it from here:
* [Palm detection model](https://github.com/google/mediapipe/raw/master/mediapipe/modules/palm_detection/palm_detection_full.tflite)
* [Hand landmark detection model](https://github.com/google/mediapipe/raw/master/mediapipe/modules/hand_landmark/hand_landmark_full.tflite) 
 
### Additional Note
_Please do not delete the assets folder content_. If you explicitly deleted the
 files, then please choose `Build` > `Rebuild` from menu to re-download the
 deleted model files into assets folder.

