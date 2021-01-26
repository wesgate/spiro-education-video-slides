<template>
  <div class="bg-red h-screen">
    <video id="videoBG" autoplay muted loop class="h-screen w-screen fixed">
      <source :src="require('@/assets/video/spiro.mp4')" type="video/mp4">
    </video>
    <div class="bg-navy absolute h-screen w-screen opacity-90" />
    <div class="relative h-screen flex items-center justify-center">
      <div class="control-wrapper bg-red w-full p-12 pt-32">
        <Logo />
        <h1 class="text-center text-3xl text-white uppercase tracking-widest mt-8 mb-12">
          Watch Experts Discusss Spiro, the Mississippian World and it's people.
        </h1>
        <h3>
          <nuxt-link class="video-play-button" to="/videos/">
            <span />
          </nuxt-link>
        </h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {}
  }
}
</script>

<style scoped>
.control-wrapper {
  background-image: url('~assets/images/border.jpg');
  background-repeat: repeat-x;
  background-size: 35px;
}

.video-play-button {
  position: absolute;
  z-index: 10;
  top: 78vh;
  left: 50%;
  transform: translateX(-50%) translateY(-50%);
  box-sizing: content-box;
  display: block;
  width: 64px;
  height: 88px;
  /* background: #fa183d; */
  border-radius: 50%;
  padding: 18px 20px 18px 28px;
}

.video-play-button:before {
  @apply bg-orange;
  content: "";
  position: absolute;
  z-index: 0;
  left: 50%;
  top: 50%;
  transform: translateX(-50%) translateY(-50%);
  display: block;
  width: 160px;
  height: 160px;
  border-radius: 50%;
  animation: pulse-border 1500ms ease-out infinite;
}

.video-play-button:after {
  @apply bg-orange;
  content: "";
  position: absolute;
  z-index: 1;
  left: 50%;
  top: 50%;
  transform: translateX(-50%) translateY(-50%);
  display: block;
  width: 160px;
  height: 160px;
  border-radius: 50%;
  transition: all 200ms;
}

.video-play-button span {
  display: block;
  position: relative;
  z-index: 3;
  width: 0;
  height: 0;
  border-left: 64px solid rgba(255, 255, 255, 0.75);
  border-top: 44px solid transparent;
  border-bottom: 44px solid transparent;
}

@keyframes pulse-border {
  0% {
    transform: translateX(-50%) translateY(-50%) translateZ(0) scale(1);
    opacity: 1;
  }
  100% {
    transform: translateX(-50%) translateY(-50%) translateZ(0) scale(1.5);
    opacity: 0;
  }
}
</style>
