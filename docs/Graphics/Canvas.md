## Module Graphics.Canvas

This module defines foreign types and functions for working with the 2D
Canvas API.

#### `Canvas`

``` purescript
data Canvas :: !
```

The `Canvas` effect denotes computations which read/write from/to the canvas.

#### `CanvasElement`

``` purescript
data CanvasElement :: *
```

A canvas HTML element.

#### `Context2D`

``` purescript
data Context2D :: *
```

A 2D graphics context.

#### `ImageData`

``` purescript
type ImageData = { width :: Int, height :: Int, data :: Uint8ClampedArray }
```

An image data object, used to store raster data outside the canvas.

#### `CanvasImageSource`

``` purescript
data CanvasImageSource :: *
```

Opaque object for drawing elements and things to the canvas.

#### `CanvasGradient`

``` purescript
data CanvasGradient :: *
```

Opaque object describing a gradient.

#### `canvasElementToImageSource`

``` purescript
canvasElementToImageSource :: CanvasElement -> CanvasImageSource
```

#### `tryLoadImage`

``` purescript
tryLoadImage :: forall eff. String -> (Maybe CanvasImageSource -> Eff (canvas :: Canvas | eff) Unit) -> Eff (canvas :: Canvas | eff) Unit
```

Wrapper for asynchronously loading a image file by path and use it in callback, e.g. drawImage

#### `getCanvasElementById`

``` purescript
getCanvasElementById :: forall eff. String -> Eff (canvas :: Canvas | eff) (Maybe CanvasElement)
```

Get a canvas element by ID, or `Nothing` if the element does not exist.

#### `getContext2D`

``` purescript
getContext2D :: forall eff. CanvasElement -> Eff (canvas :: Canvas | eff) Context2D
```

Get the 2D graphics context for a canvas element.

#### `getCanvasWidth`

``` purescript
getCanvasWidth :: forall eff. CanvasElement -> Eff (canvas :: Canvas | eff) Number
```

Get the canvas width in pixels.

#### `getCanvasHeight`

``` purescript
getCanvasHeight :: forall eff. CanvasElement -> Eff (canvas :: Canvas | eff) Number
```

Get the canvas height in pixels.

#### `setCanvasWidth`

``` purescript
setCanvasWidth :: forall eff. Number -> CanvasElement -> Eff (canvas :: Canvas | eff) CanvasElement
```

Set the canvas width in pixels.

#### `setCanvasHeight`

``` purescript
setCanvasHeight :: forall eff. Number -> CanvasElement -> Eff (canvas :: Canvas | eff) CanvasElement
```

Set the canvas height in pixels.

#### `Dimensions`

``` purescript
type Dimensions = { width :: Number, height :: Number }
```

Canvas dimensions (width and height) in pixels.

#### `getCanvasDimensions`

``` purescript
getCanvasDimensions :: forall eff. CanvasElement -> Eff (canvas :: Canvas | eff) Dimensions
```

Get the canvas dimensions in pixels.

#### `setCanvasDimensions`

``` purescript
setCanvasDimensions :: forall eff. Dimensions -> CanvasElement -> Eff (canvas :: Canvas | eff) CanvasElement
```

Set the canvas dimensions in pixels.

#### `canvasToDataURL`

``` purescript
canvasToDataURL :: forall eff. CanvasElement -> Eff (canvas :: Canvas | eff) String
```

Create a data URL for the current canvas contents

#### `setLineWidth`

``` purescript
setLineWidth :: forall eff. Number -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current line width.

#### `setFillStyle`

``` purescript
setFillStyle :: forall eff. String -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current fill style/color.

#### `setStrokeStyle`

``` purescript
setStrokeStyle :: forall eff. String -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current stroke style/color.

#### `setShadowColor`

``` purescript
setShadowColor :: forall eff. String -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current shadow color.

#### `setShadowBlur`

``` purescript
setShadowBlur :: forall eff. Number -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current shadow blur radius.

#### `setShadowOffsetX`

``` purescript
setShadowOffsetX :: forall eff. Number -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current shadow x-offset.

#### `setShadowOffsetY`

``` purescript
setShadowOffsetY :: forall eff. Number -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current shadow y-offset.

#### `LineCap`

``` purescript
data LineCap
  = Round
  | Square
  | Butt
```

Enumerates the different types of line cap.

#### `setLineCap`

``` purescript
setLineCap :: forall eff. LineCap -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current line cap type.

#### `Composite`

``` purescript
data Composite
  = SourceOver
  | SourceIn
  | SourceOut
  | SourceAtop
  | DestinationOver
  | DestinationIn
  | DestinationOut
  | DestinationAtop
  | Lighter
  | Copy
  | Xor
```

Enumerates the different types of alpha composite operations.

##### Instances
``` purescript
Show Composite
```

#### `setGlobalCompositeOperation`

``` purescript
setGlobalCompositeOperation :: forall eff. Context2D -> Composite -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current composite operation.

#### `setGlobalAlpha`

``` purescript
setGlobalAlpha :: forall eff. Context2D -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current global alpha level.

