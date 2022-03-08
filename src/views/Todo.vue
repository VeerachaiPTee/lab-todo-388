<template>
  <v-container class="box">
    <Addwork title="Homework / Asssignment" color="white" />
  </v-container>
</template>

<script>
import Addwork from "../components/Addwork.vue";
export default {
  name: "Todo",
  components: {
    Addwork,
  },
};
</script>

<style></style>
