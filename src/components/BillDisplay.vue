<template>
  <div>
    <h5>Bill Per Person: {{ billPerPerson }}</h5>
  </div>
  <div>
    <h5>Tip Per Person: {{ tipPerPerson }}</h5>
  </div>
  <div>
    <h5>Total/person: {{ totalAmountPerPerson }}</h5>
  </div>
  <div>
    <button type="button" @click="calcBillPerPerson">CALCULATE</button>
    <button type="button" @click="resetCalculation">RESET</button>
  </div>
</template>

<script>
export default {
  props: ["totalBill", "noPeople", "customAmount"],
  emits: ["resetCalculation"],
  data() {
    return {
      billPerPerson: "",
      tipPerPerson: "",
      totalAmountPerPerson: "",
    };
  },
  methods: {
    calcBillPerPerson() {
      this.billPerPerson = this.totalBill / this.noPeople;
      this.tipPerPerson = this.billPerPerson / this.customAmount;
      this.totalAmountPerPerson = this.billPerPerson + this.tipPerPerson;
    },
    resetCalculation() {
      this.$emit("resetCalculation");
      this.billPerPerson = "";
      this.tipPerPerson = "";
      this.totalAmountPerPerson = "";
    },
  },
};
</script>

<style>
button {
  background-color: white;
  border-radius: 5px;
  border: none;
  cursor: pointer;
  margin: 5px;
  font-size: 15px;
  padding: 3px 5px;
}
</style>