<template>
  <div :class="[{startPosition: state === 1},'wrapper']">
    <transition name="slide">
    <img src="@/assets/logo.png" class="logo" v-if="state === 1">
    </transition>
    <transition name="fade">
      <HeroImage v-if="state === 0" />
    </transition>
    <Claim v-if="state === 0" />
    <Input v-model="searchValue" @input="handleInput" :dark="state === 1"/>
    <div class="results" v-if="results && !loading && state === 1">
      <Item v-for="item in results"
      :item="item"
      :key="item.data[0].nasa_id"
      @click.native="handleModalOpen(item)"/>
    </div>
    <Modal v-if="modalOpen" :item="modalItem" @closeModal="modalOpen = false"/>
  </div>
</template>
<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import Input from '@/components/Input.vue';
import HeroImage from '@/components/HeroImage.vue';
import Item from '@/components/Item.vue';
import Modal from '@/components/Modal.vue';

const API = 'https://images-api.nasa.gov/search';
export default {
  name: 'App',
  components: {
    Claim, Input, HeroImage, Item, Modal,
  },
  data() {
    return {
      modalItem: null,
      modalOpen: false,
      state: 0,
      loading: false,
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleModalOpen(item) {
      this.modalOpen = true;
      this.modalItem = item;
    },
    handleInput: debounce(function deb() {
      this.loading = true;
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
          this.loading = false;
          this.state = 1;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 1000),
  },
};
</script>

<style lang="scss">
  * {
    box-sizing: border-box;
    font-family: fantasy;
    font-size: 10px;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #fff;
  }
  body {
    margin: 0;
    padding: 0;
  }
  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s ease;
  }
  .fade-enter, .fade-leave-to {
    opacity: 0;
  }
  .slide-enter-active, .slide-leave-active {
    transition: margin-top .5s ease;
  }
  .slide-enter, .slide-leave-to {
    margin-top: -5rem;
  }
  .wrapper {
    position: relative;
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    margin: 0;
    width: 100%;
    height: 100vh;
   &.startPosition {
      justify-content: flex-start;
    }
    .logo {
      position: absolute;
      top: 4rem;
      width: 6rem;
    }
    .results {
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-gap: 2rem;
      margin-top: 5rem;

      @media(min-width:768px) {
        grid-template-columns: 1fr 1fr 1fr;
      }
    }
  }
  @media (min-width:768px) {
    .wrapper {
      justify-content: center;
    }
  }
</style>
