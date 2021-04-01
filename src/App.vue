<template>
  <div id="app" class="container mt-5">
    <div class="row">
      <div class="col form-inline">
        <b-form-input
          v-model="newTask"
          placeholder="Enter Task..."
          @keyup.enter="add"
        ></b-form-input> 
        <b-button class="ml-2 " variant="primary" @click="add">Add</b-button>
      </div>
    </div>
    <div class="row mt-3">
      <Board
        :name="'Backlog'"
        :list="arrBackLogs"
        :arr="arrBackLogs"
      />
      <Board 
        :name="'In Progress'"
        :list="arrInProgress"
        :arr="arrInProgress"
      />
      <Board 
        :name="'Done'"
        :list="arrDone"
        :arr="arrDone"
      />
    </div>
  </div>
</template>

<script>
import Board from './components/Board'
export default {
  name: 'App',
  components: {Board },
  data() {
    return {
      newTask: '',
      arrBackLogs: [
        { name: 'Code sign up page' },
        { name: 'Test Dashboard' },
        { name: 'Style Registration' },
        { name: 'Help with designs' },
      ],
      arrInProgress: [],
      arrTestes: [],
      arrDone: [],
    }
  },
  methods: {
    add() {
      if(this.newTask) {
        this.arrBackLogs.push( { name: this.newTask });
        this.newTask = '';
      }
    }
  }
}
</script>

<style>
  .kanban-column {
    min-height: 300px;
  }
</style>