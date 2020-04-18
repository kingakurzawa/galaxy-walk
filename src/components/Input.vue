<template>
  <div class="inputWrapper">
     <div class='search'>
      <input
        id='search'
        name='search'
        :class="{ dark: dark}"
        :value="value"
        @input="handleChange"
      />
    </div>
  </div>
</template>

<script>

export default {
  name: 'Input',
  props: {
    value: {
      type: String,
      required: true,
    },
    dark: {
      type: Boolean,
      default: false,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>
<style lang='scss'>
.inputWrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-top: 10rem;
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
      box-shadow: 0 1.5rem 1.5rem -1rem #f40c0c76;
    }
    .dark {
      color: #243933;
      border-bottom-color: #243933;
    }
    .dark:focus {
        box-shadow: 0 1.5rem 1.5rem -1rem rgba(#243933, .3);
      }
  }
  @media (min-width:768px) {
    .search {
      width: 24rem;
    }
  }
</style>
