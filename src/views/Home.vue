<template>
  <div class="home">
    <Denomination />
  </div>
</template>

<script>
import Denomination from "./Denomination.vue";

export default {
  name: "Home",
  components: {
    Denomination,
  },
};
</script>

<style scoped>
body {
  overflow-y: hidden;
  overflow-x: hidden;
}
</style>
