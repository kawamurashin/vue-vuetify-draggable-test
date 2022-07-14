<template>
  <div>
    <draggable
        v-model="myArray"
        group="people"
        @start="drag=true"
        @end="drag=false"
        item-key="id"
        v-bind="dragOptions"
        handle=".handle">
      <template #item="{element}">
        <div class="list-group-item">
          <span class="handle">
            <v-icon
                large
                color="black"
            style="margin: 10px">
              mdi-drag-horizontal-variant
            </v-icon>
          </span>
          <span class="text">{{ element.name }} </span>
        </div>
      </template>
    </draggable>
  </div>
</template>
<script lang="ts">
import {defineComponent} from 'vue'
import draggable from 'vuedraggable'
export default defineComponent({
  name: 'App',
  components: {
    draggable
  },
  data() {
    return {
      myArray: [
        {name: "John", id: 0},
        {name: "Joao", id: 1},
        {name: "Jean", id: 2},
        {name: "004", id: 3},
        {name: "4", id: 4},
        {name: "Jean5", id: 5}
      ],
      drag: false
    }
  },
  computed: {
    dragOptions() {
      return {
        animation: 200,
        group: "description",
        disabled: false,
        ghostClass: "ghost"
      };
    }
  },
})
</script>
<style>
.ghost {
  opacity: 0.75;
  background: #c8ebfb;
}
.list-group-item {
  padding: 5px;
  border-bottom: solid #000000 1px;
}
.handle {
  cursor: move;
}
</style>