<template>
  <TheHeader text="MyCounter" />
  <div>{{ count }}</div>
  <BaseButton :disabled="hasMaxCount" @onClick="plusOne">+</BaseButton>
  <BaseButton :disabled="hasMinCount" @onClick="minusOne">-</BaseButton>
  <div>
    <NumberInput v-model.numberOnly="inputCount" max="9999" min="0" />
    <BaseButton @onClick="insertCount">insert</BaseButton>
  </div>
</template>

<script lang="ts">
import TheHeader from "./components/TheHeader.vue";
import BaseButton from "./components/BaseButton.vue";
import NumberInput from "./components/NumberInput.vue";

export default {
  components: {
    TheHeader,
    BaseButton,
    NumberInput,
  },
  data() {
    return {
      count: 0,
      inputCount: 0,
    };
  },
  watch: {
    inputCount(value) {
      if (value >= 9999) {
        this.inputCount = 9999;
        console.log(">= 9999");
      }

      if (value <= 0) {
        this.inputCount = 0;
        console.log("<= 0");
      }
    },
  },
  computed: {
    hasMaxCount() {
      return this.count >= 9999;
    },

    hasMinCount() {
      return this.count <= 0;
    },
  },
  methods: {
    plusOne() {
      this.count++;
      console.log("+");
    },
    minusOne() {
      this.count--;
      console.log("-");
    },
    insertCount() {
      console.log("-----");
      this.count = this.inputCount;
      console.log(this.count);
      console.log("-----");
      console.log("insert");
    },
  },
};
</script>

<style scoped></style>
