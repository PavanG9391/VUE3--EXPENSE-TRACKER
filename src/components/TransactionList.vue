<template>
    <h3>History</h3>
    <ul id="list" class="list">
        <li v-for="transaction in props.transactions" 
        v-bind:key="transaction.id"
        v-bind:class="transaction.amount >0 ? 'plus' : 'minus' "
        >
            {{ transaction.text }} <span>{{transaction.amount}}</span><button @click="deleteTransaction(transaction.id)" class="delete-btn">x</button>
        </li>
     
    </ul>

</template>
<script setup>
import {defineProps} from 'vue'

const emit = defineEmits(['transactionDeleted'])

const props =defineProps({
    transactions:{
        type:Array,
        required:true
    }
})

const deleteTransaction=(id)=>{
   emit('transactionDeleted',id)
}
</script>

