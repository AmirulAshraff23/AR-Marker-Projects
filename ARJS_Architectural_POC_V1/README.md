# Marker-Based Architectural AR Proof of Concept

A lightweight browser-based starting point using AR.js 3.4.7 and A-Frame 1.6.0.
It uses an AR.js Hiro marker and a simple architectural model built from A-Frame primitives.

## Files

- `index.html` — complete prototype in one file.
- `markers/README.md` — contains the official download link and print instructions for the Hiro marker.
- `models/` — place an optional `.glb` model here later.

## First test on the laptop

1. Open this folder in Visual Studio Code.
2. Start the Live Server extension from `index.html`.
3. Open the localhost URL in Chrome.
4. Allow camera access and point the webcam at the printed Hiro marker.
5. Confirm the model appears, then test Rotate, Size, Reset and Building info.

Do not open the file by double-clicking it (`file://`). Use a local server.

## Test on the Redmi 13C

Camera access on a phone browser requires a secure HTTPS website. A laptop Live Server address on the local network using plain `http://` may not be accepted for camera access.

Recommended quick route: publish the folder using Netlify Drop at https://app.netlify.com/drop . Alternatively, use GitHub Pages. Then open the HTTPS URL in Chrome on the Redmi 13C, grant camera permission, and scan the marker.

## Marker print

Download the official Hiro marker from https://raw.githubusercontent.com/AR-js-org/AR.js/master/data/images/hiro.png and print it as a square, approximately 16 cm x 16 cm, with the complete black border visible. Keep it flat and use bright, even lighting. The `size="0.16"` marker attribute in `index.html` means the outer black marker square is 16 cm wide. Measure the black square after printing. If it is a different width, change the value to that width in metres (for example, 0.14 for 14 cm).

## Optional custom pattern marker

Use the AR.js marker generator: https://ar-js-org.github.io/AR.js/three.js/examples/marker-training/examples/generator.html . Upload a high-contrast, simple image and download both the marker image and `.patt` file. Put the `.patt` file in `markers/`, then replace the Hiro marker element in `index.html` with:

```html
<a-marker id="hiro-marker" type="pattern" url="markers/your-marker.patt" size="0.16" emitevents="true">
  <!-- keep the building entity here -->
</a-marker>
```

Also print the generated marker image at 16 cm square. The actual outer marker width must match the `size` in metres.

## Optional GLB model

A-Frame supports glTF 2.0 `.glb` files. Put a lightweight model in `models/` and replace the primitive building contents with an entity such as:

```html
<a-entity gltf-model="url(models/building.glb)" scale="0.03 0.03 0.03" position="0 0 0"></a-entity>
```

Adjust scale and position after testing. Keep the model small and use a licence that permits your intended use. Record the model source and licence in your paper.

## Important research integrity note

This is a prototype demonstration, not a validated production framework. Only report features you actually test. Do not claim user evaluation, accuracy, frame rates, usability scores or performance measurements unless you collect those data using a stated procedure.
