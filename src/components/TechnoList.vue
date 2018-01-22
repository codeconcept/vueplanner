<template>
    <div>
        <techno v-bind:techno="techno" v-for="techno in technos" v-bind:key="techno._id"></techno>
    </div>
</template>

<script>
import Techno from "./Techno.vue";

export default {
  name: "TechnoList",
  props: ["technos"],
  components: {
    techno: Techno
  }
};
</script>

<style scoped>
.techno-details {
  border: 3px solid rgb(141, 214, 30);
  margin: 10px 5px;
  padding: 13px 10px;
}
</style>
