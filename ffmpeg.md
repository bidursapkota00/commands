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
# Show keyframes and timestamps
ffprobe -select_streams v:0 -show_entries frame=best_effort_timestamp_time -of csv=p=0 input.mp4 | awk '{print NR-1 "," $0}' > frame_timestamps.csv

# Cut
ffmpeg -i input.mp4 -ss 0 -to 20.013267 -c copy segment1.mp4
ffmpeg -i input.mp4 -ss 20.013267 -to 32.146156 -c copy segment2.mp4
ffmpeg -i input.mp4 -ss 32.146156 -to 86.756378 -c copy segment3.mp4

# Merge
copy con segments.txt
file 'segment1.mp4'
file 'segment2.mp4'
file 'segment3.mp4'
^Z

ffmpeg -f concat -safe 0 -i segments.txt -c copy output.mp4

# Convert to constant 30fps
ffmpeg -i input.mp4 -r 30 -c:v libx264 -crf 18 -preset slow -c:a copy -movflags +faststart out.mp4
# or -b:a 128k aac instead of copy audio

# With re-encoding
ffmpeg -i input.mp4 -filter_complex "[0:v]select='between(t,0,20)+between(t,20,30)+between(t,30,86)',setpts=N/FRAME_RATE/TB[v]; [0:a]aselect='between(t,0,20)+between(t,20,30)+between(t,30,86)',asetpts=N/SR/TB[a]" -map "[v]" -map "[a]" -c:v libx264 -crf 15 -preset slow -c:a aac -b:a 128k -movflags +faststart output.mp4
```

- **Description:** Cut and merge videos. Input time in seconds.

### Filter audio noise

```bash
# Extract noise sample
ffmpeg -i input.mp4 -ss 00:00:04.021 -to 00:00:04.387 -vn -acodec pcm_s16le noise_sample.wav -y

# Extract full audio
ffmpeg -i input.mp4 -vn -acodec pcm_s16le full_audio.wav -y

# Create noise profile
sox noise_sample.wav -n noiseprof noise.prof

# Remove noise from audio
sox full_audio.wav clean_audio.wav noisered noise.prof 0.21

# Combine clean audio with original video
ffmpeg -i input.mp4 -i clean_audio.wav -c:v copy -c:a aac -map 0:v:0 -map 1:a:0 output.mp4 -y
```

- **Description:** Filter audio noise.
