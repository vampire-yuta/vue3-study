<template>
  <TheHeader text="MyCounter" />
  <div>{{ count }}</div>
  <BaseButton @onClick="plusOne">+</BaseButton>
  <BaseButton @onClick="minusOne">-</BaseButton>
  <div>
    <NumberInput v-model.numberOnly="inputCount" />
    <BaseButton @onClick="insertCount">Insert</BaseButton>
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
      this.count = this.inputCount;
      console.log("insert");
    },
  },
};
</script>

<style scoped></style>
