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

### Cut and merge videos

```bash
ffmpeg -i input.mp4 -ss START1 -to END1 -c copy segment1.mp4
ffmpeg -i input.mp4 -ss START2 -to END2 -c copy segment2.mp4

# OR
# Re-encode for perfect sync
ffmpeg -i input.mp4 -ss 0 -to 20 -c:v libx264 -crf 0 -c:a aac -b:a 128k segment1.mp4 -y
ffmpeg -i input.mp4 -ss 20 -to 30 -c:v libx264 -crf 0 -c:a aac -b:a 128k segment2.mp4 -y
ffmpeg -i input.mp4 -ss 30 -to 86 -c:v libx264 -crf 0 -c:a aac -b:a 128k segment3.mp4 -y

copy con segments.txt
file 'segment1.mp4'
file 'segment2.mp4'
file 'segment3.mp4'
^Z

ffmpeg -f concat -safe 0 -i segments.txt -c copy output.mp4


# Selected
ffmpeg -i input.mp4 -filter_complex "[0:v]select='between(t,0,20)+between(t,20,30)+between(t,30,86)',setpts=N/FRAME_RATE/TB[v]; [0:a]aselect='between(t,0,20)+between(t,20,30)+between(t,30,86)',asetpts=N/SR/TB[a]" -map "[v]" -map "[a]" -c:v libx264 -crf 15 -preset slow -c:a aac -b:a 128k -movflags +faststart output.mp4
```

- **Description:** Cut and merge videos. Input time in seconds.
