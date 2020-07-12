# [Video Transcoder and Converter](https://videotranscode.space/)

[![Netlify Status](https://api.netlify.com/api/v1/badges/ae9bdf66-0d0e-41fd-9ad6-4141e7f86fbf/deploy-status)](https://app.netlify.com/sites/wasm-video-transcoder/deploys)
[![Mozilla-Open-Lab-Etwas](https://circleci.com/gh/Mozilla-Open-Lab-Etwas/Video-Transcoder-Codecs-Formats.svg?style=svg)](https://app.circleci.com/pipelines/github/Mozilla-Open-Lab-Etwas/Video-Transcoder-Codecs-Formats)
![Node.js CI](https://github.com/Mozilla-Open-Lab-Etwas/Video-Transcoder/workflows/Node.js%20CI/badge.svg)

[![Rahul Tarak](https://img.shields.io/badge/Author-Rahul%20Tarak-green)](https://cryogenicplanet.tech/)
[![Rithvik Mahindra](https://img.shields.io/badge/Author-Rithvik%20Mahindra-green)](https://www.linkedin.com/in/rithvik-mahindra/)
[![Zack Radisic](https://img.shields.io/badge/Author-Zack%20Radisic-green)](https://github.com/zackradisic)
[![Arnav Bansal](https://img.shields.io/badge/Author-Arnav%20Bansal-green)](https://github.com/lunaroyster)

A video transcoder and converter built use Web Assembly and FFMPEG to transcode and convert videos right in your browser while protecting your privacy

**This project is still very early in development and only a proof of concept**

## Contributing

We encourage users to submit codecs and formats for review to expand our capabilities using pull requests. Please follow the requirements below and if it passes the automated tests we will add it to our main product in the next build.

### Adding Codecs

**Make sure ffmpeg supports your codec and find the ffmpeg cli command for the codec**

Please add the FFmpeg Docs and FFmpeg cli command in the pull request when adding a new codec

1. Create a new JS file in codecs folder with the name of the codec, please use camelCase
2. Add the required information below in that js file
3. Update the formats folder for each format that the codec supports
4. Submit Pull Request!

```
// Codec Example
module.exports = {
    name: "H.264", // User Facing Name of Codec
    compressionRange: { // FFmpeg Compression Ranges
      min: 1,
      max: 51,
    },
    ffmpegLib: "libx264" // FFmpeg Cli Codec Type
}
```

**If the formats are not updated with codec, they will not be displayed**

```
// Formats Example
module.exports = CODEC_TYPES => ({
    name: "MP4",
    extension: ".mp4",
    display: true,
    defaultCodec: null,
    type: "video/mp4",
    codecs: [CODEC_TYPES.H264, CODEC_TYPES.MPEG4],
    // Add to this list with the newly added Codec Type
})
```
