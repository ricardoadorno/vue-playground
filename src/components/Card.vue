<script lang="ts">
type Card = {
  name: string;
  count: number;
  increment: () => void;
  decrement: () => void;
};

export default {
  name: "Card",

  props: {
    store: {
      type: Object as () => Card,
      required: true,
    },
  },
};
</script>

<template>
  <div class="price-card">
    <h2>Price: {{ store.name }}</h2>
    <p>Quantity: {{ store.count }}</p>
    <button @click="store.increment">Increment</button>
    <button @click="store.decrement">Decrement</button>
  </div>
</template>

<style scoped>
.price-card {
  background-color: #f2f2f2;
  border-radius: 10px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  padding: 20px;
  text-align: center;
  width: 300px;
}

.price-card h2 {
  color: #333;
  font-size: 24px;
  margin-bottom: 20px;
}

.price-card p {
  color: #666;
  font-size: 18px;
  margin-bottom: 20px;
}

.price-card button {
  background-color: #4caf50;
  border: none;
  border-radius: 5px;
  color: white;
  padding: 10px 20px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  margin-top: 20px;
  cursor: pointer;
  margin: 0.5rem;
}
</style>