#### `beginPath`

``` purescript
beginPath :: forall eff. Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Begin a path object.

#### `stroke`

``` purescript
stroke :: forall eff. Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Stroke the current object.

#### `fill`

``` purescript
fill :: forall eff. Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Fill the current object.

#### `clip`

``` purescript
clip :: forall eff. Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Clip to the current object.

#### `lineTo`

``` purescript
lineTo :: forall eff. Context2D -> Number -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

Move the path to the specified coordinates, drawing a line segment.

#### `moveTo`

``` purescript
moveTo :: forall eff. Context2D -> Number -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

Move the path to the specified coordinates, without drawing a line segment.

#### `closePath`

``` purescript
closePath :: forall eff. Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Close the current path.

#### `strokePath`

``` purescript
strokePath :: forall eff a. Context2D -> Eff (canvas :: Canvas | eff) a -> Eff (canvas :: Canvas | eff) a
```

A convenience function for drawing a stroked path.

For example:

```purescript
strokePath ctx $ do
  moveTo ctx 10.0 10.0
  lineTo ctx 20.0 20.0
  lineTo ctx 10.0 20.0
  closePath ctx
```

#### `fillPath`

``` purescript
fillPath :: forall eff a. Context2D -> Eff (canvas :: Canvas | eff) a -> Eff (canvas :: Canvas | eff) a
```

A convenience function for drawing a filled path.

For example:

```purescript
fillPath ctx $ do
  moveTo ctx 10.0 10.0
  lineTo ctx 20.0 20.0
  lineTo ctx 10.0 20.0
  closePath ctx
```

#### `Arc`

``` purescript
type Arc = { x :: Number, y :: Number, r :: Number, start :: Number, end :: Number }
```

A type representing an arc object:

- The center coordinates `x` and `y`,
- The radius `r`,
- The starting and ending angles, `start` and `end`.

#### `arc`

``` purescript
arc :: forall eff. Context2D -> Arc -> Eff (canvas :: Canvas | eff) Context2D
```

Render an arc object.

#### `Rectangle`

``` purescript
type Rectangle = { x :: Number, y :: Number, w :: Number, h :: Number }
```

A type representing a rectangle object:

- The top-left corner coordinates `x` and `y`,
- The width and height `w` and `h`.

#### `rect`

``` purescript
rect :: forall eff. Context2D -> Rectangle -> Eff (canvas :: Canvas | eff) Context2D
```

Render a rectangle.

#### `fillRect`

``` purescript
fillRect :: forall eff. Context2D -> Rectangle -> Eff (canvas :: Canvas | eff) Context2D
```

Fill a rectangle.

#### `strokeRect`

``` purescript
strokeRect :: forall eff. Context2D -> Rectangle -> Eff (canvas :: Canvas | eff) Context2D
```

Stroke a rectangle.

#### `clearRect`

``` purescript
clearRect :: forall eff. Context2D -> Rectangle -> Eff (canvas :: Canvas | eff) Context2D
```

Clear a rectangle.

#### `ScaleTransform`

``` purescript
type ScaleTransform = { scaleX :: Number, scaleY :: Number }
```

An object representing a scaling transform:

- The scale factors in the `x` and `y` directions, `scaleX` and `scaleY`.

#### `scale`

``` purescript
scale :: forall eff. ScaleTransform -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Apply a scaling transform.

#### `rotate`

``` purescript
rotate :: forall eff. Number -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Apply a rotation.

#### `TranslateTransform`

``` purescript
type TranslateTransform = { translateX :: Number, translateY :: Number }
```

An object representing a translation:

- The translation amounts in the `x` and `y` directions, `translateX` and `translateY`.

#### `translate`

``` purescript
translate :: forall eff. TranslateTransform -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Apply a translation

#### `Transform`

``` purescript
type Transform = { m11 :: Number, m12 :: Number, m21 :: Number, m22 :: Number, m31 :: Number, m32 :: Number }
```

An object representing a general transformation as a homogeneous matrix.

#### `transform`

``` purescript
transform :: forall eff. Transform -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Apply a general transformation.

#### `TextAlign`

``` purescript
data TextAlign
  = AlignLeft
  | AlignRight
  | AlignCenter
  | AlignStart
  | AlignEnd
```

Enumerates types of text alignment.

##### Instances
``` purescript
Show TextAlign
```

#### `textAlign`

``` purescript
textAlign :: forall eff. Context2D -> Eff (canvas :: Canvas | eff) TextAlign
```

Get the current text alignment.

#### `setTextAlign`

``` purescript
setTextAlign :: forall eff. Context2D -> TextAlign -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current text alignment.

#### `TextMetrics`

``` purescript
type TextMetrics = { width :: Number }
```

Text metrics:

- The text width in pixels. 

#### `font`

``` purescript
font :: forall eff. Context2D -> Eff (canvas :: Canvas | eff) String
```

Get the current font.

#### `setFont`

``` purescript
setFont :: forall eff. String -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the current font.

#### `fillText`

``` purescript
fillText :: forall eff. Context2D -> String -> Number -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

