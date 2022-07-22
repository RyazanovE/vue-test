<template lang="">
  <div class="wrapper">
    <div class="container">
      <slot></slot>
    </div>
  </div>
</template>
<script>
export default {};
</script>
<style lang="scss" scoped>
.wrapper {
  padding: 32px;
}

.container {
  width: 100%;
  display: flex;
  gap: 16px;
}
</style>
