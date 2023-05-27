<script lang="ts">
import { useCounterStore } from "./store/index";
import Card from "./components/Card.vue";
import List from "./components/List.vue";

function onDragEnd(event: DragEvent) {
  console.log("drag end");
}

function onDragStart(event: DragEvent) {
  console.log("drag card");
}

export default {
  name: "App",
  components: {
    Card,
    List,
  },

  data() {
    return {
      store: useCounterStore(),
    };
  },

  methods: {
    onDragStart,
    onDragEnd,
  },
};
</script>

<template>
  <div id="app">
    <h1>Hello</h1>
    <div ondragstart="onDragStart(e)" ondragend="onDragEnd(e)" draggable="true">
      <Card :store="store" />
    </div>
    <List />
  </div>
</template>

<style scoped></style>
