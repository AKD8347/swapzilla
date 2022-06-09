<template>
  <v-app>
    <div class="fund-your-acc">
      <div class="fund-your-acc__form">
        <div class="fund-your-acc__navigation">
          <v-tabs v-model="tab">
            <v-tab>Deposit</v-tab>
            <v-tab>Withdraw</v-tab>
            <v-tab>Rebalance</v-tab>
          </v-tabs>
          <div class="fund-your-acc__exit"></div>
        </div>

        <transition name="slide-fade" mode="out-in" appear>
          <deposit-tab v-if="tab === 0" />
          <withdraw-tab v-if="tab === 1" />
          <rebalance-tab v-if="tab === 2" />
        </transition>
      </div>
    </div>
  </v-app>
</template>

<script>
import DepositTab from "@/components/tabs/Deposit"
import WithdrawTab from "@/components/tabs/Withdraw"
import RebalanceTab from "@/components/tabs/Rebalance"

export default {
  name: "App",
  components: { DepositTab, WithdrawTab, RebalanceTab },
  data() {
    return {
      tab: 0
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
