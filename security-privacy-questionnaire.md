# Self-Review Questionnaire: Security and Privacy

Last update: 2023-07-07

Below are the answers to [W3C's Self-Review Questionnaire](https://w3ctag.github.io/security-questionnaire/#questions). See also Security/Privacy Considerations sections in the specification.

## 2.1. What information does this feature expose, and for what purposes?

When a user performs a screen capture via the [Screen Capture](https://w3c.github.io/mediacapture-screen-share) API, or any other future API that would use a [CaptureController](https://www.w3.org/TR/screen-capture/#capturecontroller) object to facilitate secreen-capture, this specification exposes mouse coordinates within the captured surface, or the departure of the mouse from the captured surface. (The cursor's location outside of the captured surface is NOT exposed.)

## 2.2. Do features in your specification expose the minimum amount of information necessary to enable their intended uses?

Yes, the minimum information is exposed. In fact, all of the information exposed is already available, but the mechanisms we introduce in our specification improve the simplicity, effiency and robustness to that information, by exposing the values programmatically, rather than requiring a capturing application to scan for the cursor's location in each and every frame.

## 2.3. Do the features in your specification expose personal information, personally-identifiable information (PII), or information derived from either?

Generally no. But one could imagine that fingerprinting could be done based on the patterns of a user's mouse movements. However, as mentioned in 2.2, this is not new information.

## 2.4. How do the features in your specification deal with sensitive information?

Sensitive information might be inferred on the person capturing their screen by e.g. analyzing the movement of the mouse (speed, tremor, no move at all etc). But as mentioned in 2.2 above, this is already available from the captured video frames.

## 2.5. Do the features in your specification introduce state that persists across browsing sessions?

No.

## 2.6. Do the features in your specification expose information about the underlying platform to origins?

These are just mouse coordinates relative to the captured surface which do not depend on the underlying platform. As mentioned in 2.2, this is already available from the captured video frames.

## 2.7. Does this specification allow an origin to send data to the underlying platform?

No.

## 2.8. Do features in this specification enable access to device sensors?

No.

## 2.9. Do features in this specification enable new script execution/loading mechanisms?

No.

## 2.10. Do features in this specification allow an origin to access other devices?

No.

## 2.11. Do features in this specification allow an origin some measure of control over a user agent’s native UI?

No.

## 2.12. What temporary identifiers do the features in this specification create or expose to the web?

None.

## 2.13. How does this specification distinguish between behavior in first-party and third-party contexts?

Mouse events are only dispatched to the `CaptureController` object, which lives in the document where the method `navigator.mediaDevices.getDisplayMedia()` was called to start the screen capture session. This specification does not make any specific distinction between first-party and third-party contexts besides what exists in the [Screen Capture](https://w3c.github.io/mediacapture-screen-share) specification.

## 2.14. How do the features in this specification work in the context of a browser’s Private Browsing or Incognito mode?

This specification does make any distiction between normal and private modes besides what exists in the [Screen Capture](https://w3c.github.io/mediacapture-screen-share) specification.

## 2.15. Does this specification have both "Security Considerations" and "Privacy Considerations" sections?

Yes, as a single section covering both sets of considerations. (Separation of these sections would not make sense in this specification's case.)

## 2.16. Do features in your specification enable origins to downgrade default security protections?

No.

## 2.17. What happens when a document that uses your feature is kept alive in BFCache (instead of getting destroyed) after navigation, and potentially gets reused on future navigations back to the document?

If that document is navigated away the screen capture session ends, stopping the user agent from firing additional events.
