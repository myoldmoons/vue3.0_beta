<template>
  <div id="app">
    <h1>{{title.name}}</h1>
    <div>{{user}}</div>
    <button @click="updateUser">修改名称</button>
    <div>当前count：{{computedCount}}</div>
    <button @click="increment">修改count</button>
    <hello-world msg="hello"></hello-world>
    <div v-for='item in list' :key="item" @click='addItem(item)'>{{item}}</div>
  </div>
</template>

<script>
import { reactive,ref,onMounted,computed } from 'vue'
import helloWorld from './components/HelloWorld.vue'
import axios from 'axios'
export default {
  name: 'App',
  components:{
    helloWorld
  },
  setup(){
    const title = reactive({
      name:'欢迎学习Vue3.0'
    })
    const user = ref('河畔一角');
    //如果需要修改值，可通过value
    
    const updateUser = ()=>{
      user.value = '河畔老师'
    }
    
    //生命周期方法

    onMounted(()=>{
      console.log('init mounted...')
      // axios.get('http://192.168.11.53:3000/list').then(res=>{
      //   console.log(res)
      // })
      // axios.post('http://192.168.11.53:3000/list/add',{
      //   name:'user0001',
      //   age:18,
      //   six:'女',
      //   id:1
      // }).then(res=>{
      //   console.log(res)
      // })
      // axios.post('http://192.168.11.53:3000/login/',{
      //   account:'admin',
      //   password:'12345'
      // }).then(res=>{
      //   console.log(res)
      // })
    })

    // 初始化count值
    const count = ref(0);

    const increment = ()=>{
      count.value++
    }

    const list=ref([1,2,3,4])

    const addItems=()=>{
      alert(1)
    }
    const addItem=()=>{
      addItems()
      list.value.push(5)
    }
    // 调用计算属性函数Hook
    const computedCount=computed(()=>count.value*10)
    return { title , user, updateUser,count,increment,computedCount ,list,addItem}
  }
}
</script>

<style>
#app {
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
