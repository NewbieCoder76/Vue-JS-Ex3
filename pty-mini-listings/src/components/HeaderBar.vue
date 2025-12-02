<template>
  <header class="header">
    <h1>Homes & Beyond</h1>

    <p class="count">{{ total }} properties found</p>

    <div class="controls">
      <input 
        type="text"
        placeholder="Search by title or location..."
        v-model="search"
      />

      <button @click="$emit('toggle-sort')">
        Sort: {{ sortOrder === 'asc' ? 'Low → High' : 'High → Low' }}
      </button>
    </div>
  </header>
</template>

<script>
export default {
  props: ["total", "modelValue", "sortOrder"],
  emits: ["update:modelValue", "toggle-sort"],

  computed: {
    search: {
      get() { return this.modelValue; },
      set(val) { this.$emit("update:modelValue", val); }
    }
  }
};
</script>

<style scoped>
.header {
  margin-bottom: 30px;
}

.controls {
  margin-top: 15px;
  display: flex;
  gap: 12px;
}

input {
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 6px;
  flex: 1;
}

button {
  padding: 10px 16px;
  border: none;
  background: #1d70b8;
  color: white;
  border-radius: 6px;
  cursor: pointer;
}
</style>
