<template>
    <br>
    {{ dato }}
    <hr>
    {{ profile }}
    <hr>
    <form >
        <input type="text" placeholder="user">
        <br>
        <input type="password" placeholder="Mots de passe">
        <br>
        <input type="text" placeholder="MAC">
        <br>
        <input type="submit" value="send">
    </form>
   
</template>

<script setup>





const ip = ref()
const user = ref()
const pasa = ref()
const dato = ref()
const profile = ref()
ip.value = '192.168.1.1'
user.value = 'admin'
pasa.value = ''

const re = await useFetch('http://'+ip.value+'/rest/ip/hotspot/active',{
  method: 'GET',
  headers : {
    'Authorization': 'Basic ' + btoa(user.value + ':' + pasa.value),
  }
})
dato.value = re.data.value

const { data: res } = await useFetch('http://' + ip.value + '/rest/ip/hotspot/user/profile', {
    method: 'GET',
    headers: {
        'Authorization': 'Basic ' + btoa(user.value + ':' + pasa.value),
    }
})
profile.value = res.value
console.log(profile)




async function adduser() {
    const resu = await useFetch('http://' + ip.value + '/rest/ip/hotspot/active', {
        method: 'GET',
        headers: {
            'Authorization': 'Basic ' + btoa(user.value + ':' + pasa.value),
        }
    })
    dato.value = resu.data.value

}



</script>