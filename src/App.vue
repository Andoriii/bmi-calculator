<template>
  <div>
    <label for="lengte">Lengte in CM</label>
    <input type="text" name="lengte" v-model="lengte" />
    <label for="gewicht">Gewicht in KG:</label>
    <input type="text" name="gewicht" v-model="gewicht" />
    <button @click="result">Bereken je BMI</button>
    <p v-if="show">{{ bmi.toFixed(1) }} - {{ message }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      lengte: "",
      gewicht: "",
      bmi: 0,
      message: "",
      show: false,
    };
  },
  methods: {
    result() {
      if (this.lengte != "" && this.gewicht != "") {
        this.show = true;
        if (this.bmiCalc < 18.5) {
          this.message = "Je hebt ondergewicht!";
          this.bmi = this.bmiCalc;
        } else if (this.bmiCalc > 18.5 && this.bmiCalc < 24.9) {
          this.message = "Je hebt een normaal gezond gewicht";
          this.bmi = this.bmiCalc;
        } else if (this.bmiCalc > 25 && this.bmiCalc < 29.9) {
          this.message = "Je hebt overgewicht!";
          this.bmi = this.bmiCalc;
        } else if (this.bmiCalc > 30 && this.bmiCalc < 34.9) {
          this.message = "Je hebt klasse 1 obesitas";
          this.bmi = this.bmiCalc;
        } else if (this.bmiCalc > 35 && this.bmiCalc < 39.9) {
          this.message = "Je hebt klasse 2 obesitas";
          this.bmi = this.bmiCalc;
        } else if (this.bmiCalc > 40) {
          this.message = "Je hebt klasse 3 obesitas";
          this.bmi = this.bmiCalc;
        } else {
          this.message = "Gelieve correcte waarde in te geven";
        }
      }
    },
  },
  computed: {
    bmiCalc() {
      if (this.lengte < 2 && this.lengte > 0) {
        return this.gewicht / (this.lengte * this.lengte);
      }
      if (this.lengte > 2 && this.lengte > 0) {
        return (this.gewicht / (this.lengte * this.lengte)) * 10000;
      }
    },
  },
};
</script>

<style scoped>
div {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 400px;
  height: 400px;
  margin: auto;
  margin-top: 10rem;
}
input {
  border: none;
  padding: 1rem;
  border-bottom: 1px solid black;
}
label {
  font-size: 1.8rem;
  font-weight: bolder;
  color: rgb(63, 62, 62);
}
button {
  padding: 1rem 0 1rem 0;
  border: none;
  cursor: pointer;
  background-color: rgb(205, 207, 207);
  transition: 300ms;
}
button:hover {
  background-color: rgb(107, 106, 106);
  color: white;
}
</style>

