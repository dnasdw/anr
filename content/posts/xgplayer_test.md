---
slug: "xgplayer test"
title: "Xgplayer_test"
summary: "xgplayer test"
authors: [dnasdw]
date: 2022-01-26T16:16:44+08:00
draft: false
---

<html>
  <head>
    <meta charset="utf-8">
    <meta name=viewport content="width=device-width,initial-scale=1,maximum-scale=1,minimum-scale=1,user-scalable=no,minimal-ui">
    <meta name="referrer" content="no-referrer">
    <title>xgplayer</title>
    <style type="text/css">
      html, body {width:100%;height:100%;margin:auto;overflow: hidden;}
    </style>
  </head>
  <body>
    <div id="mse"></div>
    <script src="https://cdn.jsdelivr.net/npm/xgplayer/browser/index.js" charset="utf-8"></script>
      <script src="https://cdn.jsdelivr.net/npm/xgplayer-hls.js/browser/index.js" charset="utf-8"></script><script>
      let player = new HlsJsPlayer({
		"id": "mse",
		"url": "https://storage.googleapis.com/shaka-demo-assets/angel-one-hls/hls.m3u8",
		"playsinline": true,
		"whitelist": [
				""
		]
      });
    </script>
  </body>
</html>
