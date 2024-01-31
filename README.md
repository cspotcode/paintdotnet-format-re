# paintdotnet-format-re

It would be nice to extract PDN layers as separate images from CLI or other pipeline.

Took a look at this for a few minutes, writing down what I found:

ILSpy shows PaintDotNet.Data assembly contains `Document` class, appears to be the class that marshalls into a .pdn file.

Has `FromStream` / `SaveToStream` methods which appear to do the marshalling.

In theory, can write some C# that links against the PaintDotNet.Data assembly, uses `FromStream` to read .pdn, then uses `.layers.GetAt()` to get all layers and emit as pngs.
