<template>
  <h3>History</h3>
  <ul id="list" class="list">
    <!-- v-for="(value, key) in myObject"-->
    <li
      v-for="anyTransaction in transactions"
      :key="anyTransaction?.id"
      :class="anyTransaction?.amount < 0 ? 'minus' : 'plus'"
    >
      {{ anyTransaction?.text }} <span>${{ anyTransaction?.amount }} </span
      ><button class="delete-btn" @click="deleteTransaction(anyTransaction?.id)">x</button>
    </li>
  </ul>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  // transactions is the Prop passed from App.vue
  transactions: {
    type: Array,
    required: true,
  },
});

const emit = defineEmits(["transactionDeleted"]);
const deleteTransaction = (id) => {
  emit("transactionDeleted", id);
};
</script>
