<template>
  <div class="app">
    <my-header></my-header>
    <control
      :addGood="addGood"
      @addNeutral="state.neutral += 1"
      @addBad="state.bad += 1"
      @reset="resetState"
      :total="state.good + state.bad + state.neutral"
    />
    <feedback :state="state" />
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader.vue";
import Control from "./components/Control.vue";
import Feedback from "./components/Feedback.vue";
export default {
  components: {
    MyHeader,
    Control,
    Feedback,
  },
  data() {
    return {
      state: null,
    };
  },
  methods: {
    resetState() {
      this.state = { good: 0, neutral: 0, bad: 0 };
    },
    addGood() {
      this.state.good += 1;
    },
  },
  watch: {
    state: {
      handler() {
        localStorage.setItem("state", JSON.stringify(this.state));
      },
      deep: true,
    },
  },

  created() {
    const savedState = localStorage.getItem("state");
    this.state = JSON.parse(savedState) || {
      good: 0,
      neutral: 0,
      bad: 0,
    };
  },
};
</script>

<style scoped>
.app {
  display: flex;
  flex-direction: column;
}
</style>
