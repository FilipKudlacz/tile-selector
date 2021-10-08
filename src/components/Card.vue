<template>
  <div class="card-wrapper">
    <slot>Title</slot>
  </div>
</template>

<script>
export default {
};
</script>

<style scoped lang="scss">
.card-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 30px;
  font-weight: bold;
  min-height: 100px;
  min-width: 300px;
  background-color: #ffb085;
  border-radius: 20px;
  justify-self: center;
  box-shadow: 8px 8px 2px 0px rgba(66, 68, 90, 1);
}
</style>
