<template>
  <div id="app">
    <div>
      <h1>Hello Vue</h1>
    </div>

    <div>
      <p>{{ fixedDataMessage }}</p>
    </div>

    <BucketList></BucketList>
    <div class="testField">
      <h2>This is a field of my tests of the techniques</h2>
      <div class="testElement">
        <TryImportVue :prop="propData"></TryImportVue>
      </div>
    </div>
  </div>
</template>

<script>
import TryImportVue from "./components/tryComponent.vue";
import BucketList from "./components/firstVue";

export default {
  name: "App",

  // used components
  components: {
    TryImportVue,
    BucketList,
  },

  // fixed datas, loaded before the component render.
  // or not. I can change the task.id and it change the class... ??????
  data() {
    return {
      propData: "propdata what I will send U",
      fixedDataMessage: "This is my first rapid rendez-vous with Vue",
      //date: (new Date).toISOString().split("T")[0]  ,  // eredeti dátum
    };
  },

  // dynamic datas
  computed: {},

  //a lifcycled hook,
  created() {},

  // define functions here
  methods: {},
};
</script>

<style>
@import "./styles/style.css";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.testField {
  margin: 2rem 5rem 0;
  padding: 1rem 0;
  border: 2px black solid;
  border-radius: 1rem;
  background-color: rgb(158, 200, 255);
}

.testElement {
  width: 70%;
  margin: 1rem auto;
  border-radius: 1rem;
  padding: 1rem;
  background-color: rosybrown;
}

.testElement > div > * {
  margin: 1rem;
}

.testElement > div > div:nth-child(2) div:nth-child(2) {
  margin: 2px;
  font-weight: bolder;
}
</style>
