<template>
  <div class="outer">
    <div class="inner">
      <div class="photo">
        <img :src="photo"/>
      </div>
      <div class="about">
        <h2 class="title">{{title}}</h2>
        <p class="description">{{description}}</p>
      </div>
    </div>
    <div class="exit" @click="$emit('closeModal')"></div>
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      photo: null,
      title: null,
      description: null,
    };
  },
  mounted() {
    this.photo = this.item.links[0].href;
    this.title = this.item.data[0].title;
    this.description = this.item.data[0].description.substring(0, 100);
  },
};
</script>

<style lang='scss' scoped>
  .outer {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: #fff;
    @media(min-width:1024px){
      max-width: 70%;
      height: 60%;
      left: 0;
      right: 0;
      top: 0;
      bottom: 0;
      margin: auto;
      box-shadow: 0 3rem 3rem -1rem rgba(0,0,0, .4);
    }
  }

  .inner {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    height: 100%;
    padding: 5rem;

    @media(min-width:1024px){
      flex-direction: row;
        .photo {
          min-width: 50%;
          margin-right: 2rem;
        }
    }
    .photo {
      width: 50%;
      height: auto;
      background: #000;
      img {
        width: 80%;
      }
    }
    .description, .title {
      color: rgb(38, 13, 13);
    }
    .title {
      font-size: 2rem;
    }
    .description {
      font-size: 1.6rem;
    }
  }
  .exit {
    position: absolute;
    right: 0;
    top: 0;
    width: 3rem;
    height: 3rem;
    cursor: pointer;

    &::before, &::after {
      position: absolute;
      content: '';
      top: 3rem;
      right: 2rem;
      display: block;
      width: 2rem;
      height: .2rem;
      background: #000;
    }
    &::before {
      transform: rotate(45deg);
      padding: .2rem;
    }
     &::after {
      transform: rotate(-45deg);
      padding: .2rem;
    }
  }

</style>
