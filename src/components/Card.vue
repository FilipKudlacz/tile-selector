<template>
  <div class="card-wrapper">
    <p>
      <slot>Title</slot>
    </p>
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

  p {
    margin: 0;
    overflow: hidden;
    max-width: 100%;
  }
}
</style>
