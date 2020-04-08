/* eslint-disable max-len */
<template>
  <div class="claimWrapper">
    <h1 class="claim" >Galaxy Walk</h1>
    <p class="subclaim" >“The real voyage
      of discovery consists not in seeking new
      landscapes but in having new eyes.”
      ~ Marcel Proust ~
    </p>
    <p class="subclaim" >
        Grab the keyboard and discover the unknown
    </p>
  </div>
</template>

<script>

export default {
  name: 'Claim',
};
</script>
<style lang='scss' scoped>
.claimWrapper {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.claim {
  margin: 0;
  font-size: 3rem;
}
.subclaim {
  margin-top: 2rem;
  font-size: 1.3rem;
}
</style>
