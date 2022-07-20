<template lang="">
  <button class="card__delete-btn">
    <img class="" src="public\images\delete 1.png" />
  </button>
</template>
<script>
export default {};
</script>
<style scoped lang="scss">
.card__delete-btn {
  opacity: 0;
  position: absolute;
  right: -8px;
  top: -8px;

  width: 32px;
  height: 32px;
  background-color: #ff8484;
  box-shadow: 0px 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 10px;

  cursor: pointer;
  transition: opacity 0.3s, visibility 0.3s, background-color 0.3s;

  &:hover {
    background-color: #f55c5c;
  }
}
</style>
