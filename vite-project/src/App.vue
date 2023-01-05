<template>
  <TheHeader text="MyCounter" />

  <!-- if modifying or overtreshold, Changing Validation Message. -->
  <div v-if="!validationMessageList.length">{{ count }}</div>
  <!-- Printing validation message list in loop. -->
  <div v-else v-for="message in validationMessageList" :key="message">
    {{ message }}
  </div>
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
      isEditing: false,
    };
  },
  watch: {
    inputCount() {
      // When editing, Editing Flag to true.
      this.isEditing = true;
    },
  },
  computed: {
    hasMaxCount() {
      return this.count >= 9999;
    },

    hasMinCount() {
      return this.count <= 0;
    },
    hasMaxInputCount() {
      // when inputCount over 9999, return true.
      return this.inputCount > 9999;
    },
    hasMinInputCount() {
      return this.inputCount < 0;
    },
    validationMessageList() {
      const validationList = [];

      // when editing, pushing message.
      if (this.isEditing) {
        validationList.push("Editing...");
      }

      if (this.hasMaxInputCount) {
        validationList.push("Not input over 9999.");
      }

      if (this.hasMinInputCount) {
        validationList.push("Not input under 0.");
      }

      return validationList;
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
      if (this.hasMaxInputCount || this.hasMinInputCount) return;
      this.count = this.inputCount;
      this.isEditing = false;
    },
  },
};
</script>

<style scoped></style>
