<script setup>

  const props = defineProps(['list'])
  
 
  


</script>

<template>
	<ul>
    <li v-for="(item,index) in props.list" @click="$emit('deleteList',index)">
    	{{item}}
    </li>
  </ul>

</template>