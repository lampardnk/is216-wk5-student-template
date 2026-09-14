<script setup>
import { ref, computed } from 'vue'

const x = ref(0)
const y = ref(0)
const operators = ref(["+", "-", "*", "/", "%"])
const selectedOp = ref("+")


const result = computed(() => {
    switch (selectedOp.value) {
        case '+': return x.value + y.value
        case '-': return x.value - y.value
        case '*': return x.value * y.value
        case '/': return y.value !== 0 ? x.value / y.value : 'Cannot divide by zero'
        case '%': return y.value !== 0 ? x.value % y.value : 'Cannot divide by zero'
        default: return 0
    }
})

    
</script>

<template>
    <p>x <input v-model.number="x"></p>
    <select v-model="selectedOp">
        <option v-for="op in operators">{{ op }}</option>
    </select>
    <p>y <input v-model.number="y"></p>

    <p>---------------------</p>

    <p>= {{ result }}</p>
</template>

<style scoped>
p,
input {
    font-family: monospace;
}

p {
    white-space: pre;
}
</style>
