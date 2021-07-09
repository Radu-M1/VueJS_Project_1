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
  width: 100%;
  margin: 5px auto;
  text-align: center;
  font-size: 3em;
  font-size: 8vw;
  aspect-ratio: auto 4/3;
}

@media screen and (min-width: 730px) {
  .m-elem {
     font-size: 60px;
  }
}

.m-elem:hover {
  background-color: #90ee90;
  cursor: pointer;
}
</style>