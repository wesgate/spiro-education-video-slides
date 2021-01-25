<template>
  <div class="slideshow-wrap">
    <v-idle
      :duration="300"
      :events="idle.events"
      @idle="onidle"
    />
    <div class="multiple-slides">
      <vueper-slides
        ref="vueperslides1"
        :slide-ratio="1 / 2"
        :bullets="false"
        :autoplay="false"
        @slide="$refs.vueperslides2 && $refs.vueperslides2.goToSlide($event.currentSlide.index, { emit: false })"
      >
        <vueper-slide
          v-for="(slide, i) in slides"
          :key="i"
          :image="slide.image"
          :video="slide.video"
        />
      </vueper-slides>

      <vueper-slides
        ref="vueperslides2"
        :slide-ratio="1 / 8"
        :dragging-distance="50"
        :visible-slides="6"
        fixed-height="100px"
        :gap="1"
        @slide="$refs.vueperslides1 && $refs.vueperslides1.goToSlide($event.currentSlide.index, { emit: false })"
      >
        <vueper-slide
          v-for="(slide, i) in slides"
          :key="i"
          :title="slide.title"
          :content="slide.content"
          @click.native="$refs.vueperslides2 && $refs.vueperslides2.goToSlide(i)"
        >
          <template #content>
            <div class="vueperslide__content-wrapper">
              <div class="vueperslide__title">
                {{ slide.title.toString() }}
              </div>
              <div class="vueperslide__content">
                {{ slide.content.toString() }}
              </div>
            </div>
          </template>
        </vueper-slide>
      </vueper-slides>
    </div>
  </div>
</template>

<script>
import { VueperSlides, VueperSlide } from 'vueperslides'
export default {
  components: {
    VueperSlides,
    VueperSlide
  },
  data () {
    return {
      idle: {
        events: [
          'mousemove',
          'keypress',
          'click'
        ]
      },
      slides: [
        {
          title: 'Spiro',
          content: 'Spiro Video.',
          image: 'https://i.ytimg.com/vi_webp/ehJg_OlcjpE/maxresdefault.webp',
          video: {
            mp4: require('@/assets/video/spiro.mp4'),
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: 'https://i.ytimg.com/vi_webp/ehJg_OlcjpE/maxresdefault.webp',
              autoplay: true
            }
          }
        },
        {
          title: 'Cohokia',
          content: 'Cohokia video.',
          video: {
            mp4: require('@/assets/video/cohokia.mp4'),
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: 'https://i.ytimg.com/vi_webp/ehJg_OlcjpE/maxresdefault.webp',
              autoplay: false
            }
          }
        },
        {
          title: 'Etowah',
          content: 'Etowah video.',
          video: {
            mp4: require('@/assets/video/etowah.mp4'),
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: 'https://i.ytimg.com/vi_webp/ehJg_OlcjpE/maxresdefault.webp',
              autoplay: false
            }
          }
        },
        {
          title: 'Kincaid',
          content: 'Kincaid video.',
          video: {
            mp4: require('@/assets/video/kincaid.mp4'),
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: 'https://i.ytimg.com/vi_webp/ehJg_OlcjpE/maxresdefault.webp'
            }
          }
        },
        {
          title: 'Mississippian',
          content: 'Mississippian video.',
          video: {
            mp4: require('@/assets/video/mississippian.mp4'),
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: 'https://i.ytimg.com/vi_webp/ehJg_OlcjpE/maxresdefault.webp'
            }
          }
        },
        {
          title: 'Moundville',
          content: 'Moundville video.',
          video: {
            mp4: require('@/assets/video/moundville.mp4'),
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: 'https://i.ytimg.com/vi_webp/ehJg_OlcjpE/maxresdefault.webp'
            }
          }
        }
      ]
    }
  },
  methods: {
    onidle () {
      this.$router.push('/')
    }
  }
}
</script>

<style>

.v-idle {
    display: none;
}

.slideshow-wrap {
  @apply text-center mx-auto w-full bg-red;
}

.vueperslide video {
  width: 1600px;
  margin: 0 auto;
  margin-top: 50px;
}

.vueperslide .vueperslide__content-wrapper {
  -webkit-transform: scale(.9);
  transform: scale(.9);
  -webkit-transition: .3s ease-in-out;
  transition: .3s ease-in-out;
  opacity: .4;
  -webkit-filter: blur(1px);
  filter: blur(1px);
}

.vueperslide.vueperslide--active .vueperslide__content-wrapper {
  -webkit-transform: scale(1.1,1.2);
  transform: scale(1.1,1.2);
  -webkit-box-shadow: 0 0 6px rgba(0,0,0,.3);
  box-shadow: 0 0 6px rgba(0,0,0,.3);
  opacity: 1;
  -webkit-filter: blur(0);
  filter: blur(0);
}

video::-webkit-media-controls-panel {
   display: flex !important;
   opacity: 1 !important;
}

</style>
