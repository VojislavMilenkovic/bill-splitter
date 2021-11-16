<template>
  <div>
    <h2>Bill Splitter</h2>
  </div>
  <div>
    <input type="number" placeholder="Enter Your Bill" v-model="totalBill" />
  </div>
  <div>
    <h4>Enter Number of People</h4>
    <input type="number" v-model="noPeople" />
  </div>
  <div>
    <h4>Please enter your tip %</h4>
    <input type="number" v-model="customAmount" />
  </div>

  <bill-display
    :noPeople="noPeople"
    :totalBill="totalBill"
    :customAmount="customAmount"
    @resetCalculation="setToZero"
  ></bill-display>
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
</style>