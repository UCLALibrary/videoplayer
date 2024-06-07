<template>
  <main class="app">
    <h1>{{ title }}</h1>

    <p v-if="streamBaseUrl">
      To view this media, you must connect from the UCLA campus or via
      <a
        href="https://www.it.ucla.edu/it-support-center/services/virtual-private-network-vpn-clients"
        >the UCLA VPN</a
      >
    </p>

    <div v-if="streamBaseUrl" class="video-js-container">
      <div class="video-player">
        <video
          ref="videoPlayer"
          class="video-js vjs-big-play-centered"
          poster="https://static.library.ucla.edu/video_icon.svg"
        ></video>
      </div>
    </div>
    <p v-else>
      <strong>Invalid URL:</strong> Please provide a valid URL with a <code>src</code> query
      parameter containing a video stream URL.
    </p>
  </main>
</template>

<script>
import videojs from 'video.js'
import 'video.js/dist/video-js.css'

export default {
  name: 'VideoPlayer',
  computed: {
    options() {
      return {
        autoplay: false,
        controls: true,
        fill: true,
        sources: this.sources
      }
    },
    sources() {
      if (/(Apple|iOS)/.test(navigator.userAgent)) {
        return [
          {
            src: this.streamBaseUrl + '/manifest.mpd',
            // "type": "Video",
            type: 'application/dash+xml'
          }
        ]
      } else {
        return [
          {
            src: this.streamBaseUrl + '/playlist.m3u8',
            type: 'application/vnd.apple.mpegurl'
          }
        ]
      }
    },
    streamBaseUrl() {
      return (
        this.urlParams?.get('src') ||
        ''
          ?.replace(/manifest.mpd$/, '')
          ?.replace(/playlist.m3u8$/, '')
          ?.replace(/\/$/, '')
      )
    },
    title() {
      return this.urlParams.get('title') || 'Video Player'
    },
    urlParams() {
      return new URLSearchParams(window.location.search)
    }
  },
  mounted() {
    this.player = videojs(this.$refs.videoPlayer, this.options)
  },
  beforeUnmount() {
    if (this.player) {
      this.player.dispose()
    }
  }
}
</script>

<style scoped>
.app {
  /* --video-width: min(1920px, 98vw);
  --video-height: calc(var(--video-width) * 1080 / 1920);

  width: var(--video-width); */
  width: 98vw;
  height: 98vh;
  margin: auto;

  display: flex;
  flex-direction: column;
}

h1 {
  font-family: 'Helvetica', sans-serif;
  color: #333;
  box-sizing: border-box;
  font-weight: 500;
  line-height: 1.2;
  font-size: 1.75rem;
  flex-grow: 0;
}

p {
  flex-grow: 0;
}

.video-js-container {
  flex-grow: 1;
}

.video-player {
  --video-height: min(100%, 98vw * 1080 / 1920);
  width: calc(var(--video-height) * 1920 / 1080);
  height: var(--video-height);
}
</style>
