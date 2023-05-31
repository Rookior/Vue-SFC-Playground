<script setup>
 
console.log('hello script setup')
  import list from './list.vue'
  const msg = ref('Hello')
  // 函数
function log() {
  console.log(msg.value)
}
  
  import {ref,reactive,computed  } from 'vue'
  const count = ref(0)
  
  const newTodo = ref(null)
  const listArr = reactive ([
    
    "洗衣",
    '做饭',
    "喂马",
    "劈柴"
  ])
  const addList = ()=>{
    console.log(123,newTodo)
    listArr.push(newTodo.value)
  }
  const deleteList = (index)=>{
    console.log(index)
    listArr.splice(index,1)
  }
  const listComputedLength = computed(()=>{
    	return listArr.length > 10 ? 'Yes' : 'No'
  })
  
  const now = computed(() => {
    return Date.now() 
  })
  
  const firstName = ref('John')
const lastName = ref('Doe')

let fullName = computed({
  // getter
  get() {
    return firstName.value + ' ' + lastName.value
  },
  // setter
  set(newValue) {
    // 注意：我们这里使用的是解构赋值语法
    [firstName.value, lastName.value] = newValue.split(' ')
  }
})
const changeFullname = ()=>{
  console.log(123,fullName)
  fullName.value = 'w zy'
}

const isActive = ref(true)
</script>


<template>
  <h1 :class="{ active: isActive }">{{ msg }}</h1>
  <input v-model="msg">
  <div>
     <button @click="log">打印msg
  
    </button>
    
    
    
  </div>
  <button @click ="count++">
     {{count}}
  </button>
  <br/>
  <input v-model="newTodo" />
  <button @click="addList">
  添加
  </button>
  <list :list="listArr" @deleteList="deleteList" ></list>
   <p>
     待办列表超过10项目:{{listComputedLength}}
  </p>
  
  <p>
    计算属性值被缓存，除非有关联值修改：{{new Date(now).getFullYear() }}
    -{{new Date(now).getMonth()+1}}
    -{{new Date(now).getDay()}}
    {{new Date(now).getHours()}}
    :{{new Date(now).getMinutes()}}
    :{{new Date(now).getSeconds()}}
  </p>
  
  <input type="text" v-model="firstName" />
    <input type="text" v-model="lastName" />
  {{fullName}}
  
  <button @click="changeFullname">
    修改fullName
  </button>
</template>

<style>
  .active{
    color:#f00
  }
</style>