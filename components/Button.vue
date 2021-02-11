<template>
  <button type="type" :class="[block ? 'btn-block' : '']"><slot /></button>
</template>

<script>
export default {
  props: {
    type: String,
    className: String,
    block: Boolean
  }
};
</script>

<style lang="scss">
@import "~/assets/scss/style.scss";
.btn {
  display: inline-block;

  user-select: none;
  border: 1px solid $red-base;
  padding: $input-padding-y $input-padding-x;
  background-color: $red-base;
  transition: all 0.3s;
  color: $white;
  border-radius: $radius-sm;
  line-height: $line-height-md;

  &:hover {
    background-color: lighten($red-base, 15%);
  }
  &:focus {
    outline: none;
  }
  &:active {
    background-color: $red-base;
  }
  &-block {
    display: block !important;
    width: 100%;
  }
}

button[disabled],
button[disabled]:hover,
button[disabled]:active,
button[disabled]:focus {
  background-color: lighten($red-base, 50%);
  border: 1px solid lighten($red-base, 45%);
  cursor: not-allowed;
}
</style>
