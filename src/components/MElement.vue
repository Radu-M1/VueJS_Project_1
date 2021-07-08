<template>
  <button class="m-elem" @click="toggleItem(elem.id)">{{ elem.value }}</button>
</template>

<script>
export default {
  name: "MElement",
  props: {
    elem: Object,
  },
  methods: {
    toggleItem(id) {
      this.$emit("toggle-item", id);
    },
  },
};
</script>

<style scoped>
button {
  all: unset;
  user-select: none;
}
.m-elem {
  background-color: #c1f7fe;
  width: 120px;
  height: 100px;
  margin: 5px;
  text-align: center;
  vertical-align: middle;
  line-height: 100px;
  font-size: xxx-large;

}

.m-elem:hover{
  background-color: #90ee90;
}
</style>