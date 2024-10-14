<script setup>
  import {defineProps} from 'vue'
  
  const props = defineProps({
  transections:{}
  })
  const emit = defineEmits(["transectionDeleted"])
  const transectionDelete =(id)=>{
    emit('transectionDeleted',id)
  }
</script>
<template>
  <h3>History</h3>
      <ul id="list" class="list">
         <li v-for="transection of transections" :key="transection.id" :class="transection.amount > 0 ? 'plus' : 'minus'">
          {{transection.type}} <span>{{transection.amount}}$</span><button @click="transectionDelete(transection.id)" class="delete-btn">x</button>
        </li>
      </ul>
</template>