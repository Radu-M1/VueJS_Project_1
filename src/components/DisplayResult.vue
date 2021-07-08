<template>
  <div>
    {{ solutionString }}
  </div>
  <div>
    {{ letterString }}
  </div>
</template>

<script>
export default {
  name: "DisplayResult",
  props: {
    solutionString: String,
    letterString: String,
  },
};
</script>
