<template>
  <div class='wrapper'>
    <Claim />
    <Input />
  </div>
</template>
<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import Input from '@/components/Input.vue';

const API = 'https://images-api.nasa.gov/search';
export default {
  name: 'Home',
  components: { Claim, Input },
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
<style lang="scss" scoped>
  .wrapper {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin: 0;
    padding: 30px;
    width: 100%;
    // background-image: url('../assets/');
  }
</style>
