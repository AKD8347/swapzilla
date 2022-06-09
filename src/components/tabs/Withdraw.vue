<template>
  <div class="fund-your-acc__content withdraw">
    <v-select
      v-model="value.chooseExchange"
      icon="mdi-arrow-down-thick"
      :items="items"
      label="Choose exchange"
      append-icon="expand_more"
      menu-props="auto"
      @change="onChooseExchange"
      :error-messages="error.chooseExchange"
      filled
      outlined
    ></v-select>
    <v-select
      v-model="value.chooseCurrency"
      icon="mdi-arrow-down-thick"
      :items="items"
      label="Choose currency"
      append-icon="expand_more"
      menu-props="auto"
      @change="onChooseCurrency"
      :error-messages="error.chooseCurrency"
      filled
      outlined
    ></v-select>
    <v-text-field
      v-model="value.withdrawAmount"
      label="Withdraw amount"
      class="withdrawСustom"
      @input="onWithdrawAmount"
      :error-messages="error.withdrawAmount"
      :class="{ errorCustom: isErrorAmount }"
    ></v-text-field>
    <v-btn color="primary" elevation="2" large @click="onWinthdraw"
      >Withdraw</v-btn
    >

    <v-snackbar
      info
      v-model="snackbar"
      color="deep-purple accent-4"
      :timeout="2000"
    >
      {{ textSnackbar }}
    </v-snackbar>
  </div>
</template>

<script>
export default {
  name: "WithdrawTab",
  data() {
    return {
      items: ["Kraken", "Kraken 1", "Kraken 2"],

      isErrorAmount: false,
      snackbar: false,
      value: {
        chooseExchange: "",
        chooseCurrency: "",
        withdrawAmount: ""
      },
      error: {
        chooseExchange: [],
        chooseCurrency: [],
        withdrawAmount: []
      }
    }
  },
  methods: {
    onChooseExchange() {
      this.error.chooseExchange = []
    },
    onChooseCurrency() {
      this.error.chooseCurrency = []
    },
    onWithdrawAmount() {
      if (
        this.value.withdrawAmount === "" ||
        this.value.withdrawAmount >= 100
      ) {
        this.isErrorAmount = true
        this.error.withdrawAmount = ["Fill in withdrawal amount"]
      } else {
        this.isErrorAmount = false
        this.error.withdrawAmount = []
      }
    },
    onWinthdraw() {
      if (this.value.chooseExchange === "") {
        this.error.chooseExchange = ["Currency cannot be empty"]
      }
      if (this.value.chooseCurrency === "") {
        this.error.chooseCurrency = ["Currency cannot be empty"]
      }
      if (
        this.value.withdrawAmount === "" ||
        this.value.withdrawAmount >= 100
      ) {
        this.error.withdrawAmount = ["Fill in withdrawal amount"]
      }

      if (
        this.error.chooseExchange.length === 0 &&
        this.error.chooseCurrency.length === 0 &&
        this.error.withdrawAmount.length === 0
      ) {
        this.snackbar = true
      }
    }
  },
  computed: {
    textSnackbar() {
      return "Currency successfully withdrawn"
    }
  }
}
</script>

<style lang="scss">
.withdraw {
  .v-text-field__slot input:hover,
  .v-text-field__slot input:focus {
    background: rgba(0, 0, 0, 0.14);
  }
}
</style>
