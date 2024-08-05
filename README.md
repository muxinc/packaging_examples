# packaging_examples

> [!NOTE]
> We routinely archive repositories that were created for talks, blog posts, and articles but haven't received an update in a while. That doesn't mean there's anything wrong with the contents of the repo, just that it might be a little dusty.

Samples files packaged by mux
The files here are an sample files for demonstrating transport stream packaging overhead.
Overhead measured using muxincstreamvalidator found at https://github.com/muxinc/hlstools

# Overhead

`ffmpeg -i tears_of_steel_720p.mp4 -vcodec libx264 -preset faster -x264opts keyint=120:min-keyint=120:scenecut=-1 -b:v 500k -b:a 96k -hls_playlist_type vod ffmpeg/ffmpeg.m3u8`

```
PID 0: SID 00, size 27636, overhead 100.00%
PID 17: SID 00, size 27636, overhead 100.00%
PID 256: SID e0, size 48533516, overhead 6.25%
PID 257: SID c0, size 9579728, overhead 5.38%
PID 4096: SID 00, size 27636, overhead 100.00%
-------------------------------------------------------------
TOTALS: size 58196152, overhead 6.24%
```

# Produced by mux.com

`/mux`

```
/mux
PID 0: SID 00, size 27636, overhead 100.00%
PID 256: SID e0, size 45831204, overhead 2.96%
PID 257: SID c0, size 9443616, overhead 4.51%
PID 4096: SID 00, size 27636, overhead 100.00%
-------------------------------------------------------------
TOTALS: size 55330092, overhead 3.32%
```

# ffmpeg remux
`/remux` contains a repackaging of the files in `/mux` using ffmpeg

`ffmpeg -i ./mux/manifest.m3u8 -codec copy -hls_playlist_type vod remux/remux.m3u8`

```
/remux
PID 0: SID 00, size 27636, overhead 100.00%
PID 17: SID 00, size 27636, overhead 100.00%
PID 256: SID e0, size 47416420, overhead 6.20%
PID 257: SID c0, size 9544008, overhead 5.59%
PID 4096: SID 00, size 27636, overhead 100.00%
-------------------------------------------------------------
TOTALS: size 57043336, overhead 6.24%
```

# I just want to be awesome in space!
Tears of Steel is licensed as Creative Commons Attribution 3.0
https://mango.blender.org


These tools make use of the execlent "Json for Modern C++"
Licensed under MIT and available at https://github.com/nlohmann/json
