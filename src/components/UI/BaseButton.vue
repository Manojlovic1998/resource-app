<template>
  <button class="btn btn-primary">
    <slot></slot>
  </button>
</template>

<style scoped>
.btn-primary.active {
  background: #040921;
}

.btn-primary {
  padding: 10px 16px;
  border-radius: 8px;
  background: rgba(4, 9, 33, 0.32);
  border: none;
}

.btn-primary:hover {
  background: #040921;
}
</style>