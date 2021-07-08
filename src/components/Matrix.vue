<template>
  <div class="m-container">
    <div :key="elem.id" v-for="elem in displayArray">
      <MElement @toggle-item="$emit('toggle-item', elem.id)" :elem="elem" />
    </div>
  </div>
</template>



<script>
import MElement from "./MElement";

export default {
  name: "Matrix",
  props: {
    displayArray: Array,
  },
  components: {
    MElement,
  },
  emits: ["toggleItem"],
};
</script>

<style scoped>
.m-container {
  border: 1px solid steelblue;
  padding: 5px;
  border-radius: 5px;
  display: flex;
  margin: 10px auto;
  justify-content: space-evenly;
  flex-wrap: wrap;
  background-color:#fcf3e8;
}
</style>