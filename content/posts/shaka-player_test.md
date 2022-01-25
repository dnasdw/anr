---
slug: "shaka-player test"
title: "Shaka Player_test"
summary: "shaka-player test"
authors: [dnasdw]
date: 2022-01-25T23:44:19+08:00
draft: false
---

<!DOCTYPE html>
<html>
  <head>
    <!-- Shaka Player ui compiled library: -->
    <script src="https://cdn.jsdelivr.net/npm/shaka-player@3.3.0/dist/shaka-player.ui.js"></script>
    <!-- Shaka Player ui compiled library default CSS: -->
    <link rel="stylesheet" type="text/css" href="https://cdn.jsdelivr.net/npm/shaka-player@3.3.0/dist/controls.css">
    <!-- Chromecast SDK (if you want Chromecast support for your app): -->
    <!-- <script defer src="https://www.gstatic.com/cv/js/sender/v1/cast_sender.js"></script> -->
    <!-- Your application source: -->
    <!-- <script src="myapp.js"></script> -->
    <script>
        const manifestUri =
            'https://storage.googleapis.com/shaka-demo-assets/angel-one-hls/hls.m3u8';
            async function init() {
                // When using the UI, the player is made automatically by the UI object.
                const video = document.getElementById('video');
                const ui = video['ui'];
                const config = {
                    'seekBarColors': {
                        base: 'rgba(255, 0, 0, 0.3)',
                        buffered: 'rgba(0, 0, 255, 0.54)',
                        played: 'rgb(0, 255, 0)',
                    },
                    // 'customContextMenu' : true,
                    // 'contextMenuElements' : ['statistics'],
                    'overflowMenuButtons' : ['statistics'],
                    'enableTooltips' : true,
                    'controlPanelElements': ['play_pause', 'time_and_duration', 'picture_in_picture', 'loop', 'spacer', 'language', 'captions', 'playback_rate', 'quality', 'mute', 'volume', 'fullscreen', 'overflow_menu']
                };
                ui.configure(config);
                const controls = ui.getControls();
                const player = controls.getPlayer();
                // Attach player and ui to the window to make it easy to access in the JS console.
                window.player = player;
                window.ui = ui;
                // Listen for error events.
                player.addEventListener('error', onPlayerErrorEvent);
                controls.addEventListener('error', onUIErrorEvent);
                // Try to load a manifest.
                // This is an asynchronous process.
                try {
                    await player.load(manifestUri);
                    // This runs if the asynchronous load is successful.
                    console.log('The video has now been loaded!');
                } catch (error) {
                    onPlayerError(error);
                }
            }
            function onPlayerErrorEvent(errorEvent) {
                // Extract the shaka.util.Error object from the event.
                onPlayerError(event.detail);
            }
            function onPlayerError(error) {
                // Handle player error
                console.error('Error code', error.code, 'object', error);
            }
            function onUIErrorEvent(errorEvent) {
                // Extract the shaka.util.Error object from the event.
                onPlayerError(event.detail);
            }
            function initFailed(errorEvent) {
                // Handle the failure to load; errorEvent.detail.reasonCode has a
                // shaka.ui.FailReasonCode describing why.
                console.error('Unable to load the UI library!');
            }
            // Listen to the custom shaka-ui-loaded event, to wait until the UI is loaded.
            document.addEventListener('shaka-ui-loaded', init);
            // Listen to the custom shaka-ui-load-failed event, in case Shaka Player fails
            // to load (e.g. due to lack of browser support).
            document.addEventListener('shaka-ui-load-failed', initFailed);
    </script>
  </head>
  <body>
    <!-- The data-shaka-player-container tag will make the UI library place the controls in this div.
         The data-shaka-player-cast-receiver-id tag allows you to provide a Cast Application ID that
           the cast button will cast to; the value provided here is the sample cast receiver. -->
    <div data-shaka-player-container style="max-width:40em"
         data-shaka-player-cast-receiver-id="BBED8D28">
       <!-- The data-shaka-player tag will make the UI library use this video element.
            If no video is provided, the UI will automatically make one inside the container div. -->
      <video autoplay data-shaka-player id="video" style="width:100%;height:100%"></video>
    </div>
  </body>
</html>
