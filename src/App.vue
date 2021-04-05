<template>
  <div id="app" class="container mt-5">
    <div class="row">
      <div class="col form-inline">
        <b-form-input
          v-model="newTask"
          placeholder="Enter Task..."
          @keyup.enter="add"
        ></b-form-input>
        <b-button class="ml-2" variant="primary" @click="add">Add</b-button>
        <b-button class="ml-2" variant="primary" @click="addList"
          >Add List</b-button
        >
      </div>
    </div>
    <br />

    <div class="row flex-nowrap" id="project">
      <div  v-for="list in arrList" :key="list.id">
        <List class="col-3" :name="'Backlog'" :list="arrBackLogs" :arr="arrBackLogs" />
      </div>
    </div>
  </div>
</template>

<script>
import List from "./components/List";
export default {
  name: "App",
  components: { List },
  data() {
    return {
      newTask: "",
      arrList: [],
      arrBackLogs: [
        { name: "Code sign up page" },
        { name: "Test Dashboard" },
        { name: "Style Registration" },
        { name: "Help with designs" },
      ],
      arrInProgress: [],
      arrTestes: [],
      arrDone: [],
    };
  },
  methods: {
    add() {
      if (this.newTask) {
        this.arrBackLogs.push({ name: this.newTask });
        this.newTask = "";
      }
    },
    addList() {
      this.arrList.push(List);
    },
  },
};
</script>

<style>
.kanban-column {
  min-height: 300px;
  min-width: 200px;
}
</style>