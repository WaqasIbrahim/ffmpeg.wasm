## Dockerfile.joiner
Can only be used to join mp4 + m4a (aac) files for youtube using copy. Single threaded because multithreading is slow in case of copy.
```ts
await ffmpeg.exec([
    '-i', 'video.mp4',
    '-i', 'audio.m4a',
    '-map', '0:v',
    '-map', '1:a',
    '-c:v', 'copy',
    '-c:a', 'copy',
    '-movflags', 'faststart',
    '-shortest',
    '-fflags', '+genpts',
    'output.mp4'
]);
```