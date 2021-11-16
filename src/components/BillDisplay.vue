<template>
  <div>
    <h4>Bill Per Person:</h4>
    <h3>{{ billPerPerson }}</h3>
  </div>
  <div>
    <h4>Tip Per Person:</h4>
    <h3>{{ tipPerPerson }}</h3>
  </div>
  <div>
    <h4>Total Amount per Person:</h4>
    <h3>{{ totalAmountPerPerson }}</h3>
  </div>
  <div>
    <button type="button" @click="calcBillPerPerson">CALCULATE</button>
  </div>
  <div>
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
</style>