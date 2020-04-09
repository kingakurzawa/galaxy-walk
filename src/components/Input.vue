<template>
  <div class="inputWrapper">
     <div class='search'>
      <input
        id='search'
        name='search'
        v-model="searchValue"
        @input="handlerInput"
      />
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
}
.search {
    display: flex;
    flex-direction: column;
    width: 14rem;
    input {
      height: 3rem;
      color: #fff;
      font-family: fantasy;
      font-weight: bolder;
      font-size: 2rem;
      font-weight: 500;
      text-align: center;
      border: 0;
      border-bottom: .1rem dashed #fff;
      background: none;
      outline: none;
    }
    input:focus {
      box-shadow: 0 15px 15px -10px #f40c0c76;
    }
  }
</style>
