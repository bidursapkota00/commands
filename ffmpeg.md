## FFmpeg

### Resize an image to a specific width

```bash
ffmpeg -i input.jpg -vf "scale=WIDTH:-1" output.jpg
```

- **Description:** Resizes the input image to a specified width while maintaining the aspect ratio. Replace `WIDTH` with your desired value (e.g., 800).

### Stack two images vertically

```bash
ffmpeg -i image1.jpg -i image2.jpg -filter_complex "vstack=inputs=2" merged.jpg
```

- **Description:** Vertically stacks two images (`image1.jpg` and `image2.jpg`) and outputs the result to `merged.jpg`.

### Compress an image

```bash
ffmpeg -i merged.jpg -q:v 20 output.jpg
```

- **Description:** Compresses the input image (`merged.jpg`) with a quality factor of 20 and saves the result to `output.jpg`. Lower values indicate higher quality.

### Convert PNG to JPG

```bash
ffmpeg -i input.png output.jpg
```

- **Description:** Converts a PNG image (`input.png`) to a JPG format (`output.jpg`).
