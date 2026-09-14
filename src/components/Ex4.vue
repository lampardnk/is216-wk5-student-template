<script setup>
import { ref } from 'vue'
const items = ref(['keyboard', 'mouse', 'iPhone', 'macbook', 'adapter'])
const newItem = ref('')


function addItem() {
    if (newItem.value.trim() !== '') {
        items.value.push(newItem.value.trim())
        newItem.value = ''
    }
}

function removeItem(index) {
    items.value.splice(index, 1)
}


</script>

<template>

    <h2>Shopping Cart</h2>

    <div>
        <input v-model="newItem" placeholder="Add an item" @keyup.enter="addItem">
        <button @click="addItem">Add!</button>
    </div>
    <ul>
        <li v-for="(item, index) in items" :key="index">
            {{ item }} <button @click="removeItem(index)">Delete!</button>
        </li>
    </ul>

</template>
