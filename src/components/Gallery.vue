<template>
  <div class="gallery">
      <VueSlickCarousel v-bind="settings">
        <slot></slot>
      </VueSlickCarousel>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'

export default {
  name: 'Gallery',
  components: {
    VueSlickCarousel
  },
  data() {
    return {
      settings: {
        infinite: true,
        slidesToShow: 4
      },
    }
  }
}
</script>

<style lang="scss">
.gallery {
  padding: 35px 30px;

  .slick-arrow {
    position: absolute;
    top: 50%;
    display: block;
    width: 58px;
    height: 58px;
    padding: 0;
    transform: translate(0, -50%);
    border: 1px solid #ececec;
    border-radius: 100%;
    outline: none;
    background-color: #fff;
    font-size: 0;
    line-height: 0;
    cursor: pointer;
    color: transparent;
    z-index: 1;

    &:before {
      content: '';
      display: inline-block;
      width: 12px;
      height: 12px;
      border-right: 3px solid #b4b4b4;
      border-bottom: 3px solid #b4b4b4;
    }
  }

  .slick-prev {
    left: -25px;

    &:before {
      margin-left: 6px;
      transform: rotate(-225deg);
    }
  }

  .slick-next {
    right: -25px;

    &:before {
      margin-right: 6px;
      transform: rotate(-45deg);
    }
  }

  .slick-slide {
    a {
      outline: none;
      
      img {
        margin: auto;
      }
    }
  }
}
</style>
