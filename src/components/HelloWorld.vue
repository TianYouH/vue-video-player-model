<template>
  <div class="item">
    <div class="player">
      <video-player 
				class="vjs-custom-skin"
				ref="videoPlayer"
				:options="playerOptions"
				:playsinline="true"
				:events="['fullscreenchange']"
				@play="onPlayerPlay($event)"
				@pause="onPlayerPause($event)"
				@ended="onPlayerEnded($event)"
				@loadeddata="onPlayerLoadeddata($event)"
				@waiting="onPlayerWaiting($event)"
				@playing="onPlayerPlaying($event)"
				@timeupdate="onPlayerTimeupdate($event)"
				@canplay="onPlayerCanplay($event)"
				@canplaythrough="onPlayerCanplaythrough($event)"
				@ready="playerReadied"
				@statechanged="playerStateChanged($event)"
				@fullscreenchange="onPlayerFullScreenchange($event)"
			>
      </video-player>
    </div>
  </div>
</template>

<script>
// custom skin css

export default {
  data() {
    return {
      // videojs options
      playerOptions: {
        height: '360',
        autoplay: true,
        muted: true,
        language: 'en',
        playbackRates: [0.7, 1.0, 1.5, 2.0],
        sources: [{
          type: "video/mp4",
          src: "http://vjs.zencdn.net/v/oceans.mp4",
        }],
        poster: "https://surmon-china.github.io/vue-quill-editor/static/images/surmon-1.jpg",
      }
    }
  },
  mounted() {
    setTimeout(() => {
      console.log('dynamic change options', this.player)

      this.player.muted(false)
    }, 5000)
  },
  computed: {
    player() {
      return this.$refs.videoPlayer.player
    }
  },
  methods: {
    // listen event
    onPlayerPlay(player) {
      // console.log('player 开始!', player)
    },
    onPlayerPause(player) {
      // console.log('player 暂停!', player)
    },
    onPlayerEnded(player) {
      console.log('player ended!', player)
    },
    onPlayerLoadeddata(player) {
      console.log('player Loadeddata!', player)
    },
    onPlayerWaiting(player) {
      console.log('player Waiting!', player)
    },
    onPlayerPlaying(player) {
      console.log('player Playing!', player)
    },
    onPlayerTimeupdate(player) {
      // console.log('player 时间更新!', player.currentTime())
    },
    onPlayerCanplay(player) {
      console.log('player Canplay!', player)
    },
    onPlayerCanplaythrough(player) {
      console.log('player Canplaythrough!', player)
    },

    // 监听状态事件
    playerStateChanged(playerCurrentState) {
      // console.log('player 状态更新', playerCurrentState)
    },

    // player is ready
    playerReadied(player) {
      // seek to 10s
      console.log('example player 1 readied', player)
      player.currentTime(10)
      // console.log('example 01: the player is readied', player)
		},
		onPlayerFullScreenchange(e) {
			console.log('player 全屏' , e)
		}
  }
}
</script>