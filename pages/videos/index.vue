<template>
  <div class="slideshow-wrap">
    <v-idle
      :duration="210"
      :events="idle.events"
      @idle="onidle"
    />
    <div class="multiple-slides">
      <vueper-slides
        ref="vueperslides1"
        :slide-ratio="1 / 2"
        :bullets="false"
        :autoplay="false"
        fixed-height="90vh"
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
        class="nav-slides"
        :slide-ratio="1 / 8"
        :dragging-distance="50"
        :visible-slides="6"
        fixed-height="10vh"
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
              <div class="icon text-xs border-2 border-orange border border-solid rounded-full h-8 w-8 flex justify-center items-center text-center">
                <font-awesome-icon class="fa-fw" icon="play" />
              </div>
              <div class="vueperslide__title text-xl mb-0 uppercase font-bold">
                {{ slide.title.toString() }}
              </div>
              <div class="vueperslide__content text-sm">
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
          title: 'Introduction',
          content: '1:20',
          image: require('@/assets/images/1-bg.png'),
          video: {
            mp4: 'https://ncm-touch-screen.s3.amazonaws.com/spiro-education-videos/01-Introduction.mp4',
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: require('@/assets/images/1-bg.jpg'),
              autoplay: true
            }
          }
        },
        {
          title: 'Getting Started',
          content: '1:29',
          image: require('@/assets/images/1-bg.png'),
          video: {
            mp4: 'https://ncm-touch-screen.s3.amazonaws.com/spiro-education-videos/02-Getting-Started.mp4',
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: require('@/assets/images/1-bg.jpg'),
              autoplay: false
            }
          }
        },
        {
          title: 'Digging up the Past',
          content: '2:10',
          image: require('@/assets/images/1-bg.png'),
          video: {
            mp4: 'https://ncm-touch-screen.s3.amazonaws.com/spiro-education-videos/03-Digging-Up-The-Past.mp4',
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: require('@/assets/images/1-bg.jpg'),
              autoplay: false
            }
          }
        },
        {
          title: 'City of the Sun',
          content: '2:27',
          image: require('@/assets/images/1-bg.png'),
          video: {
            mp4: 'https://ncm-touch-screen.s3.amazonaws.com/spiro-education-videos/04-City-of-the-Sun.mp4',
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: require('@/assets/images/1-bg.jpg')
            }
          }
        },
        {
          title: 'America Before Columbus',
          content: '1:25',
          image: require('@/assets/images/1-bg.png'),
          video: {
            mp4: 'https://ncm-touch-screen.s3.amazonaws.com/spiro-education-videos/05-America-Before-Columbus.mp4',
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: require('@/assets/images/1-bg.jpg')
            }
          }
        },
        {
          title: 'Anchient-Architects',
          content: '1:32',
          image: require('@/assets/images/1-bg.png'),
          video: {
            mp4: 'https://ncm-touch-screen.s3.amazonaws.com/spiro-education-videos/06-Ancient-Architects.mp4',
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: require('@/assets/images/1-bg.jpg')
            }
          }
        },
        {
          title: 'Cahokia Day by Day',
          content: '2:17',
          image: require('@/assets/images/1-bg.png'),
          video: {
            mp4: 'https://ncm-touch-screen.s3.amazonaws.com/spiro-education-videos/07-Cahokia-Day-By-Day.mp4',
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: require('@/assets/images/1-bg.jpg')
            }
          }
        },
        {
          title: 'Supernaturals & the Cosmos',
          content: '2:43',
          image: require('@/assets/images/1-bg.png'),
          video: {
            mp4: 'https://ncm-touch-screen.s3.amazonaws.com/spiro-education-videos/08-Supernaturals-and-the-Cosmos.mp4',
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: require('@/assets/images/1-bg.jpg')
            }
          }
        },
        {
          title: 'Conclusion',
          content: '0:50',
          image: require('@/assets/images/1-bg.png'),
          video: {
            mp4: 'https://ncm-touch-screen.s3.amazonaws.com/spiro-education-videos/09-Conclusion.mp4',
            props: {
              controls: true,
              controlsList: 'nodownload nofullscreen',
              disablePictureInPicture: true,
              poster: require('@/assets/images/1-bg.jpg')
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
  @apply text-center mx-auto w-full bg-navy;
}

.vueperslide video {
  width: 1100px;
  margin: 0 auto;
  margin-top: 50px;
}

.vueperslide .vueperslide__content-wrapper {
  -webkit-transform: scale(.75);
  transform: scale(.75);
  -webkit-transition: .3s ease-in-out;
  transition: .3s ease-in-out;
  opacity: .4;
}

.nav-slides {
  @apply bg-red;
}

.nav-slides .vueperslide {
  @apply bg-red text-orange;
}

.nav-slides .vueperslide.vueperslide--active {
  @apply bg-navy border-b-4 border-orange border-solid;
}

.vueperslide.vueperslide--active .vueperslide__content-wrapper {
  box-shadow: none !important;
}

.vueperslide.vueperslide--active .vueperslide__content-wrapper .icon {
  display: none;
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
