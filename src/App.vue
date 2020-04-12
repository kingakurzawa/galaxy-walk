<template>
  <div class='wrapper'>
    <HeroImage v-if="state === 0" />
    <Claim v-if="state === 0" />
    <Input v-model="searchValue" @input="handleInput" />
  </div>
</template>
<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import Input from '@/components/Input.vue';
import HeroImage from '@/components/HeroImage.vue';

const API = 'https://images-api.nasa.gov/search';
export default {
  name: 'App',
  components: { Claim, Input, HeroImage },
  data() {
    return {
      state: 0,
      loading: false,
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handleInput: debounce(function deb() {
      console.log(this.searchValue);
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
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
  .wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
    margin: 0;
    width: 100%;
    height: 100vh;
  }
  @media (min-width:768px) {
    .wrapper {
      justify-content: center;
    }
  }
</style>
