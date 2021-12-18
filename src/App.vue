<template>
  <div id="app">
    <div>
      <h1>Hello Vue</h1>
    </div>
    <div>
      <p>{{fixedDataMessage}}</p>
    </div>
    <div class="bucketlist">
      <h2>BucketList</h2>
      <ul>
        <li v-for="task in tasks" v-bind:key="task.id" :class="{completedClass: task.completed}">
           <div> <span>Task: </span>
           <span>{{task.name}}</span>
           </div>
           <div>
             <span>Until: </span>
             <span>{{task.due}}</span>
           </div>
           <div>
             <input type="checkbox" :checked=task.completed @click="changeCompleted(task.id)">
             <span> Done</span>
           </div>
        </li>
      </ul>
    </div>
<!--     <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
/* import HelloWorld from './components/HelloWorld.vue' */

export default {
  name: 'App',
  
  // used components
  components: {
  },

// fixed datas, loaded before the component render. 
// or not. I can change the task.id and it change the class... ??????
data(){
  return{
    fixedDataMessage: "fix data, what U use in the components. This loaded, when the componens loaded",
    tasks:   [
    {
      id:1,
      name:"Listen every music",
      completed: false,
      due: "2025-12-12"
    },    
    {
      id:2,
      name:"Join every festival",
      completed: false,
      due: "2025-12-22"
    },
        {
      id:3,
      name:"Drink every good shit",
      completed: true,
      due: "2028-12-22"
    },
        {
      id:4,
      name:"Fuck every hot girl",
      completed: false,
      due: "2027-12-30"
    }
    ]

  };

}, 

// dynamic datas
computed:{
  }, 

  //a lifcycled hook, 
  created(){
  },


// define functions here
methods:{
  changeCompleted(id){
     let task = this.tasks.find(task => task.id === id)
    task.completed = !task.completed 
  }
}


}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  ;
}

.bucketlist{
  margin: 0px 5rem;
  max-width: 1000px;
  margin: 0 auto;
}

.bucketlist li{
  text-align: start;
  margin: 1rem 0 0 0;
  
}

.bucketlist li div span:first-child{
  font-weight: bold;
}

.completedClass{
  background-color: rgba(255, 0, 0, .3);
}
</style>