Fill some text.

#### `strokeText`

``` purescript
strokeText :: forall eff. Context2D -> String -> Number -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

Stroke some text.

#### `measureText`

``` purescript
measureText :: forall eff. Context2D -> String -> Eff (canvas :: Canvas | eff) TextMetrics
```

Measure some text.

#### `save`

``` purescript
save :: forall eff. Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Save the current context.

#### `restore`

``` purescript
restore :: forall eff. Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Restore the previous context.

#### `withContext`

``` purescript
withContext :: forall eff a. Context2D -> Eff (canvas :: Canvas | eff) a -> Eff (canvas :: Canvas | eff) a
```

A convenience function: run the action, preserving the existing context.

For example, outside this block, the fill style is preseved:

```purescript
withContext ctx $ do
  setFillStyle "red" ctx
  ...
```

#### `getImageData`

``` purescript
getImageData :: forall eff. Context2D -> Number -> Number -> Number -> Number -> Eff (canvas :: Canvas | eff) ImageData
```

Get image data for a portion of the canvas.

#### `putImageDataFull`

``` purescript
putImageDataFull :: forall eff. Context2D -> ImageData -> Number -> Number -> Number -> Number -> Number -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

Set image data for a portion of the canvas.

#### `putImageData`

``` purescript
putImageData :: forall eff. Context2D -> ImageData -> Number -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

Set image data for a portion of the canvas.

#### `createImageData`

``` purescript
createImageData :: forall eff. Context2D -> Number -> Number -> Eff (canvas :: Canvas | eff) ImageData
```

Create an image data object.

#### `createImageDataCopy`

``` purescript
createImageDataCopy :: forall eff. Context2D -> ImageData -> Eff (canvas :: Canvas | eff) ImageData
```

Create a copy of an image data object.

#### `drawImage`

``` purescript
drawImage :: forall eff. Context2D -> CanvasImageSource -> Number -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

#### `drawImageScale`

``` purescript
drawImageScale :: forall eff. Context2D -> CanvasImageSource -> Number -> Number -> Number -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

#### `drawImageFull`

``` purescript
drawImageFull :: forall eff. Context2D -> CanvasImageSource -> Number -> Number -> Number -> Number -> Number -> Number -> Number -> Number -> Eff (canvas :: Canvas | eff) Context2D
```

#### `LinearGradient`

``` purescript
type LinearGradient = { x0 :: Number, y0 :: Number, x1 :: Number, y1 :: Number }
```

A type representing a linear gradient.
 -  Starting point coordinates: (`x0`, `y0`)
 -  Ending point coordinates: (`x1`, `y1`)

#### `createLinearGradient`

``` purescript
createLinearGradient :: forall eff. LinearGradient -> Context2D -> Eff (canvas :: Canvas | eff) CanvasGradient
```

Create a linear CanvasGradient.

#### `RadialGradient`

``` purescript
type RadialGradient = { x0 :: Number, y0 :: Number, r0 :: Number, x1 :: Number, y1 :: Number, r1 :: Number }
```

A type representing a radial gradient.
 -  Starting circle center coordinates: (`x0`, `y0`)
 -  Starting circle radius: `r0`
 -  Ending circle center coordinates: (`x1`, `y1`)
 -  Ending circle radius: `r1`

#### `createRadialGradient`

``` purescript
createRadialGradient :: forall eff. RadialGradient -> Context2D -> Eff (canvas :: Canvas | eff) CanvasGradient
```

Create a radial CanvasGradient.

#### `addColorStop`

``` purescript
addColorStop :: forall eff. Number -> String -> CanvasGradient -> Eff (canvas :: Canvas | eff) CanvasGradient
```

Add a single color stop to a CanvasGradient.

#### `setGradientFillStyle`

``` purescript
setGradientFillStyle :: forall eff. CanvasGradient -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Set the Context2D fillstyle to the CanvasGradient.

#### `QuadraticCurve`

``` purescript
type QuadraticCurve = { cpx :: Number, cpy :: Number, x :: Number, y :: Number }
```

A type representing a quadratic Bézier curve.
 - Bézier control point: (`cpx`, `cpy`)
 - Ending point coordinates: (`x`, `y`)

#### `quadraticCurveTo`

``` purescript
quadraticCurveTo :: forall eff. QuadraticCurve -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Draw a quadratic Bézier curve.

#### `BezierCurve`

``` purescript
type BezierCurve = { cp1x :: Number, cp1y :: Number, cp2x :: Number, cp2y :: Number, x :: Number, y :: Number }
```

A type representing a cubic Bézier curve.
 - First Bézier control point: (`cp1x`, `cp1y`)
 - Second Bézier control point: (`cp2x`, `cp2y`)
 - Ending point: (`x`, `y`)

#### `bezierCurveTo`

``` purescript
bezierCurveTo :: forall eff. BezierCurve -> Context2D -> Eff (canvas :: Canvas | eff) Context2D
```

Draw a cubic Bézier curve.


