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
      border: 0;
      border-bottom: .1rem solid #fff;
      background: none;
    }
  }
</style>
