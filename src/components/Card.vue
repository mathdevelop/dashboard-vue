<template>
  <div class="card">
      <div class="title" v-if="title">
          <h3>{{ title }}</h3>
          <a href="#">
            <DragIcon />
          </a>
      </div>
      <div class="slot">
        <slot></slot>
      </div>
  </div>
</template>

<script>
import DragIcon from '@/assets/drag.svg'

export default {
  name: 'Card',
  components: {
    DragIcon
  },
  props: ['title']
}
</script>

<style scoped lang="scss">
.card {
  width: 100%;
  min-height: 260px;
  border-radius: 3px;
  box-shadow: 0px 0px 26px rgba(0, 0, 0, 0.09);
  background-color: #fff;

  .title {
    display: flex;
    justify-content: space-between;
    padding: 15px 30px;
    border-bottom: 1px solid #e2e2e2;

    h3 {
      margin: 0;
      font-family: 'Rubik', sans-serif;
      font-size: 18px;
      line-height: 21px;
      color: #000;
    }
  }

  .slot {
    padding: 15px 30px;
  }
}
</style>
