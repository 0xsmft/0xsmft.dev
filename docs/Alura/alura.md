# Alura

Alura is the name of the in-game UI system, it is a frame-by-frame immediate-mode UI system.

The orgin of the canvas is the top left of the canvas.
The origin of elements is the same.

Mouse positions are relative in canvas space and not in screen space.

## Design

In order to draw elements on the screen you must first access the current [AluraCanvas](aluracanvas.md) aka `g_AluraCanvas`, from there the canvas provides functions to draw elements.

The lifetime and validity of `g_AluraCanvas` is guaranteed to be valid so long as you access it during an Alura frame.

### Drawers

Main page: [AluraDrawer](aluradrawer.md)

Drawers are inheritable class to allow for custom drawing onto the AluraCanvas.

For example in a game you may have `PlayerHUD`, `GameStateHUD` in which all of them would be child classes of `AluraDrawer`.

The lifetime of an AluraDrawer is complex. You must store your AluraDrawer with an [intrusive reference](ref.md) this means that the class that owns the drawer should release the reference. 

AluraCanvas will also hold an owning reference to the drawer as well.

Futhermore, you must also take into account of any objects you store in the drawer, if you create a drawer to display player information you may want to use a [`WeakRef`](ref.md) to hold a reference to the player, if you do not, you may run into lifetime issues.

## Styling

Alura's style is customisable and you can use an [`AluraStylingProfile`](alurastylingprofile.md) to do so.

You can specify a styling profile during the creation of the AluraCanvas.

You can also swap styling profiles out after the end of the frame. Attempting to swap during the frame is not supported.

## Related

[AluraCanvas](aluracanvas.md)
[AluraCanvasSpecification](aluracanvasspecification.md)
[AluraFont](alurafont.md)
[AluraColour](aluracolour.md)
[AluraStyle](alurastyle.md)
[AluraStylingProfile](alurastylingprofile.md)
