<template>
  <div class="container">
    <div class="headline">
      <h2>Bill Splitter</h2>
    </div>
    <div>
      <h5>Your Bill:</h5>
      <input type="number" placeholder="Your Bill goes here" v-model="totalBill" />
    </div>
    <div>
      <h5>Enter Number of People:</h5>
      <input type="number" placeholder="No. people goes here" v-model="noPeople" />
    </div>
    <div>
      <h5>Please enter your tip %:</h5>
      <input type="number" placeholder="Your Tip % goes here" v-model="customAmount" />
    </div>

    <bill-display
      :noPeople="noPeople"
      :totalBill="totalBill"
      :customAmount="customAmount"
      @resetCalculation="setToZero"
    ></bill-display>
  </div>
</template>

<script>
import BillDisplay from "./components/BillDisplay.vue";
export default {
  components: {
    BillDisplay,
  },
  data() {
    return {
      totalBill: "",
      noPeople: "",
      customAmount: "",
    };
  },
  methods: {
    setToZero() {
      this.totalBill = "";
      this.noPeople = "";
      this.customAmount = "";
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Rubik&display=swap");
#app{
  background:chartreuse;
}
.container {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  padding: 20px 40px;
  background: salmon;
  font-family: "Rubik", sans-serif;
  border-radius: 5px;
}

.container h2{
  text-align: center;
  color: black;
}
h5{
  margin-bottom: 10px;
}
input{
  border-radius: 6px;
  border: none;
  outline: none;
  padding: 2px 5px;
  }

</style>