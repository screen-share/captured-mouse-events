# Screen-Capture Mouse Events

Web applications can use `getDisplayMedia()` to capture any display-surface - tabs, windows or screens.
When they do, they can also specify the cursor constraint to control whether the cursor's pixels are captured or not.

But what if the application wishes to programmatically observe the location of the cursor?
That can be done by scanning each frame and employing heuristics to detect the cursor.
But that's neither simple, nor efficient, nor robust.

A mechanism for exposing mouse coordinates over a captured surface to a capturing application is desirable.
Such a mechanism is proposed by this specification.

The TL;DR is that we expose an `oncapturedmousechange` EventHandler on [CaptureController](https://www.w3.org/TR/screen-capture/#dom-capturecontroller).
Events are of the general shape `{surfaceX: long, surfaceY: long}`, exposing the coordinates of the mouse relative to the origin of the captured surface.

Future extensions, such as exposing the state of mouse buttons and modifier keys, are outscoped for the time being.
