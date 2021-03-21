<template>
  <div id="app" class="container mt-5">
    <div class="row">
      <div class="col form-inline">
        <b-form-input
          v-model="newTask"
          placeholder="Enter Task..."
          @keyup.enter="add"
        ></b-form-input> <b-button class="ml-2 " variant="primary" @click="add">Add</b-button>
      </div>
    </div>
    <div class="row mt-3">
      <div class="col-md-3">
        <div class="p-2 alert-secondary">
          <h3>Backlog</h3>
          <draggable  class="list-group kanban-column" :list="arrBackLogs" group="tasks">
            <div class="list-group-item" v-for="element in arrBackLogs" :key="element.name">
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert-primary">
          <h3>In Progress</h3>
          <draggable  class="list-group kanban-column" :list="arrInProgress" group="tasks">
            <div class="list-group-item" v-for="element in arrInProgress" :key="element.name">
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert-warning">
          <h3>Tested</h3>
          <draggable  class="list-group kanban-column" :list="arrTestes" group="tasks">
            <div class="list-group-item" v-for="element in arrTestes" :key="element.name">
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>

      <div class="col-md-3">
        <div class="p-2 alert-success">
          <h3>Done</h3>
          <draggable  class="list-group kanban-column" :list="arrDone" group="tasks">
            <div class="list-group-item" v-for="element in arrDone" :key="element.name">
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import draggable from 'vuedraggable'

export default {
  name: 'App',
  components: { draggable },
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