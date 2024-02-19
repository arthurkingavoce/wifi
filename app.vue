<template>
  <NuxtPage>
    <hr>
    <br>
    {{ dato }}
    <br>
    <hr>

  </NuxtPage>
 
  <hr>
  


 

</template>
<script setup>
const ip = ref()
const user = ref()
const pasa = ref()
const dato = ref()
ip.value='192.168.1.1'
user.value = 'admin'
pasa.value= ''



</script>