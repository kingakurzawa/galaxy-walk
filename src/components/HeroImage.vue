<template>
  <div class="heroImage" />
</template>
<script>
export default {
  name: 'HeroImage',
};
</script>
<style lang="scss" scoped>
.heroImage {
    position: fixed;
    top: 0;
    z-index: -1;
    width: 100%;
    height: 100vh;
    background-image: url('../assets/nasa.large.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 50% 100%;
}
.heroImage::after {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  z-index: 1;
  width: 100%;
  height: 100vh;
  background: rgba(0, 0, 0, 0.406);
}
</style>
