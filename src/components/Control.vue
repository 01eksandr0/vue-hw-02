<template>
  <div class="list">
    <button @click="addGood" class="btn" type="button">Good</button>
    <button @click="$emit('addNeutral')" class="btn" type="button">
      Neutral
    </button>
    <button @click="$emit('addBad')" class="btn" type="button">Bad</button>
    <button v-if="total" @click="$emit('reset')" class="btn" type="button">
      Reset
    </button>
  </div>
</template>

<script>
export default {
  name: "control",
  props: {
    total: Number,
    addGood: Function,
  },
};
</script>

<style lang="css" scoped>
.list {
  display: flex;
  align-items: center;
  gap: 10px;
  margin: 0 auto;
}
.btn {
  background-color: #fff;
  font-size: 20px;
  border: none;
  padding: 4px 6px;
  transition: background-color 250ms linear;
}
.btn:hover {
  background-color: #999696;
}
</style>
