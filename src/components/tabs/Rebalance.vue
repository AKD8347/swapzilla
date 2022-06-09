<template>
  <div class="fund-your-acc__content rebalance">
    <v-subheader>From</v-subheader>
    <v-select
        icon="mdi-arrow-down-thick"
        :items="items"
        label="Choose exchange"
        append-icon="expand_more"
        menu-props="auto"
        filled
        outlined
    ></v-select>
    <v-subheader>To</v-subheader>
    <v-select
        icon="mdi-arrow-down-thick"
        :items="items"
        label="Choose exchange"
        append-icon="expand_more"
        menu-props="auto"
        filled
        outlined
    ></v-select>
    <v-select
        icon="mdi-arrow-down-thick"
        :items="items"
        label="Choose currency"
        append-icon="expand_more"
        menu-props="auto"
        filled
        outlined
    ></v-select>
    <v-text-field label="Amount on the balance"></v-text-field>
    <div class="rebalance__percent-block">
      <div class="rebalance__balance">Balance:&nbsp;<b>0.04763864</b></div>
      <div class="rebalance__percent-wrap">
        <v-radio-group v-model="radioSelected" row>
          <v-radio
              fluid
              v-for="item in radioGroup"
              :label="item.label"
              :value="item.label"
              :key="item.label"
          ></v-radio>
        </v-radio-group>
      </div>
    </div>
    <v-btn v-if="false" color="primary" elevation="2" large>Apply</v-btn>
  </div>
</template>

<script>
export default {
  name: "RebalanceTab",
  data() {
    return {
      items: ["Kraken", "Kraken 1", "Kraken 2"],
      radioSelected: null,
      radioGroup: [
        {
          label: "10%"
        },
        {
          label: "25%"
        },
        {
          label: "50%"
        },
        {
          label: "100%"
        },
        {
          label: "Split"
        }
      ]
    }
  }
}
</script>

<style lang="scss">
.rebalance {
  &__percent-block {
    background: #ffffff;
    box-shadow: 0px 7px 16px rgba(60, 72, 76, 0.1);
    border-radius: 5px;
    padding: 20px;
  }

  &__balance {
    display: flex;
    max-width: 139px;
    background: rgba(42, 101, 145, 0.1);
    border-radius: 3px;
    padding: 8px 12px;
    font-family: "Open Sans";
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 16px;

    color: #2a6591;
  }

  &__balance b {
    font-weight: 700;
  }

  &__percent-wrap .v-input--selection-controls__input {
    height: 0;
    width: 0;
    opacity: 0;
  }

  &__percent-wrap .v-radio {
    padding: 8px 10px;
    background: #9aa2a8;
    border-radius: 3px;
    gap: 10px;
  }

  .v-input--radio-group--row .v-input--radio-group__input {
    gap: 6px 10px;
  }

  .v-input--selection-controls__input {
    display: none;
  }

  .v-radio.theme--light.v-item--active {
    background: #2a6591;
  }

  .v-radio.theme--light.v-item--active .v-label {
    color: #ffffff;
  }

  .v-input--radio-group.v-input--radio-group--row .v-radio {
    margin-right: 0;
  }

}
</style>
