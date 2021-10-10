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
  max-width: 450px;
  background-color: #334756;
  border-radius: 20px;
  padding: 20px;
  justify-self: center;
  user-select: none;
  overflow: hidden;
}
</style>
