# Captured Mouse Events

Web applications can use `getDisplayMedia()` to capture any display-surface - tabs, windows or screens.
When they do, they can also specify the [cursor constraint](https://www.w3.org/TR/screen-capture/#dfn-cursor) to control whether the cursor's pixels are captured or not.

But what if the application wishes to programmatically observe the location of the cursor?
That can be done by scanning each frame and employing heuristics to detect the cursor.
But that's neither simple, nor efficient, nor robust.

To that end, we propose a mechanism for exposing mouse coordinates over a captured surface to a capturing application.

The TL;DR is that we expose an `oncapturedmousechange` EventHandler on [CaptureController](https://www.w3.org/TR/screen-capture/#dom-capturecontroller).
Events are of the general shape `{surfaceX: long, surfaceY: long}`, exposing the coordinates of the mouse relative to the origin of the captured surface.

### Future extensions
#### Planned
1. Exposing the shape of the cursor
2. Exposing useful timestamps (that can be correlated with video frames' timestamps)

#### Potential (discussed but not currently planned)
1. Exposing mouse buttons (might be tricky security- and privacy-wise)
2. Exposing the state of modifier keys (might be tricky security- and privacy-wise)
3. Exposing keyboard events (might be tricky security- and privacy-wise)
4. Mechanism for controlling event frequency
