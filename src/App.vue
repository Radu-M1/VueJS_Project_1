<template>
  <div class="container">
    <div class="card">
      <InputForm @update-display="updateDisplay" />
      <DisplayResult
        :solutionString="solutionString"
        :letterString="letterString"
      />
      <Matrix @toggle-item="toggleItem" :displayArray="displayArray" />
    </div>
  </div>
</template>

<script>
import InputForm from "./components/InputForm";
import DisplayResult from "./components/DisplayResult";
import Matrix from "./components/Matrix";

export default {
  data() {
    return {
      solutionString: "",
      letterString: "",
      displayArray: [],
    };
  },
  name: "App",
  components: {
    InputForm,
    DisplayResult,
    Matrix,
  },
  methods: {
    updateDisplay(inputString) {
      let numbers = inputString.split(",");
      numbers = numbers.map((elem) => parseInt(elem, 10));
      
      for (let i = 0; i < numbers.length; i++) {
        if (isNaN(numbers[i])) {
          alert("Please, add a valid input!");
          // this.letterString = "";
          // this.solutionString = "";
          inputString = "";
          return;
        }
      }
      this.letters = [];
      this.displayArray = [];
      let letters = [];
      let solutionMap = new Map();
      for (let i of numbers) {
        let clasa = Math.floor(i / 100);
        if (solutionMap.get(clasa.valueOf())) {
          if (solutionMap.get(clasa.valueOf()) < i) {
            solutionMap.set(clasa.valueOf(), i);
          }
        } else {
          solutionMap.set(clasa.valueOf(), i);
        }
      }

      solutionMap[Symbol.iterator] = function* () {
        yield* [...this.entries()].sort((a, b) => a[1] - b[1]);
      };

      const alphabet = [
        "A",
        "B",
        "C",
        "D",
        "E",
        "F",
        "G",
        "H",
        "I",
        "J",
        "K",
        "L",
        "M",
        "N",
        "O",
        "P",
        "Q",
        "R",
        "S",
        "T",
        "U",
        "V",
        "W",
        "X",
        "Y",
        "Z",
      ];

      for (let item of solutionMap) {
        letters.push(alphabet[item[1] % 26]);
      }
      this.letterString = "[";
      for (let i of letters) {
        this.letterString += '"' + i + '", ';
      }

      this.letterString =
        this.letterString.slice(0, this.letterString.length - 2) + "]";
      letters = [...new Set(letters)];

      for (let i = 0; i < 16; i++) {
        this.letters.push(letters[Math.floor(Math.random() * letters.length)]);
      }
      for (let i = 0; i < 16; i++) {
        let obj = {
          id: i.valueOf(),
          value: "?",
        };
        this.displayArray.push(obj);
      }
      this.solutionString = "[";
      for (let i of solutionMap) {
        this.solutionString += i[1] + " ,";
      }
      this.solutionString =
        this.solutionString.slice(0, this.solutionString.length - 2) + "]";
    },
    toggleItem(id) {
      if (this.displayArray[id].value === "?") {
        this.displayArray[id].value = this.letters[id];
      } else {
        this.displayArray[id].value = "?";
      }
    },
  },
  created() {
    this.letters = [];
  },
};
</script>


<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}

.container {
  display: flex;
  justify-content: center;
}

.card {
  max-width: 700px;
  margin: 30px 30px auto 30px;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}

.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
