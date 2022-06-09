<template>
  <v-app>
    <div class="fund-your-acc">
      <div class="fund-your-acc__form">
        <div class="fund-your-acc__navigation">
          <v-tabs v-model="tab">
            <v-tab>Deposit</v-tab>
          </v-tabs>
          <div class="fund-your-acc__exit"></div>
        </div>

        <transition name="slide-fade" mode="out-in" appear>
          <deposit-tab v-if="tab === 0" />
        </transition>
      </div>
    </div>
  </v-app>
</template>

<script>
import DepositTab from "@/components/tabs/Deposit"

export default {
  name: "App",
  components: { DepositTab},
  data() {
    return {
      tab: 0
    }
  }
}
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=Open+Sans&display=swap");

.slide-fade-enter-active {
  transition: all 0.2s ease-in-out;
}
.slide-fade-leave-active {
  transition: all 0.4s cubic-bezier(1, 0.5, 0.8, 1);
}
.slide-fade-enter,
.slide-fade-leave-to {
  transform: translateX(30px);
  opacity: 0;
}

.fund-your-acc {
  background: #7e7e7e;

  display: flex;
  flex: 1;
  padding: 20px;

  .v-tab + .v-tab {
    padding-right: 20px;
    padding-left: 20px;
  }

  .v-text-field > .v-input__control > .v-input__slot:before,
  .v-text-field > .v-input__control > .v-input__slot:after {
    display: none;
  }

  .v-text-field--outlined.v-input--is-focused fieldset,
  .v-text-field--outlined.v-input--has-state fieldset {
    border: 0;
  }

  .v-text-field--filled > .v-input__control > .v-input__slot,
  .v-text-field--full-width > .v-input__control > .v-input__slot,
  .v-text-field--outlined > .v-input__control > .v-input__slot {
    min-height: 50px;
  }

  .v-text-field--outlined fieldset {
    border-width: 0;
  }

  .v-tabs-slider-wrapper .v-tabs-slider {
    background: #3c484c;
  }

  .v-tabs-slider-wrapper {
    height: 4px !important;
  }

  .v-tabs-bar {
    height: 70px;
  }

  .deposit button {
    text-transform: capitalize;
  }

  .rebalance .v-subheader {
    height: auto;
    font-family: "Open Sans";
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 16px;

    color: #3c484c;
    margin-bottom: 10px;
  }

  .v-text-field__slot label {
    top: 12px;
  }

  .v-input.theme--light.v-text-field.errorCustom .v-text-field__slot::before {
    background: #e92525;
  }

  .withdrawCustom .v-text-field__slot::before {
    position: absolute;
    right: 9px;
    top: 10px;
    content: "max";
    padding: 7px 10px;
    padding-bottom: 9px;

    background: #9aa2a8;
    border-radius: 3px;

    font-family: "Open Sans";
    font-style: normal;
    font-weight: 700;
    font-size: 12px;
    line-height: 16px;

    color: #ffffff;
  }

  .withdraw .withdrawСustom .v-messages__message {
    padding-left: 12px;
  }

  .v-text-field__slot input {
    background: #f0f0f0;
    border-radius: 5px;
    min-height: 50px !important;
    max-height: 50px !important;
    height: 100%;
    padding-left: 12px;
  }

  .v-text-field {
    padding-top: 0;
    margin-top: 0;
  }

  .v-text-field__slot .theme--light.v-label {
    padding-left: 12px;
  }

  .v-tab {
    max-height: 48px;
    margin-top: 10px;
    font-family: "Open Sans";
    font-style: normal;
    font-weight: 400;
    font-size: 20px;
    line-height: 27px;

    text-transform: capitalize;
    // padding-left: 0;
    justify-content: left;
    letter-spacing: 0.008286em !important;
  }

  &__form {
    background: #ffffff;
    display: flex;
    flex-direction: column;
    flex: 1;
    max-width: 780px;
    margin: auto;
    border-radius: 5px;
    padding: 30px;
    padding-top: 16px;
    padding-bottom: 71px;
  }

  &__navigation {
    display: flex;
    justify-content: space-between;
    width: 100%;
    cursor: pointer;
  }

  &__exit {
    content: url("data:image/svg+xml;charset=UTF-8,%3csvg width='22' height='23' viewBox='0 0 22 23' fill='none' xmlns='http://www.w3.org/2000/svg'%3e%3cpath d='M1 1.5L21 21.5' stroke='%239AA2A8' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3e%3cpath d='M21 1.5L0.999999 21.5' stroke='%239AA2A8' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3e%3c/svg%3e ");
  }

  &__content {
    display: flex;
    justify-content: center;
    flex-direction: column;
    margin: auto;
    margin-top: 41px;
    max-width: 380px;
    width: 100%;
    padding-right: 5px;
  }

  &__code {
    display: flex;
    justify-content: center;
    margin-bottom: 27px;
  }

  &__code-text {
    margin-bottom: 29px !important;
    display: flex;
    justify-content: center;
    font-family: "Open Sans";
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 22px;
    color: #3c484c;
  }
}

@media screen and (max-width: 567px) {
  .v-slide-group__prev.v-slide-group__prev--disabled {
    display: none !important;
  }
  .v-tabs.theme--light {
    overflow: auto;
    width: 70vw;
    padding-right: 20px;
  }
}

@media screen and (max-width: 425px) {
  .v-tabs.theme--light {
    overflow: auto;
    width: 70vw;
    padding-right: 20px;
  }
  .fund-your-acc__form {
    padding: 20px;
    padding-bottom: 60px;
  }
}
@media screen and (max-width: 360px) {
  .v-tabs.theme--light {
    width: 220px;
  }
  .fund-your-acc__form {
    max-width: 100%;
  }
  .v-application p {
    overflow-wrap: anywhere;
  }
}
</style>
