<template>
  <div id="app">
    <div class="bucketlist">
      <h2>BucketList</h2>
      <form>
        <input type="text" v-model="listName" placeholder="add new task" />
        <input type="date" v-model="date" @blur="addTask" />
      </form>
      <div class="hideButton" @click="hideCompleteFunction">
        Hide / Show Completed Task
      </div>
      <div class="openDueContainer">
        <div>
          <span> Open Task: </span>
          <span> {{ open }} </span>
        </div>
        <div>
          <span> Dued Tasks: </span>
          <span> {{ overdue }} </span>
        </div>
      </div>
      <ul>
        <li
          v-for="task in tasks"
          v-bind:key="task.id"
          :class="{ completedClass: task.completed }"
          v-show="!task.completed || (showCompleted && task.completed)"
        >
          <div class="li-left">
            <div>
              <span class="elementTitle">Task: </span>
              <span>{{ task.name }}</span>
            </div>

            <div>
              <span class="elementTitle">Until: </span>
              <span>{{ task.due }}</span>
            </div>

            <div>
              <input
                type="checkbox"
                :checked="task.completed"
                @click="changeCompleted(task.id)"
              />
              <span> Done</span>
            </div>
          </div>
          <div class="li-right">
            <div @click="modifyFunction(task.id)">modify</div>
            <div @click="deleteFunction(task.id)">delete</div>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
/* import HelloWorld from './components/HelloWorld.vue' */

export default {
  name: "BucketList",

  // used components
  components: {},

  // fixed datas, loaded before the component render.
  // or not. I can change the task.id and it change the class... ??????
  data() {
    return {
      showCompleted: true,
      fixedDataMessage:
        "fix data, what U use in the components. This loaded, when the componens loaded",
      //date: (new Date).toISOString().split("T")[0]  ,  // eredeti dátum
      listName: "",
      date: new Date(new Date().setDate(new Date().getFullYear() + 5))
        .toISOString()
        .split("T")[0],
      tasks: [
        {
          id: 1,
          name: "Listen every music",
          completed: false,
          due: "2025-12-12",
        },
        {
          id: 2,
          name: "Join every festival",
          completed: false,
          due: "2025-12-22",
        },
        {
          id: 3,
          name: "Drink every good shit",
          completed: true,
          due: "2028-12-22",
        },
        {
          id: 4,
          name: "Fuck every hot girl",
          completed: false,
          due: "2027-12-30",
        },
      ],
    };
  },

  // dynamic datas
  computed: {
    open: function () {
      return this.tasks.filter((task) => !task.completed).length;
    },
    overdue: function () {
      return this.tasks.filter(
        (task) => !task.completed && task.due < new Date().toISOString()
      ).length;
    },
  },

  //a lifcycled hook,
  created() {},

  // define functions here
  methods: {
    changeCompleted(id) {
      let task = this.tasks.find((task) => task.id === id);
      task.completed = !task.completed;
    },

    addTask() {
      const listElement = {
        name: this.listName,
        due: this.date,
        completed: false,
      };

      const taskList = this.tasks;

      taskList.push(listElement);
    },

    hideCompleteFunction() {
      this.showCompleted = !this.showCompleted;
    },

    deleteFunction(id) {
      this.tasks = this.tasks.filter((item) => item.id !== id);
    },

    modifyFunction(id) {
      let task = this.tasks.find((task) => task.id === id);
      task.name = "modified, (I too lazy to make a new form)";
    },
  },
};
</script>

<style>
@import "../styles/style.css";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.bucketlist {
  margin: 0px 5rem;
  max-width: 1000px;
  margin: 0 auto;
}

.bucketlist li {
  text-align: start;
  margin: 1rem 0 0 0;
  border: 2px solid black;
  border-radius: 1rem;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
}

.elementTitle {
  font-weight: bold;
}

.completedClass {
  text-decoration: line-through;
  color: green;
}

.li-right div {
  cursor: pointer;
}

.li-right div:hover {
  color: blue;
}

.li-right div:first-child {
  margin: 0 0 1rem;
}

form {
  display: flex;
  width: 40%;
  margin: 0 auto;
}

input[type="text"] {
  flex-grow: 3;
  font-size: 1.5 rem;
}
</style>
