<template>
  <div class="claimWrapper">
    <h1 class="claim" >Galaxy Walk</h1>
    <p class="subclaim" >“The real voyage
      of discovery consists not in seeking new
      landscapes but in having new eyes.”
      <span>~ Marcel Proust ~</span>
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
  font-size: 5rem;
}
.subclaim {
  display: flex;
  flex-direction: column;
  margin: 2rem;
  font-size: 1.8rem;
  span {
    align-self: flex-end;
    font-size: 1.4rem;
  }
}
  @media (min-width:768px) {
    .claimWrapper {
      width: 80%;
    }
    .claim {
      font-size: 7rem;
    }
    .subclaim {
      font-size: 2.2rem;
      span {
        align-self: flex-end;
        margin-top: 1rem;
        font-size: 1.5rem;
      }
    }
  }
  @media (min-width:768px) {
    .claimWrapper {
      width: 60%;
    }
    .subclaim:first-of-type {
      margin-top: 10rem;
    }
  }
</style>
