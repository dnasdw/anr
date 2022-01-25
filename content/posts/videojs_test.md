---
slug: "video.js test"
title: "Videojs_test"
summary: "video.js test"
authors: [dnasdw]
date: 2022-01-25T23:17:39+08:00
draft: false
---

<html>
    <head>
        <link href="https://unpkg.com/video.js@7.10.2/dist/video-js.min.css" rel="stylesheet">
        <script src="https://unpkg.com/video.js@7.10.2/dist/video.min.js"></script>
        <script src="https://unpkg.com/video.js@7.10.2/dist/lang/zh-Hans.js"></script>
        <style type="text/css">
            .video-js .vjs-time-control{display:block;}
            .video-js .vjs-remaining-time{display: none;}
        </style>
    </head>
    <body>
        <video-js id=vid1 width=600 height=300 class="vjs-default-skin" controls>
          <source
             src="https://storage.googleapis.com/shaka-demo-assets/angel-one-hls/hls.m3u8"
             type="application/x-mpegURL">
        </video-js>
        <script src="https://unpkg.com/@videojs/http-streaming@2.13.1/dist/videojs-http-streaming.js"></script>
        <script>
            var player = videojs('vid1', {
                language: 'zh-Hans',
                playbackRates: [0.50, 0.75, 1.00, 1.25, 1.50, 1.75, 2.00]
            });
            player.play();
        </script>
    </body>
</html>
