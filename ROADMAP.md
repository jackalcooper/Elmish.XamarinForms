## Roadmap

* Programming model: Do these from `Xamarin.Forms.Core`: 
  * Change `Xaml.` to `UI.` or `XF.` or `X.`
  * Move to `seq<_>` as the de-facto model type
  * Animation
  * OpenGLView
  * Consider allowing explicit static Xaml through a type provider, e.g `xaml<"""<StackLayout Padding="20">...</StackLayout>""">`, evaluating to a `ViewElement`

* Docs
  * Generate `///` docs in code generator

* Programming efficiency
  * Support F# in Xamarin Live Player
  * Support hot-reloading of the saved model, reapplying to the same app where possible

* Handle 3rd party controls.
  * Add a charting control library
  * Possibly switch to a type provider (see [this comment](https://github.com/fsprojects/Elmish.XamarinForms/issues/50#issuecomment-390396365))

* Debugging
  * Improve diagnostics when property update fails
  * Fix bug where ranges for locals seem off-by-one in Android debugging

* Testing
  * Add an explicit unit-test project

* Real-world road-testing:
  * Apps using charting
  * Apps using maps

* App size:
  * Remove F# resources in linker, see https://github.com/fsprojects/Elmish.XamarinForms/issues/94

* Performance:
  * Do better list comparison/diffing
  * Perf-test on large lists and do resulting perf work
  * Consider allowing a `ChunkList` tree as input to ListView etc., e.g. `chunks { yield! stablePart; yield newElement; yield! stablePart2 }` 
  * Consider memoize function closure creation
  * Consider using integer atoms for property names
  * Consider keeping a running identity hash on the immutable objects
  * Consider implementing equality and hash on the immutable objects
  * Consider moving 'view' and 'model' computations off the UI thread

* Make some small F# langauge improvements to improve code:
  * Remove `yield` in more cases
  * Automatically save function values that do not capture any arguments
  * Allow a default unnamed argument for `children` so the argument name doesn't have to be given explicitly
  * Allow the use of struct options for optional arguments (to reduce allocations)
  * Implement the C# 5.0 "open static classes" feature in F# to allow the `Xaml.` prefix to be dropped

Bugs:
  * Fix issue for slider where minimum = 1.0, maximum=10.0 (i.e. when value=0 and minimum gets set before maximum?)
  * Fix issue with application reload in AllControls.fs

