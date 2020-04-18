<template>
  <div class="item" :style="style"/>
</template>

<script>
export default {
  name: 'Item',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      photo: this.item.links[0].href,
      title: this.item.data[0].title,
    };
  },
  computed: {
    style() {
      return `background-image: url("${this.photo}")`;
    },
  },
};
</script>
<style lang='scss' scoped>
  .item {
    height: 10rem;
    width: 40vw;
    background-repeat: no-repeat;
    background-position: 50%;
    background-size: cover;
    @media (min-width:768px) {
      width: 25vw;
      height: 30rem;
    }
  }
</style>
