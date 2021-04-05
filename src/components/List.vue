<template>
  <div class="col-md-3 kanban-column">
        <div class="p-2 alert-secondary">
          <h3>{{ name }}</h3>
          <draggable  class="list-group " group="tasks">
            <div class="list-group-item" v-for="element in arr" :key="element.name">
              {{ element.name }}
            </div>
          </draggable>
        </div>
      </div>
</template>

<script>
import draggable from 'vuedraggable'
export default {
    props: [
        'name',
        'list', 
        'arr'
    ],
    components: { draggable }
}
</script>

<style>

</style>