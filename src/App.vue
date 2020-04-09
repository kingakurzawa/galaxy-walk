<template>
  <div class='wrapper'>
    <HeroImage />
    <Claim />
    <Input />
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
      searchValue: '',
      results: [],
    };
  },
  methods: {
    handlerInput: debounce(function deb() {
      axios.get(`${API}?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
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
    justify-content: center;
    align-items: center;
    margin: 0;
    width: 100%;
    height: 100vh;
  }
</style>
