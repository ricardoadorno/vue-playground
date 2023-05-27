<template>
  <div>
    <div
      v-for="(item, index) in items"
      :key="item.id"
      :draggable="true"
      @dragstart="dragStart(index)"
      @dragover="dragOver"
      @drop="drop"
      class="item"
    >
      {{ item.name }}
    </div>
  </div>
</template>

<script lang="ts">
export default {
  data() {
    return {
      items: [
        { id: 1, name: "Item 1" },
        { id: 2, name: "Item 2" },
        { id: 3, name: "Item 3" },
      ],
    };
  },
  methods: {
    dragStart(index: number, event: DragEvent) {
      // Set the data being dragged
      event.dataTransfer.setData("index", index);
    },
    dragOver(event: DragEvent) {
      // Allow the element to be dropped
      event.preventDefault();
    },
    drop(event: DragEvent) {
      // Get the index of the dragged item
      const draggedIndex = event.dataTransfer.getData("index");

      // Get the index of the drop target
      const dropIndex = event.target.getAttribute("data-index");

      // Swap the items in the array
      const temp = this.items[draggedIndex];
      this.items[draggedIndex] = this.items[dropIndex];
      this.items[dropIndex] = temp;
    },
  },
};
</script>

<style>
.item {
  background-color: rebeccapurple;
  border-radius: 10px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  padding: 20px;
  text-align: center;
  width: 300px;
  margin-bottom: 20px;
  cursor: move;
}
</style>
