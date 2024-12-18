# Expo Linking.getInitialURL() Inconsistently Returns Null

This repository demonstrates a bug in the Expo `Linking` API where `getInitialURL()` inconsistently returns `null` when the app is launched with a deep link.  This makes it difficult to reliably handle initial app startup and process deep links.

## Problem Description

The `Linking.getInitialURL()` method is designed to retrieve the URL used to launch the app.  However, in some cases, it returns `null` even when a deep link was successfully opened, making it impossible to know if there was an initial deep link at startup. This behavior is inconsistent and unreliable. 

## Steps to Reproduce

1. Clone the repository.
2. Run the app using `expo start`.
3. Launch the app using a deep link (e.g., `myapp://somepath`).
4. Observe the console output: you will see `null` printed sometimes, even when the app was opened with a deep link.

## Expected Behavior

`getInitialURL()` should always return the deep link URL used to launch the app if one exists.  If no deep link was used, it should return null.  The behavior should be consistent and reliable.

## Workaround

Currently there's no robust solution within the Expo Linking API. A possible workaround involves using a combination of `Linking.addEventListener` and storing the deep link URL in AsyncStorage, though this is less ideal because it requires extra storage and event handling.
