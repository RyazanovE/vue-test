<template lang="">
  <section class="card-form-container">
    <h4 class="card-form-header">Добавление товара</h4>
    <slot></slot>
  </section>
</template>
<script>
export default {};
</script>
<style lang="scss" scoped>
.card-form-container {
  flex-basis: 23%;
  display: flex;
  flex-direction: column;
  gap: 16px;
}

.card-form-header {
  font-size: 28px;
  font-weight: 600;
}
</style>
