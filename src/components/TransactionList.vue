<template>
    <h3>History</h3>
    <ul id="list" class="list">
        <!-- v-for="(value, key) in myObject"-->
        <li v-for="anyTransaction in transactions" :key="anyTransaction?.id"
            :class="anyTransaction?.amount < 0 ? 'minus' : 'plus'">
            {{ anyTransaction?.text }} <span>${{ anyTransaction?.amount }}</span><button class="delete-btn">x</button>
        </li>
    </ul>
</template>

<script setup>
import { defineProps } from 'vue';
const props = defineProps({
    // transactions is the Prop passed from App.vue
    transactions: {
        type: Array,
        required: true
    }
});
</script>

<!-- //  export default {
// data() {
//     return {
//         transactions: [
//             { id: 1, text: "Flower", amount: -20 },
//             { id: 2, text: "Basket1", amount: -10 },
//             { id: 3, text: "Camera", amount: 10 },
//             { id: 4, text: "Book", amount: 150 },
//         ],
//     }
// }
//2nd method to define
// setup() {
//     return {
//         transactions
//     }
// }
// } -->