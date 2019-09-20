<template>
  <div class="tile" :class="{checked: todo.checked}">
    <div class="tile-icon list">
      <div>
        <i class="icon" :class="todo.checked ? 'icon-check': 'icon-time'"></i>
      </div>
      <div class="tile-content">
        <p class="tile-subtile">{{todo.description}}</p>
      </div>
      <div class="tile-action">
        <button @click="$emit('toggle', todo)" class="btn btn-link">
          <span v-if="todo.checked">Desmarcar</span>
          <span v-else>Concluído</span>
        </button>
        <button @click="$emit('remove', todo)" class="btn btn-link">
          <span class="text-error">Remover</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: { type: Object, required: true }
  }
};
</script>

<style scoped>
.list {
  display: flex;
  flex-direction: row;
  align-content: center;
  justify-content: space-between;
  max-width: 600px;
  min-width: 300px;
}
.checked {
  text-decoration: line-through;
  color: lightgray;
}
</style>