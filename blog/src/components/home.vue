<template>
  <h1>Hellow {{ msg }}</h1>

</template>

<script setup>
  import { defineProps, reactive } from 'vue'

  defineProps({
    msg: String
  })


</script>