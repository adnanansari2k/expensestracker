<script setup>
  import {ref} from 'vue'
  import {useToast} from 'vue-toastification'
  const type = ref("")
  const amount = ref("")
  const toast = useToast()
  
  const emit = defineEmits(['transectionSubmitted'])
  const addTransection =()=>{
    if(!type.value || !amount.value){
     toast.error("add somthing pls")
     return
    }
    const transectionData = {
      type : text.value,
      amount : parseFloat(amount.value)
    }
    emit('transectionSubmitted',transectionData)
    type.value=amount.value = ""
  }
</script>

<template><h3>Add new transaction</h3>
      <form id="form" @submit.prevent="addTransection">
        <div class="form-control">
          <label for="text">Text</label>
          <input type="text" v-model="type" id="text" placeholder="Enter text..." />
        </div>
        <div class="form-control">
          <label for="amount"
            >Amount <br />
            (negative - expense, positive - income)</label
          >
          <input type="text" v-model="amount" id="amount" placeholder="Enter amount..." />
        </div>
        <button class="btn" type="submit">Add transaction</button>
      </form>
      </template>