<template>
  <form @submit="onSubmit" class="add-form">
    <div class="form-control">
      <label
        >Introduceti un sir de numere cuprinse intre 100 si 999 separate prin
        virgula</label
      >
      <input
        type="text"
        v-model="inputString"
        name="text"
        placeholder="Inserati aici"
      />
    </div>
    <input type="submit" value="Calculate" class="btn btn-block" />
  </form>
</template>

<script>
export default {
  name: "InputForm",
  data() {
    return {
      inputString: "",
    };
  },
  methods: {
    onSubmit(e) {
      e.preventDefault();
      
      this.$emit("update-display", this.inputString);
    },
  },
};
</script>

<style scoped>
.add-form {
  margin-bottom: 40px;
}
.form-control {
  margin: 20px 0;
}
.form-control label {
  display: block;
}
.form-control input {
  width: 100%;
  height: 40px;
  margin: 5px;
  padding: 3px 7px;
  font-size: 17px;
}
.form-control-check {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.form-control-check label {
  flex: 1;
}
.form-control-check input {
  flex: 2;
  height: 20px;
}
</style>