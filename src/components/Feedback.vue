<template>
  <ul class="list" v-if="getTotal">
    <li>
      <p><strong>Good</strong>: {{ state.good }}</p>
    </li>
    <li>
      <p><strong>Neutral</strong>: {{ state.neutral }}</p>
    </li>
    <li>
      <p><strong>Bad</strong>: {{ state.bad }}</p>
    </li>
    <li>
      <p><strong>Total</strong>: {{ getTotal }}</p>
    </li>
    <li>
      <p><strong>Positiv</strong>: {{ getPersent }}%</p>
    </li>
  </ul>
  <p v-else class="null">You dont have reviews</p>
</template>

<script>
export default {
  name: "feedback",
  props: {
    state: Object,
  },
  computed: {
    getTotal() {
      return this.state.good + this.state.bad + this.state.neutral;
    },
    getPersent() {
      return ((this.state.good + this.state.neutral) / this.getTotal) * 100;
    },
  },
};
</script>

<style scoped>
.list {
  display: flex;
  flex-direction: column;
  gap: 10px;
  margin: 20px auto;
}
.null {
  margin: 20px auto;
  font-size: 20px;
}
</style>
