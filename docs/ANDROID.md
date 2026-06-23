# Android Wrapper Notes

The repository is a browser game. To distribute it as a real Android application, use a standard Android Studio WebView app and copy `index.html` into:

```text
app/src/main/assets/index.html
```

The native activity should load:

```kotlin
webView.loadUrl("file:///android_asset/index.html")
```

Recommended WebView settings:

- JavaScript enabled
- DOM storage enabled
- Media playback allowed after user gesture
- No external navigation unless deliberately added
- Hardware acceleration enabled by default
- A visible back-stack handler that returns from Archive / Board / Settings before exiting

Do not rename or split the file without updating the asset path. The web edition is offline-first and does not need internet permission for normal play.
