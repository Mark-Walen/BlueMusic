<template>
  <div class="swiper">
    <div v-swiper:mySwiper="swiperOption" ref="swiper">
      <div class="swiper-slide" v-for="banner in banners" :key="banner.bannerId">
        <a :herf="banner.url">
          <img :src="banner.pic" />
          <span :style="titleStyle(banner.titleColor)" class="title">{{ banner.typeTitle }}</span>
        </a>
      </div>
    </div>
  </div>
</template>

<script>

// import style (<= Swiper 5.x)
import 'swiper/css/swiper.css'
import {
  directive, Swiper
} from "vue-awesome-swiper";

export default {
  name: 'Swiper',
  props: {
    banners: {
      type: Array,
      default: null
    }
  },
  data () {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        }
      }
    }
  },
  mounted() {
    this._initSwiper();
  },
  methods: {
    titleStyle(color) {
      if (color === 'red') {
        return {
          '--title-color': '#f01414'
        }
      }
      return {
        '--title-color': '#3C8FD2'
      }
    },
    _initSwiper () {
      this.mySwiper = new Swiper(this.$refs.swiper, {
        autoplay: true,
        direction: 'horizontal'
      })
    }
  },
  directives: {
    swiper: directive
  }
}
</script>

<style scoped>
.title {
  color: #fff;
  background: var(--title-color);
}
</style>
