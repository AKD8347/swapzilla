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
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
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
