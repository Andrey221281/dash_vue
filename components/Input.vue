<template>
  <div>
    <label v-if="label" for="">
      {{ label }}
    </label>
    <div class="input">
      <input
        :type="type"
        :class="[
          { input__error: isSubmited && isEmpty },
          variant ? `input-${variant}` : `input-default`
        ]"
        :placeholder="placeholder"
        :value="value"
        @input="$emit('input', $event.target.value)"
      />
      <div v-if="isSubmited && required && isEmpty" class="input__error-text">
        {{ errMessage }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    type: String,
    placeholder: String,
    variant: String,
    value: String,
    label: String,
    small: String,
    className: String,
    required: Boolean,
    errMessage: String,
    isSubmited: Boolean
  },
  computed: {
    isEmpty() {
      return this.value.length === 0;
    }
  }
};
</script>

<style lang="scss">
@import "~/assets/scss/style.scss";

.input {
  position: relative;

  &__error {
    @include border_input($full: false, $danger: true);
  }
  &__error-text {
    position: absolute;
    width: 100%;
    bottom: -1.25rem;
    font-size: 0.875rem;
    color: $red-base;
  }
}

input {
  display: block;
  padding: $input-padding-y $input-padding-x;
  line-height: $line-height-md;
  width: 100%;
  border: 0;
  margin: $space-base 0;
  border-radius: 0;
  &::placeholder {
    color: $gray500;
  }
}

input.small {
  margin-top: 0;
}

input:focus {
  outline: none;
}

label {
  margin-top: $space-sm;
  color: $gray200;
  font-size: $font-size-sm;
}

input.input-default {
  @include border_input($full: true, $danger: false);
}

input.input-underline {
  @include border_input($full: false, $danger: false);
}
</style>
