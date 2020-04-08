/* eslint-disable max-len */
<template>
  <div class="inputWrapper">
     <div class='search'>
      <input
        id='search'
        name='search'
        v-model="searchValue"
        @input="handlerInput"
      />
      <ul>
        <li v-for='item in results' :key='item.data[0].nasa_id'>
          <p> {{ item.data[0].description }} </p>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  name: 'Input',
};
</script>
<style lang='scss' scoped>
.inputWrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 5rem;
}
.search {
    display: flex;
    flex-direction: column;
    width: 300px;
    label {
      font-family: fantasy
    }
    input {
      height: 30px;
      border: 0;
      border-bottom: 1px solid black;
    }
  }
</style>
