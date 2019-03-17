<template>
  <div class="wrapper">
    <slot></slot>
  </div>
</template>

<style scoped lang="scss">
.wrapper {
  position: sticky;
  top: 0;
  background: #fff;
  z-index: 100;
}
</style>
