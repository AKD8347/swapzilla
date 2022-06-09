<template>
  <div class="fund-your-acc__content deposit">
    <v-select
      icon="mdi-arrow-down-thick"
      :items="items"
      :value="items[0]"
      label="Currency"
      append-icon="expand_more"
      menu-props="auto"
      filled
      outlined
    ></v-select>
    <v-select
      v-model="selectedCurrency"
      icon="mdi-arrow-down-thick"
      :items="items"
      label="Choose currency"
      append-icon="expand_more"
      menu-props="auto"
      filled
      @change="onChangeCurrency"
      :error-messages="errorMsg"
      outlined
    ></v-select>
    <div id="qrcode" class="fund-your-acc__code" ref="qrcode"></div>
    <p class="fund-your-acc__code-text">{{ qrText }}</p>
    <v-btn color="primary" elevation="2" large @click="onDeposit">Copy</v-btn>

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
import QRCode from "qrcodejs2"

export default {
  name: "DepositTab",
  created() {
    this.initQr()
  },
  data() {
    return {
      items: ["Kraken", "Kraken 1", "Kraken 2"],
      qrText: "FGBfvcnkfdnvkk74365832ybvcvdfvfvb",
      selectedCurrency: "",
      errorMsg: [],
      snackbar: false
    }
  },
  methods: {
    initQr() {
      this.$nextTick(() => {
        new QRCode("qrcode", {
          width: 105,
          height: 105,
          text: this.qrText
        })
      })
    },
    onChangeCurrency() {
      this.errorMsg = []
    },
    onDeposit() {
      if (this.selectedCurrency === "") {
        this.errorMsg = ["Select currency for deposit"]
        return
      }
      this.snackbar = true
    }
  },
  computed: {
    textSnackbar() {
      return "Successfully take a deposit"
    }
  }
}
</script>
